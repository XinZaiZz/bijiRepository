# Filter(过滤器)

##概念

### web中的过滤器

当访问服务器的资源时，过滤器可以将请求拦截下来，完成一些特殊的功能。

### 过滤器的作用

一般用于完成通用的操作。如：登陆验证、同一编码处理、敏感字符的过滤。。。

## 快速入门

#### 步骤

1、定义一个类，实现接口Filter

2、复写方法

3、配置拦截路径

​		web.xml

​		注解配置

创建filter类：

```java
/*
* 过滤器快速入门
* */
public class MyFilter implements Filter{

    @Override
    public void init(FilterConfig filterConfig) throws ServletException {

    }

    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        System.out.println("MyFilter 被执行了");
        filterChain.doFilter(servletRequest,servletResponse);//放行
    }

    @Override
    public void destroy() {

    }
}
```

web.xml配置：

```xml
<filter>
    <filter-name>demo01</filter-name>
    <filter-class>com.youxin.filter.MyFilter</filter-class>
  </filter>

  <filter-mapping>
    <filter-name>demo01</filter-name>
      <!-- 拦截路径 -->
    <url-pattern>/*</url-pattern>
  </filter-mapping>
```

结果：

当访问index.jsp时：

![image-20210802105520281](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802105520281.png)

控制台：

![image-20210802105539120](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802105539120.png)

### 过滤器的生命周期

```java
public class MyFilter03 implements Filter {
    //在服务器被关闭后，Filter对象被销毁
    //如果服务器被正常关闭后，会执行destroy方法
    //一般用来释放资源
    public void destroy() {
        System.out.println("destroy ...");
    }

    //每一次请求被拦截资源时。执行多次
    public void doFilter(ServletRequest req, ServletResponse resp, FilterChain chain) throws ServletException, IOException {
        chain.doFilter(req, resp);
        System.out.println("doFilter ...");
    }

    //服务器启动后，会创建Filter对象，然后调用init方法。执行一次
    //一般用来加载资源
    public void init(FilterConfig config) throws ServletException {
        System.out.println("init ...");
    }

}
```

![image-20210802111934616](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802111934616.png)

![image-20210802111944271](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802111944271.png)

### Filter拦截路径配置

1、具体资源路径。如：index.jsp 只有访问index.jsp资源时，过滤器才会被执行

2、目录拦截。如：/user/*  访问/user下的所有资源时，过滤器都会被执行

3、后缀名拦截。如：*.jsp 访问所有后缀名为jsp资源时，过滤器都会被执行

4、拦截所有资源。如：/* 拦截所有资源都会被执行

### Filter拦截方式配置

#### 注解配置

设置dispatcherTypes属性（数组，可以同时配置多个属性）

1、REQUEST：默认值。浏览器直接请求资源时，该过滤器会被执行，而转发时不会执行

2、FORWARD：转发访问资源，只有转发访问路径时才会被执行。

3、INCLUDE：包含访问资源

4、ERROR：错误跳转资源

5、ASYNC：异步访问资源

#### web.xml配置

添加`<dispatcher></dispatcher>`标签同样是上面5个属性值

### 过滤器链(配置多个过滤器)

执行顺序：如果有两个过滤器：过滤器1和过滤器2

1、过滤器1

2、过滤器2

3、资源执行

4、过滤器2执行完毕

5、过滤器1执行完毕

过滤器的先后顺序问题

1、注解配置：按照类名的字符串比较规则比较，值小的先执行

如：AFilter和BFilter比较大小，则AFilter先执行了

2、web.xml：谁定义在xml文件上边，谁先执行

#### 案例：登陆验证

验证是否登陆，如果登陆则直接放行，如果没有登陆，则跳转到登陆界面

验证session值是否不为空，如果不为空，则放行，没有则不放行。

排除登陆相关的资源，直接放行，不是则需要拦截。

```java
@Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
//        System.out.println("MyFilter 被执行了");
//        filterChain.doFilter(servletRequest,servletResponse);
        //强制转换
        HttpServletRequest request = (HttpServletRequest) servletRequest;
        //获取请求
        String uri = request.getRequestURI();
        //判断是否包含登陆相关资源路径
        if (uri.contains("login.jsp") || uri.contains("/loginServlet") || uri.contains("/js/") || uri.contains("/css/") || uri.contains("/imges/")){
            //包含，用户就是想登陆，放行
            filterChain.doFilter(servletRequest, servletResponse);
        }else{
            //不包含，需要验证用户是否已经登陆
            //获取session中的user
            Object user = request.getSession().getAttribute("user");
            if (user != null){
                //登陆了，可以放行
                filterChain.doFilter(servletRequest, servletResponse);
            }else {
                //没有登陆，跳转到登陆页面
                request.setAttribute("login_msg","您还未登录");
                request.getRequestDispatcher("/login.jsp").forward(servletRequest, servletResponse);
            }
        }
    }
```

#### 动态代理

![image-20210802143923116](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802143923116.png)

# Listener(监听器)

事件监听机制：

​	事件：一件事情

​	事件源：事件发生的地方

​	监听器：一个对象

​	注册监听：将事件、事件源、监听器绑定在一起。当事件源上发生某个事件后，执行监听器代码。

#### ServletContextListener：监听ServletContext对象的创建和销毁

基本方法：public void contextInitialized()，public void contextDestroyed()

```java
public class MyListener implements ServletContextListener {
    /*
    * 监听ServletContext对象创建的。ServletContext对象服务器启动后自动创建
    * */
    @Override
    public void contextInitialized(ServletContextEvent servletContextEvent) {
        //加载资源文件
        //获取ServletContext对象
        ServletContext servletContext = servletContextEvent.getServletContext();
        //加载资源文件
        String initParameter = servletContext.getInitParameter("contextConfig");
        //获取真实路径
        String realPath = servletContext.getRealPath(initParameter);
        //加载进内存
        try {
            FileInputStream fileInputStream = new FileInputStream(realPath);
            System.out.println(fileInputStream);
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }

        System.out.println("ServletContext对象被创建了");
    }

    /*
    * 在服务器关闭后，ServletContext对象被销毁，当服务器正常关闭后该方法被调用
    * */
    @Override
    public void contextDestroyed(ServletContextEvent servletContextEvent) {
        System.out.println("ServletContext对象被销毁了");
    }
}
```

xml:

```xml
  <!-- 注册监听 -->
  <listener>
    <listener-class>com.youxin.listener.MyListener</listener-class>
  </listener>

```



