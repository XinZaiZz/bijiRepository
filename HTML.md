# HTML

Hyper Text Markup Language(超文本标记语言)

### HTML5的优势

世界知名浏览器厂商对HTML5的支持

市场的需求

跨平台

### W3C标准

#### W3C

World Wide Web Consortium（万维网联盟）

成立于1994年，Web技术领域最权威和具影响力的国际中立性技术标准机构

http://www.w3.org/

http://www.chinaw3c.org/

#### W3C标准包括

结构化标准语言（HTML,XML）

表现标准语言（CSS）

行为标准（DOM、ECMAScript）

### HTML5简介

HTML5是HTML最新的修订版本，2014年10月由万维网联盟（W3C）完成标准制定。

HTML5的设计目的是为了在移动设备上支持多媒体。

HTML5 简单易学。

#### 什么是HTML5

HTML5 是下一代 HTML 标准。

HTML , HTML 4.01的上一个版本诞生于 1999 年。自从那以后，Web 世界已经经历了巨变。

HTML5 仍处于完善之中。然而，大部分现代浏览器已经具备了某些 HTML5 支持。

#### HTML5是如何起步的

HTML5 是 W3C 与 WHATWG 合作的结果,WHATWG 指 Web Hypertext Application Technology Working Group。

WHATWG 致力于 web 表单和应用程序，而 W3C 专注于 XHTML 2.0。在 2006 年，双方决定进行合作，来创建一个新版本的 HTML。

HTML5 中的一些有趣的新特性：

- 用于绘画的 canvas 元素
- 用于媒介回放的 video 和 audio 元素
- 对本地离线存储的更好的支持
- 新的特殊内容元素，比如 article、footer、header、nav、section
- 新的表单控件，比如 calendar、date、time、email、url、search

#### HTML5浏览器支持

最新版本的 Safari、Chrome、Firefox 以及 Opera 支持某些 HTML5 特性。Internet Explorer 9 将支持某些 HTML5 特性。

### HTML基本信息

```html
<!-- DOCTYPE:告诉浏览器，我们要使用什么规范 -->
<!-- head标签代表网页头部-->
<!-- title网页标题 -->
<!-- body标签代表网页主体 -->
<!-- meta描述性标签，用来描述网页的一些信息 -->
<!-- meta一般用来做SEO -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="keywords" content="first,html">
    <meta name="description" content="这是我的我第一个html网页">
    <title>First Html</title>
</head>
<body>
    Hello World
</body>
</html>
```

### 网页基本标签

| 开始标签 *             | 元素内容     | 结束标签 * |
| :--------------------- | :----------- | :--------- |
| <p>                    | 这是一个段落 | </p>       |
| <a href="default.htm"> | 这是一个链接 | </a>       |
| <br>                   | 换行         |            |

*****开始标签常被称为**起始标签（opening tag）**，结束标签常称为**闭合标签（closing tag）**。

------

####HTML 元素语法

- HTML 元素以**开始标签**起始
- HTML 元素以**结束标签**终止
- **元素的内容**是开始标签与结束标签之间的内容
- 某些 HTML 元素具有**空内容（empty content）**
- 空元素**在开始标签中进行关闭**（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有**属性**

**注释:** 您将在本教程的下一章中学习更多有关属性的内容。

------

#### 嵌套的 HTML 元素

大多数 HTML 元素可以嵌套（HTML 元素可以包含其他 HTML 元素）。

HTML 文档由相互嵌套的 HTML 元素构成。

------

#### HTML 文档实例

```html
<!DOCTYPE html>
<html>
<body>
<p>这是第一个段落。</p>
</body>
</html>
```

以上实例包含了三个 HTML 元素。

------

#### HTML 实例解析

<p> 元素:

<p>这是第一个段落。</p>

这个 <p> 元素定义了 HTML 文档中的一个段落。
这个元素拥有一个开始标签 <p> 以及一个结束标签 </p>.
元素内容是: 这是第一个段落。

**<body> 元素:**

```html
<body>

<p>这是第一个段落。</p>

</body>
```



<body> 元素定义了 HTML 文档的主体。
这个元素拥有一个开始标签 <body> 以及一个结束标签 </body>。
元素内容是另一个 HTML 元素（p 元素）。

**<html> 元素：**

```html
<html>

<body>

<p>这是第一个段落。</p>

</body>

</html>
```

<html> 元素定义了整个 HTML 文档。
这个元素拥有一个开始标签 <html> ，以及一个结束标签 </html>.
元素内容是另一个 HTML 元素（body 元素）。

```html'
&gt;<!-- 大于符号 -->
<br>
&lt;<!-- 小于符号 -->
<br>
&copy;<!-- 版权符号 -->
```

![image-20210803100223232](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803100223232.png)

##### 图像标签

![image-20210803100517792](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803100517792.png)

##### 连接标签

![image-20210803100946137](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803100946137.png)

锚链接

`<a href = "#top">回到顶部</a>` 其中#top为顶部定义的一个标识为name = top

功能性链接

`<a href="mailto:1511980683@qq.com">点击联系我</a>`

------

#### 不要忘记结束标签

即使您忘记了使用结束标签，大多数浏览器也会正确地显示 HTML：

<p>这是一个段落<p>这是一个段落

以上实例在浏览器中也能正常显示，因为关闭标签是可选的。

但不要依赖这种做法。忘记使用结束标签会产生不可预料的结果或错误。

------

#### HTML 空元素

没有内容的 HTML 元素被称为空元素。空元素是在开始标签中关闭的。

<br> 就是没有关闭标签的空元素（<br> 标签定义换行）。

在 XHTML、XML 以及未来版本的 HTML 中，所有元素都必须被关闭。

在开始标签中添加斜杠，比如 <br />，是关闭空元素的正确方法，HTML、XHTML 和 XML 都接受这种方式。

即使 <br> 在所有浏览器中都是有效的，但使用 <br /> 其实是更长远的保障。

#### 行内元素和块元素

块元素

无论内容多少，该元素独占一行

（p、h1-h6）

行内元素

内容撑开宽度，左右都是行内元素的可以排在一行

(a、strong、em)

#### 列表：

```html
<!--有序列表-->
<ol>有序列表
    <li>张三</li>
    <li>李四</li>
    <li>王五</li>
</ol>
<hr/>
<!--无序列表，导航，侧边栏。。-->
<ul>无序列表
    <li>张三</li>
    <li>李四</li>
    <li>王五</li>

</ul>
<!--自定义列表-->
<dl>
    <dt>姓名</dt><!-- 列表名称 -->
    <dd>张飒</dd>
    <dd>张三</dd>
    <dd>李四</dd>
    <dd>麻子</dd>

    <dt>地区</dt><!-- 列表名称 -->
    <dd>北京</dd>
    <dd>上海</dd>
    <dd>兰州</dd>
    <dd>成都</dd>
</dl>
```

![image-20210803103300887](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803103300887.png)

#### 表格标签

```html
<table border="5px">
        <tr></tr>
            <!-- colspan="3"表示该行占3列 -->
            <td colspan="3">1-1</td>
        <tr></tr>
            <td>2-1</td>
            <td>2-2</td>
                <!--rowspan="2"表示该列占两行 -->
            <td rowspan="2">2-3</td>
        <tr></tr>
            <td>3-1</td>
            <td>3-2</td>
    </table>
```

#### 媒体元素

视频：

![image-20210803104923812](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803104923812.png)

音频：

![image-20210803105039397](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803105039397.png)

####页面结构分析：

![image-20210803105130801](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803105130801.png)



#### iframe框架

```html
<body>

<!--  iframe内联框架
 src：地址
 w-h：宽-高-->
    <!--<iframe src="//player.bilibili.com/player.html?aid=631782145&bvid=BV1hb4y167cS&cid=375041605&page=1"
            scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>-->

    <iframe src="https://www.bilibili.com" name="myframe" width="800px" height="500px"></iframe>
    <a href="first_html.html" target="myframe" > 点击跳转</a>
</body>
```

------

#### HTML 提示：使用小写标签

HTML 标签对大小写不敏感：`<P> `等同于` <p>`。许多网站都使用大写的 HTML 标签。

因为万维网联盟（W3C）在 HTML 4 中**推荐**使用小写，而在未来 (X)HTML 版本中**强制**使用小写

### 表单元素

![image-20210803113752189](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210803113752189.png)

`<input type="url" name="url">` 必须输入完整网址



##### label标签：

```html
<p>
            <!-- 增强鼠标可用性-->
            <label for="mark">点击输入</label>
            <input type="text" id="mark">
        </p>
```

### 表单初级验证：

常用方式：

placeholder：占位提示信息

require：元素内容不能为空

pattern：正则表达式

## 新元素

| 标签       | 描述                                                         |
| :--------- | :----------------------------------------------------------- |
| `<canvas>` | 标签定义图形，比如图表和其他图像。该标签基于 JavaScript 的绘图 API |



------

## 新多媒体元素

| 标签       | 描述                                                       |
| :--------- | :--------------------------------------------------------- |
| `<audio>`  | 定义音频内容                                               |
| `<video>`  | 定义视频（video 或者 movie）                               |
| `<source>` | 定义多媒体资源 <video> 和 <audio>                          |
| `<embed>`  | 定义嵌入的内容，比如插件。                                 |
| `<track>`  | 为诸如 <video> 和 <audio> 元素之类的媒介规定外部文本轨道。 |



------

## 新表单元素

| 标签         | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| `<datalist>` | 定义选项列表。请与 input 元素配合使用该元素，来定义 input 可能的值。 |
| `<keygen>`   | 规定用于表单的密钥对生成器字段。                             |
| `<output>`   | 定义不同类型的输出，比如脚本的输出。                         |



------

## 新的语义和结构元素

HTML5提供了新的元素来创建更好的页面结构：

| 标签           | 描述                                                         |
| :------------- | :----------------------------------------------------------- |
| `<article>`    | 定义页面独立的内容区域。                                     |
| `<aside>`      | 定义页面的侧边栏内容。                                       |
| `<bdi>`        | 允许您设置一段文本，使其脱离其父元素的文本方向设置。         |
| ``<command>``  | 定义命令按钮，比如单选按钮、复选框或按钮                     |
| `<dedails>`    | 用于描述文档或文档某个部分的细节                             |
| `<dialog>`     | 定义对话框，比如提示框                                       |
| ``<summary>``  | 标签包含 details 元素的标题                                  |
| `<figure>`     | 规定独立的流内容（图像、图表、照片、代码等等）。             |
| `<figcaption>` | 定义 `<figure> `元素的标题                                   |
| ``<footer>``   | 定义 section 或 document 的页脚。                            |
| `<header>`     | 定义了文档的头部区域                                         |
| `<mark>`       | 定义带有记号的文本。                                         |
| `<meter>`      | 定义度量衡。仅用于已知最大和最小值的度量。                   |
| `<nav>`        | 定义导航链接的部分。                                         |
| `<progress>`   | 定义任何类型的任务的进度。                                   |
| ``<ruby>``     | 定义 ruby 注释（中文注音或字符）。                           |
| `<rt>`         | 定义字符（中文注音或字符）的解释或发音。                     |
| `<rp>`         | 在 ruby 注释中使用，定义不支持 ruby 元素的浏览器所显示的内容。 |
| `<section>`    | 定义文档中的节（section、区段）。                            |
| `<time>`       | 定义日期或时间。                                             |
| `<wbr>`        | 规定在文本中的何处适合添加换行符。                           |



------

## 已移除的元素

以下的 HTML 4.01 元素在HTML5中已经被删除:

- <acronym>
- <applet>
- <basefont>
- <big>
- <center>
- <dir>
- <font>
- <frame>
- <frameset>
- <noframes>
- <strike>
- <tt>

