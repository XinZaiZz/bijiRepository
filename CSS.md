# CSS

### 什么是CSS

- CSS 指层叠样式表 (**C**ascading **S**tyle **S**heets)
- 样式定义**如何显示** HTML 元素
- 样式通常存储在**样式表**中
- 把样式添加到 HTML 4.0 中，是为了**解决内容与表现分离的问题**
- **外部样式表**可以极大提高工作效率
- 外部样式表通常存储在 **CSS 文件**中
- 多个样式定义可**层叠**为一个

### CSS发展史

CSS1.0

CSS2.0:DIV(块)+CSS,HTML与CSS结构分离思想，网页变得简单。SEO

CSS2.1：浮动，定位

CSS3.0：圆角，阴影，动画....浏览器兼容性

### CSS优势

1、内容和表现分离

2、样式复用

3、样式十分丰富

4、建议使用独立于html的css文件

5、利用SEO，容易被搜索引擎录入

### 快速入门

```html
<!--规范-->
    <!--
    每一个声明最好使用;结尾
        语法：
        选择器{
            声明1;
            声明2;
            声明3;
        }
    -->
    <style>
        h1{
            color: red;
        }
    </style>
</head>
<body>
<h1>我是第一个标题</h1>
</body>
```

或者单独建立css文件再用`<link rel="stylesheet" href="css/style.css">`将其引入

### 四种CSS导入方式

优先级：就进原则

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!-- 第一种 -->
    <style>
        h1{
             color: aqua;
         }
    </style>
    <!-- 第二种 -->
    <link rel="stylesheet" href="css/style.css">
    <!-- 第三种 -->
    <style>
    	@import url("css/style.css")
    </style>
</head>
<body>

<!-- 行内样式，在标签元素中，编写一个style属性，编写样式即可 -->
<h1 style="color: green">标题1</h1>
</body>
</html>
```

首页link和import语法结构不同，link是html标签，只能放入html源代码中使用，后者可以看作为css样式，作用是引入css样式功能。import在html使用的时候需要`<style type="text/css">`标签，同时可以直接“@import url(css文件路径地址;)"放入css文件或css代码里引入其他CSS文件。本质上两者使用选择区别不大，但是为了软件中编辑布局页面html代码，一般使用link较多，也推荐使用link。

### 选择器

作用：选择页面上的某一个或者某一类元素

#### 基本选择器

#####1、标签选择器：选择一类标签

```html
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
        /* 标签选择器会匹配所有标签名匹配的标签 */
        h1{
            color: #a1e3d1;
        }
        p{
            font-size: 100px;
        }
    </style>
</head>
<body>
<h1>这是标题</h1>
<p>今天天气好好啊</p>
</body>
```

#####2、类选择器 class：选择所有class属性一致的标签，跨标签

```html
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
        /*
        类选择器的格式  .class名{}
        好处，可以多个标签归类，是同一个class，可以复用
        */
        .class1{
            color: rebeccapurple;
        }
        .class2{
            color: aqua;
        }
    </style>
</head>
<body>
    <p class="class1">今天天气怎样</p>
    <p class="class2">今天天气不好</p>
    <p class="class1">明天天气也不好</p>
</body>
```

![image-20210803150945541](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803150945541.png)

#####3、id选择器：全局唯一

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
        /*
        id选择器   #id名{}
        id必须保证唯一
        */
        #id1{
            color: crimson;
        }
        #id2{
            color: #12a3d3;
        }
        #id3{
            color: red;
        }
    </style>
</head>
<body>

<p id="id1">今天天气不好吗</p>
<p id="id2">今天不怎么好</p>
<p id="id3">昨天也不好</p>
</body>
```

![image-20210803151355803](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803151355803.png)

选择器优先级：不遵循优先级

id选择器>类选择器>标签选择器

#### 层次选择器

```html
<body>
<p class="class1">p1</p>
<p>p2</p>
<p>p3</p>
<ul>
    <li>
        <p>pp1</p>
    </li>
    <li>
        <p>pp2</p>
    </li>
    <li>
        <p>pp3</p>
    </li>
</ul>
</body>
```



##### 1、后代选择器：在某个元素的后面

```html
/*后代选择器*/
        body p{
            background-color: red;
        }
```

![image-20210803152951880](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803152951880.png)

##### 2、子选择器：后面一代

```html
<style>
/*子选择器*/
        body>p{
            background-color: rebeccapurple;
        }
    </style>
```



![image-20210803153041735](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803153041735.png)

##### 3、相邻兄弟选择器：相邻的下一个属性，只包含一个

```html
/*相邻兄弟选择器，只有一个*/        
.class1 + p{            
			background-color: bisque;        
}
```

![image-20210803153305418](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803153305418.png)

##### 4、通用选择器

```html
/*通用选择器，当前选中元素的向下的所有兄弟元素*/        
.class1~p{           
background-color: #12a3d3;        
}
```

![image-20210803153546603](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803153546603.png)

#### 结构伪类选择器

```html
<!-- 避免使用class，id选择器-->    
<style type="text/css">        
    /* 选中ul的第一个子元素li1*/        
    ul li:first-child{            
        background-color: red;        
    }        
    /*选中ul的最后一个元素*/        
    ul li:last-child{            
        background-color: aqua;        
    }    
</style>
```

![image-20210803154529539](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803154529539.png)

```html
<style>
    /*选中p1：定位到父元素，选择当前的第一个元素，按个数来选        
    选择当前p元素的父级元素，选中父级元素的第一个，并且是当前元素才生效        
    比如如果在p标签之前有一个其他标签此时参数1不管用了只有改为参数2才有用*/        
    p:nth-child(1){            
        background-color: green;        
    }        
    /*选中父元素下的p元素的第二个，按类别来选，不管p1前面是否有其他标签，都会从p1开始选择*/        
    p:nth-of-type(1){            
        background-color: #12a3d3;        
    }    	
    /*鼠标悬停时变化*/       
    a:hover{            
        background-color: rebeccapurple;        
    }    
</style>
```

![image-20210803155537765](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803155537765.png)

#### 属性选择器（常用）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
        .demo a{
            float: left;
            display: block;
            height: 50px;
            width: 50px;
            border-radius: 10px;
            background: magenta;
            text-align: center;
            color: gainsboro;
            text-decoration: none;
            margin-right: 8px;
            line-height: 50px;

        }

        /*属性名，属性名=属性值（正则）*/
        /*
        =  :  绝对等于
        *=  :  包含
        ^=  :  以这个开头
        $=  :  以这个结尾
        */
        /*存在id属性的元素
        a[]{}
        */
        /*a[id]{
            background: yellow;
        }*/
        /*id=first的元素*/
        a[id=first]{
            background: chartreuse;
        }
        /*class中有links的元素*/
        a[class*="links"]{
            background: green;
        }
        /*选中href中以http开头的元素*/
        a[href^="http"]{
            background: firebrick;
        }
        /*选中href中以pdf结尾的元素*/
        a[href$="pdf"]{
            background-color: #ffa1a2;
        }
    </style>
</head>
<body>
<p class="demo" >
    <a href="http://www.baidu.com" class="links item first" id="first">1</a>
    <a href="" class="links item active" target="_blank" title="test">2</a>
    <a href="images/123.htm1" class="links item">3</a>
    <a href="images/123.png" class="links item">4</a>
    <a href="images/123.jpg" class="links item">5</a>
    <a href="abc" class="links item">6</a>
    <a href="/a.pdf" class="links item">7</a>
    <a href="/abc.pdf" class="links item">8</a>
    <a href="abc.doc" class="links item">9</a>
    <a href="abcd.doc" class="links item last">10</a>
</p>
</body>
</html>
```

![image-20210803162854269](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803162854269.png)

### 盒子模型

![image-20210803190753471](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803190753471.png)

##### 什么是盒子模型

margin：外边距:顺时针旋转

padding：内边距

border：边框

#### 边框

1、边框的粗细

2、边框的样式

3、边框的颜色

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
        body{
            /*总有一个默认的外边距 8px*/
            margin: 0px;
        }
        #box{
            width: 300px;
            border: 1px solid red;
        }
        h2{
            font-size: 16px;
            background-color: #2c2fff;
            line-height: 30px;
            color: white;
        }
        form{
            background: #00FF00;
        }
        div:nth-of-type(1) input{
            border: 3px solid black;
        }
        div:nth-of-type(2) input{
            border: 3px dashed #df6eff;
        }
        div:nth-of-type(3) input{
            border: 3px solid #2c2fff;
        }
    </style>
</head>
<body>

<div id="box">
    <h2>会员登陆</h2>
    <form action="#">
        <div>
            <span>用户名：</span>
            <input type="text">
        </div>
        <div>
            <span>密码：</span>
            <input type="password">
        </div>
        <div>
            <span>邮箱：</span>
            <input type="email">
        </div>
    </form>
</div>
</body>
</html>
```

![image-20210803192134603](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803192134603.png)

清除浮动：clear:both(清除两侧浮动),clear:left(清除左侧浮动)

overflow : scroll：​限制高度或宽度，多余部分用滚动条。

避免父类塌陷：可以给父类添加一个伪类：after

```html
#father:after{
	content:'';
	display:block;
	clear:both;
}
```

### 定位

#### 相对定位

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!-- 相对定位：相对于自己原来的位置进行偏移 -->
    <!-- right,left,top,bottom都是指距离原来（即相对于原来的位置）右左上下的距离，不是往右左上下偏移，偏移后还是在标准文档流中 -->
    <style>
        div{
            margin: 10px;
            padding: 5px;
            font-size: 12px;
            line-height: 25px;
        }
        #father{
            border: 1px solid #666;
            padding: 0;
        }
        #first{
            background-color: #FF00FF;
            border: 1px dashed #666;
            position: relative;/* 相对定位，上下左右*/
            top: -20px;
            left: 50px;
        }
        #second{
            background-color: #FF2525;
            border: 1px dashed #666;
        }
        #third{
            background-color: #ffa1a2;
            border: 1px dashed #666;
            position: relative;
            bottom: 10px;
            right: 50px;
        }
    </style>
</head>
<body>
<div id="father">
    <div id="first" >第一个盒子</div>
    <div id="second" >第一个盒子</div>
    <div id="third" >第一个盒子</div>
</div>
</body>
</html>
```

![image-20210803201855512](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803201855512.png)

#### 绝对定位

```
绝对定位,没有父级元素定位的情况下会基于浏览器边框定位
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            margin: 10px;
            padding: 5px;
            font-size: 12px;
            line-height: 25px;
        }
        #father{
            border: 1px solid #666;
            padding: 0;
        }
        #first{
            background-color: #FF00FF;
            border: 1px dashed #666;
        }
        #second{
            background-color: #FF2525;
            border: 1px dashed #666;
            position: absolute;/*绝对定位,没有父级元素定位的情况下会基于浏览器边框定位*/
            right: 50px;
        }
        #third{
            background-color: #ffa1a2;
            border: 1px dashed #666;
        }
    </style>
</head>
<body>
<div id="father">
    <div id="first" >第一个盒子</div>
    <div id="second" >第一个盒子</div>
    <div id="third" >第一个盒子</div>
</div>
</body>
</html>
```

![image-20210803203007823](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803203007823.png)

有父级元素定位的情况下，会相对于父级元素相对定位：

```html
		#father{
            border: 1px solid #666;
            padding: 0;
            position: relative;
        }
```

![image-20210803203124776](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803203124776.png)

#### 固定定位

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            margin: 10px;
            padding: 5px;
            font-size: 12px;
            line-height: 25px;
        }
        #father{
            border: 1px solid #666;
            padding: 0;
        }
        #first{
            background-color: #FF00FF;
            border: 1px dashed #666;
        }
        #second{
            background-color: #FF2525;
            border: 1px dashed #666;
            position: fixed;/*固定定位：*/
            right: 0;
            bottom: 0;
        }
        #third{
            background-color: #ffa1a2;
            border: 1px dashed #666;
        }
    </style>
</head>
<body>
<div id="father">
    <div id="first" >第一个盒子</div>
    <div id="second" >第二个盒子</div>
    <div id="third" >第三个盒子</div>
</div>
</body>
</html>
```

![image-20210803203926478](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803203926478.png)
