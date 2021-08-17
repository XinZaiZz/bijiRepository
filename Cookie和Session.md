# Cookie

Cookie，有时也用其复数形式 [Cookies](https://baike.baidu.com/item/Cookies/187064)。类型为“**小型文本文件**”，是某些网站为了辨别用户身份，进行[Session](https://baike.baidu.com/item/Session/479100)跟踪而储存在用户本地终端上的数据（通常经过加密），由用户[客户端](https://baike.baidu.com/item/客户端/101081)计算机暂时或永久保存的信息。

Cookie 并不是它的原意“甜饼”的意思, 而是一个保存在客户机中的简单的文本文件, 这个文件与特定的 [Web](https://baike.baidu.com/item/Web/150564) 文档关联在一起, 保存了该客户机访问这个Web 文档时的信息, 当客户机再次访问这个 Web 文档时这些信息可供该文档使用。由于“Cookie”具有可以保存在客户机上的神奇特性, 因此它可以帮助我们实现记录用户个人信息的功能, 而这一切都不必使用复杂的[CGI](https://baike.baidu.com/item/CGI/607810)等程序  。

举例来说, 一个 Web 站点可能会为每一个访问者产生一个唯一的[ID](https://baike.baidu.com/item/ID/91584), 然后以 Cookie 文件的形式保存在每个用户的机器上。如果使用浏览器访问 Web, 会看到所有保存在硬盘上的 Cookie。在这个文件夹里每一个文件都是一个由“名/值”对组成的文本文件,另外还有一个文件保存有所有对应的 Web 站点的信息。在这里的每个 Cookie 文件都是一个简单而又普通的文本文件。透过文件名, 就可以看到是哪个 Web 站点在机器上放置了Cookie(当然站点信息在文件里也有保存) 。

### Cookie组成

Cookie是一段不超过4KB的小型[文本](https://baike.baidu.com/item/文本/5443630)数据，由一个名称（Name）、一个值（Value）和其它几个用于控制Cookie有效期、安全性、使用范围的可选属性组成。其中 ：

(1)Name/Value：设置Cookie的名称及相对应的值，对于认证Cookie，Value值包括Web服务器所提供的访问令牌  。

(2)Expires属性：设置Cookie的生存期。有两种存储类型的Cookie：会话性与持久性。Expires属性缺省时，为会话性Cookie，仅保存在[客户端](https://baike.baidu.com/item/客户端/101081)内存中，并在用户关闭浏览器时失效；持久性Cookie会保存在用户的硬盘中，直至生存期到或用户直接在网页中单击“注销”等按钮结束会话时才会失效  。

(3)Path属性：定义了Web站点上可以访问该Cookie的目录  。

(4)Domain属性：指定了可以访问该 Cookie 的 Web 站点或域。Cookie 机制并未遵循严格的同源策略，允许一个[子域](https://baike.baidu.com/item/子域/5873902)可以设置或获取其父域的 Cookie。当需要实现单点登录方案时，Cookie 的上述特性非常有用，然而也增加了 Cookie受攻击的危险，比如攻击者可以借此发动会话定置攻击。因而，浏览器禁止在 [Domain](https://baike.baidu.com/item/Domain/68165) 属性中设置.org、.com 等通用顶级域名、以及在国家及地区顶级域下注册的二级域名，以减小攻击发生的范围  。

(5)Secure属性：指定是否使用[HTTPS](https://baike.baidu.com/item/HTTPS/285356)安全协议发送Cookie。使用HTTPS安全协议，可以保护Cookie在浏览器和Web服务器间的传输过程中不被窃取和篡改。该方法也可用于Web站点的身份鉴别，即在HTTPS的连接建立阶段，浏览器会检查Web网站的[SSL](https://baike.baidu.com/item/SSL/320778)证书的有效性。但是基于兼容性的原因（比如有些网站使用自签署的证书）在检测到[SSL证书](https://baike.baidu.com/item/SSL证书/5201468)无效时，浏览器并不会立即终止用户的连接请求，而是显示安全风险信息，用户仍可以选择继续访问该站点。由于许多用户缺乏安全意识，因而仍可能连接到Pharming攻击所伪造的网站  。

(6)HTTPOnly 属性 ：用于防止客户端脚本通过document.cookie属性访问Cookie，有助于保护Cookie不被跨站脚本攻击窃取或篡改。但是，HTTPOnly的应用仍存在局限性，一些浏览器可以阻止客户端脚本对Cookie的读操作，但允许写操作；此外大多数浏览器仍允许通过[XMLHTTP](https://baike.baidu.com/item/XMLHTTP/481421)对象读取[HTTP](https://baike.baidu.com/item/HTTP/243074)响应中的Set-Cookie头。

### 写入与读取

[Cookies集合](https://baike.baidu.com/item/Cookies集合/6079840)是附属于[Response对象](https://baike.baidu.com/item/Response对象/7465134)及[Request对象](https://baike.baidu.com/item/Request对象/5357566)的数据集合，使用时需要在前面加上Response或Request。用于给客户机发送Cookies的语法通常为：

```
< %Response.cookies(“Cookies名称”)=数据% > 
```

当给不存在的[Cookies集合](https://baike.baidu.com/item/Cookies集合/6079840)设置时，就会在客户机创建，如果该Cookies己存在，则会被代替。由于Cookies 是作为[HTTP](https://baike.baidu.com/item/HTTP/243074)传输的头信息的一部分发给客户机的，所以向客户机发送Cookies的代码一般放在发送给浏览器的HTML 文件的标记之前。如果用户要读取Cookies，则必须使用[Request对象](https://baike.baidu.com/item/Request对象/5357566)的Cookies集合，其使用方法是：

```
< %efg=request.cookies(“abc”) (将cookies对象abc的值赋给efg)% > 
```

需要注意的是，只有在服务器未被下载任何数据给浏览器前，浏览器才能与Server进行Cookies集合的数据交换，一旦浏览器开始接收Server所下载的数据，Cookies的数据交换则停止，为了避免错误，要在程序和前面加上response.Buffer=True。

### 生成Cookie

```java
        //创建两个cookie
        Cookie cookie = new Cookie("school", "school_1");
        Cookie cookie1 = new Cookie("teacher", "teacher_1");
        //指定cookie绑定路径,如果不绑定，默认为当前路径下的所有同类请求
        //注意，这里指定的路径要求必须要添加项目名称
        cookie.setPath(req.getContextPath() + "/aaa/xxx/ooo");
        cookie1.setPath(req.getContextPath() + "/bbb");
        //设置cookie的有效期，整型，单位为秒
        //该值大于0 ，表示将cookie存放到客户端的硬盘
        //该值小于0，与不设置效果相同，会将cookie存放到浏览器缓存
        //该值等于0，表示cookie一生成，马上消失
        cookie.setMaxAge(60);
        //设置cookie有效时间为10天
        cookie1.setMaxAge(60*60*24*10);
        //向响应中添加cookie
        resp.addCookie(cookie);
        resp.addCookie(cookie1);
```

![image-20210802163339308](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802163339308.png)

注意：如果不设置setMaxAge()则在会话结束时cookie失效

### 获取客户端cookie

```
//获取请求中的cookie
Cookie[] cookies = req.getCookies();
if (cookies != null) {
    for (Cookie cookie : cookies) {
        System.out.println(cookie.getName() + "===" + cookie.getValue());
    }
}else {
    System.out.println("未存在任何cookie");
}
```

![image-20210802165115024](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802165115024.png)

**注意：Cookie不要轻易禁用**

### ServletContext、HttpSession、HttpServletRequest三个域属性空间比较

ServletContext：即application，置入其中的域属性是整个应用范围的，可以完成垮回话共享数据

HttpSession：置入其中的域属性时会话范围的，可以完成垮请求共享数据

HttpServletRequest：置入其中的域属性时请求范围的，可以完成垮servlet共享数据，但这些servlet必须在同一请求中

对于这三个域属性空间对象的使用原则是，在可以保证功能需求的前提下，优先使用小范围的，这样不仅可以节省服务器内存，还可以保证数据的安全性。

# Session

session，即会话，是web开发中的一种会话状态跟踪技术。前面的cookie也是一种会话跟踪及时。不同的是cookie是将会话状态保存在了客户端，而session则是将会话状态保存在了服务器端。

那么到底什么是“会话”？当用户打开浏览器，从发出第一次请求开始，一直到最终关闭浏览器，就表示一次会话完成。

session并不是javaweb开发所特有的，而是整个web开发中所使用的技术，在javaweb开发中，session是以javax.servlet.http.HttpSession的接口对象形式出现的。

#### 对Session域属性空间的操作

Session是一个专门用于存放数据的集合，我们一般称这个用于存放数据的内存空间为域属性空间，简称域。HttpSession中具体有三个方法，是专门用于对该域属性空间中数据进行写、读操作的。

public void setAttribute(String name,Object value)

该方法用于向Session的域属性空间中放入指定名称、指定值的域属性

public Object getAttribute(String name)

该方法用于从session的域属性空间中读取指定名称为域属性值

public void removeAttribute(String name)

该方法用于从Session的域属性空间中删除指定名称的域属性

```java
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        resp.setContentType("text/html;charset=utf-8");
        //获取用户提交参数
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        //将参数放入request域
        req.setAttribute("user",username);

        //获取 Session对象
        HttpSession session = req.getSession();
        //向Session域中写入属性
        session.setAttribute("user_name",username);
        resp.getWriter().print("SessionServlet:" + username);
    }
```

获取session:

```java
public class SessionServlet02 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        String user_name = null;
        //从request域中读取user属性
        String user = req.getParameter("user");
        resp.getWriter().println("SessionServlet02：" + user);
        //重session域中读取数据
        //获取session
        HttpSession session = req.getSession(false);
        if (session != null) {
            user_name = (String) session.getAttribute("user_name");
        }

        resp.getWriter().println("SessionServlet02：" + user_name);
    }
}
```

```html
<form action="session" method="post">
    用户名：<input type="text" name="username"><br>
    密码：<input type="password" name="password"><br>
    <input type="submit" value="提交">
</form>
```

使用zhangsan 登陆：

![image-20210802174730869](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802174730869.png)

再访问session02:

![image-20210802174821665](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802174821665.png)

可以看到requset域不能在不同请求中访问，而session域可以用getAttribute()获取session队形。

getSession(true) 和 getSession()相等，即有这个session就用原本的session，没有则创建

getSession(flase)表示有session则用原来session，没有，则返回null,读取数据只有从老的session才有可能存在要查找的数据，新建的session中不可能有这些数据。

### Session的工作原理

在服务器中系统会为每个会话维护一个Session。不同的会话，对应不同的Session。一个会话会一直找一个session。

#### 1、写入Session列表

服务器 对当前应用中的Session是以Map的形式进行管理的，这个Map称为Session列表。该Map的key为一个32位长度的随机串，这个随机串称为JSessionID,value则为Session对象的引用。

当用户第一次提交请求时，服务器端Servlet中执行到request.getSession()方法后，会自动生成一个Map.Entry对象，key为一个根据某种算法新生成的JSessionID，value则为新创建的HttpSession对象。

![image-20210802193410080](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802193410080.png)

#### 2、服务器生成并发送Cookie

在将Session信息写入Session列表后，系统还自动将“JSessionID"作为name，这个32位长度的随机串作为value，以Cookie的形式存放到响应头中，并随着响应，将该Cookie发送到客户端。

#### 3、客户端接收并发送Cookie

客户端接收到这个Cookie后会将其存放到浏览器的缓存中，即只要客户端浏览器不关闭，浏览器缓存中的Cookie就不会消失。当用户第二次提交请求时，会将缓存中的这个Cookie，伴随着请求的头部信息，一块发送到服务端。

#### 4、从Session列表中查找

服务端从请求中读取到客户端发送来的Cookie，并根据Cookie的JSessionID的值，总Map中查找相应key所对应的value，即Session对象。然后，对该Session对象的域属性进行读写操作。

### Session失效

web开发中引入了Session超时的概念，Session的失效就是指Session的超时。若某个Session在指定的时间范围内一直未被访问，那么Session将超时，即将失效。

在web.xml中可以通过`<session-config/>` 标签设置Session的超时时间，单位为分钟。默认Session的超时时间为30分钟。需要再次强调的是，这个时间并不是从Session被创建开始计时的生命周期时长，而是从最后一次被访问开始计时，在指定的时间内一直未被访问的时长。

```xml
<!-- 设置Session的失效时间 -->
<session-config>
	<session-timeout>120</session-timeout>
</session-config>
```

若未到时间时限，也可通过代码提前是Session失效。HttpSession中的方法invalidate()，使得Session失效，但session并不为null。

public void invalidate()

如果浏览器禁用cookie则每次请求服务器都会创建一个session给浏览器。但如果在请求中加 `;jsessionid = 32位jsessionid码` 则还是可以使用之前发送过来的session，并且是同一个session，这样就又实现了会话跟踪。

```java
String uri = req.getContextPath()+"/otherServlet";
//解决禁用cookie后Session的重定向传递跟踪问题。
uri = resp.encodeRedirectURL(uri);
resp.sendRedirect(uri);
```

![image-20210802204012428](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210802204012428.png)

