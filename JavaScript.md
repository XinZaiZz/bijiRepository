# JavaScript

JavaScript一门弱类型脚本语言，其源代码在发往客户端运行之前不需经过编译，而是将文本格式的字符代码发送给浏览器由浏览器解释运行。

**Native 原生JS开发**

原生JS开发，也就是让我们按照【ECMAScript】标准的开发方式，简称是ES，特点是所有浏览器都支持。截止到当前博客发布时间，ES标准已发布如下版本:

· ES3

. ES4(内部，未正式发布)

· ES5(全浏览器支持)

. ES6(常用，当前主流版本: webpack打包成为ES5支持!)

. ES7

. ES8

. ES9(草案阶段)

区别就是逐步增加新特性。

**TypeScript微软的标准**

TypeScript 是一种由微软开发的自由和开源的编程语言。它是JavaScript的一个超集，而且本质上向这个语言添加了可选的静态类型和基于类的面向对象编程。由安德斯·海尔斯伯格(C#、Delphi、TypeScript之父; .NET创立者)主导。

该语言的特点就是除了具备ES的特性之外还纳入了许多不在标准范围内的新特性，所以会导致很多浏览器不能直接支持TypeScript语法，需要编译后（编译成JS）才能被浏览器正确执行。

### JavaScript框架

. jQuery:大家熟知的JavaScript库，优点是简化了DOM操作，缺点是DOM操作太频繁，影响前端性能;在前端眼里使用它仅仅是为了兼容IE6、7、8;

. Angular: Google 收购的前端框架，由一群Java程序员开发，其特点是将后台的MVC模式搬到了前端并增加了模块化开发的理念，与微软合作，采用TypeScript语法开发;对后台程序员友好，对前端程序员不太友好;最大的缺点是版本迭代不合理(如:1代->2代，除了名字，基本就是两个东西;截止发表博客时已推出了Angular6)

. React: Facebook 出品，一款高性能的JS前端框架;特点是提出了新概念【虚拟DOM】用于减少真实DOM操作，在内存中模拟DOM操作，有效的提升了前端渲染效率;缺点是使用复杂，因为需要额外学习一门【JSX】语言;

. Vue :一款渐进式JavaScript框架，所谓渐进式就是逐步实现新特性的意思，如实现模块化开发、路由、状态管理等新特性。其特点是综合了Angular(模块化)和React(虚拟DOM)的优点;

Axios∶前端通信框架;因为 vue 的边界很明确，就是为了处理DOM，所以并不具备通信能力，此时就需要额外使用一个通信框架与服务器交互;当然也可以直接选择使用jQuery 提供的AJAX通信功能;

### UI框架

.Ant-Design:阿里巴巴出品，基于React的UI框架

. ElementUl、iview、ice:饿了么出品，基于Vue的UI框架 

.Bootstrap: Twitter推出的“个用于前端开发的开源工具包

. AmazeUl:又叫“妹子UI”，一款HTML5跨屏前端框架

## 快速入门

### 引入JavaScript

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!-- script 标签内，写JAVAScript代码-->
    <!-- 注意：script标签必须成对出现 -->
    <!-- 不用显示定义type，默认就是script -->
    <script src="js/first.js">

    </script>
    <!--    <script>
            alert("hello world")
        </script>-->
</head>
<body>

</body>
</html>
```

![image-20210804094242485](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804094242485.png)

### 基本语法

```html
	<script>
        //javascript严格区分大小写
        //定义变量
        var a = "hello";
        var b = 1;
        var score = 59;
        // alert(b);
        //条件控制
        if (score >= 60 && score < 70){
            alert("及格");
        } else if (score>60 && score < 80){
            alert("良好");
        }else if (score >= 80){
            alert("优秀");
        } else {
            alert("不及格");
            //在浏览器控制台打印变量
            console.log("不及格");
        }
    </script>
```

### 数据类型

js不区分小数和整数，==number==

```javascript
123//整数123
123.1 // 浮点数123.1
1.123e3 //科学计数法
-99 //负数
NaN //not a number
Infinity //表示无限大
```



==字符串==

'abc'   "abc"



==布尔值==

true  false



==逻辑运算==

```javascript
	&&   两个都为真才为真
	||	一个为真就为真
    !	取反
```



==比较运算符==

```javascript
	=		赋值运算符
    ==		等于（类型不一样，值一样，也会判断为true）
    === 	绝对等于（类型一样，值也一样，判断结果为true）
```

须知：

NaN与所有的数值都不想等，包括自己

只能通过isNaN(NaN)来判断这个数是否是NaN



浮点数问题：

```javascript
console.log((1/3) === 1-2/3);   //false
```

尽量避免使用浮点数进行运算，存在精度问题



==null和undefined==

null  空

undefined  未定义



==数组==

java中数组必须是一系列相同类型的对象集合

js中不需要这样！

```javascript
var arr = [1,2,3,"hello","world","null",true];
```

```html
<script>
    //js不区分小数和整数
    //变量定义可以以字母、下划线、$开头，不能以数字开头
    console.log((1/3) === 1-2/3);
    console.log(Math.abs(1/3-(1-2/3))<0.0000001);
    var arr = [1,2,3,"hello","world",undefined];
    console.log(arr);
    var array = new Array(1,2,3,"hello",true);
    console.log(array[1]);
    //取数组下标，如果越界了就会undefined
    console.log(4);
    //对象
    //每个属性之间用逗号隔开，最后一个不需要
    var person = {
        name:"张三",
        age:12,
        tags:['js','java','pathon']
    }
    console.log(person.age)
    console.log(person.name)
    console.log(person)
</script>
```

![image-20210804103601260](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804103601260.png)

#### 严格检查模式strict

```html
    <script>
        //严格检查模式 预防javascript的随意性导致一些列问题
        //局部变量建议都用let定义
        //必须写在第一行
        'use strict'
        //全局变量
        //ES6  let
        b = 2;
        let i = 1;
        console.log(i)
        console.log(b)
    </script> 
```

![image-20210804104423751](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804104423751.png)

### 数据类型

#### 字符串

正常字符串使用单引号或者双引号包裹

注意转义字符用\\

```java
	\'
	\n
    \t
    \u4e2d    Unicode字符
    \x41      Ascll字符
    
```

多行字符串编写

```html
        //tab 键上面
		let msg = `
            千里冰封，
            万里雪飘，
            望长城内外...

        `;
```

![image-20210804105404039](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804105404039.png)

模板字符串

```javascript
        console.log(msg);
        let name = "张三";
        let age = 12;
        let msg1 = `你好呀,${name},你今年${age}了`;
        console.log(msg1);
```

![image-20210804105550595](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804105550595.png)

字符串长度

```javascript
        let student= " student";
        console.log(student.length);
		console.log(student[2]);
```

![image-20210804105830044](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804105830044.png)

字符串的可变性，不可变

字符串转大写：

```javascript
console.log(student.toUpperCase())；
```

转小写：

```javascript
console.log(student.toLowerCase())；
```

获取字符所在下标：

```javascript
console.log(student.indexOf('s'))；
```

#### 数组

Array可以包含任意的数据类型

定义数组：

```javascript
let arr= [1,2,3,4,5];
```

长度

```javascript
arr.length
```

注意：如果给arr.length赋值，数组的大小就会发生变化，如果赋值变小，元素可能会丢失

字符串的“1”和数字1是不同的。

截取：

```javascript
arr.slice(3)
```

![image-20210804111549212](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804111549212.png)

压栈和弹栈：（尾部）

```javascript
arr.push(35,"a");
console.log(arr);
arr.pop();
console.log(arr);
```

![image-20210804111753068](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804111753068.png)

头部：

```javascript
arr.unshift("b","c"); //压入到头部
arr.shift(); //弹出头部的一个元素
```

![image-20210804111957682](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804111957682.png)

排序：

```javascript
arr.sort()
```

元素反转：

```javascript
arr.reverse()
```

![image-20210804112146830](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804112146830.png)

拼接：concat()

```javascript
console.log(arr.concat(["nihoa",12]))
```

![image-20210804112309861](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804112309861.png)

注意：concat()并没有修改数组，只是会返回一个新的数组



打印拼接数组，使用特定的字符串连接：

```javascript
console.log(arr.join("-"));
```

![image-20210804112504856](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804112504856.png)

多维数组：

```javascript
let arrn = [[1,2,3],[5,6,7],[9,10,11]];
console.log(arrn);
```

![image-20210804112722057](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804112722057.png)

#### 对象

若干个键值对

```javascript
var 对象名{
    属性名：属性值，
    属性名：属性值，
    属性名：属性值，
    属性名：属性值
}
```

```javascript
let person = {
    name : "张三",
    age : 23,
    email : "123@qq.com",
    score : 60
}
console.log(person.name);
```

js对象，{...}表示一个对象，键值对描述属性xxx:xxx，中间用`,`隔开，最后一个属性比较逗号

javascript中的所有的键都是字符串，值是任意对象。

1、对象赋值：

```javascript
person.name = "李四";
console.log(person.name);
```

![image-20210804113832032](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804113832032.png)

2、使用一个不存在的对象属性，不会报错！undefined

```javascript
person.xxx
undefined
```

3、动态的删减属性

```javascript
delete  person.name;
console.log(person);
```

![image-20210804114025153](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804114025153.png)

4、动态的添加，直接给新的属性添加值即可

```javascript
person.xxx = "xxxx你好";
console.log(person);
```

![image-20210804114126687](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804114126687.png)

5、判断属性值是否在这个对象中  xxx in xxx

```javascript
'age' in person
```

![image-20210804114347442](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804114347442.png)

6、判断一个属性是否是这个对象自身拥有的 hasOwnProperty

```javascript
console.log('toString' in person);
console.log(person.hasOwnProperty('toString'));//toString是父类对象的不是person对象自己的。如：console.log(person.hasOwnProperty("age"));返回true
```

![image-20210804114615166](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804114615166.png)

#### Map和Set

> ES6的新特性

Map:

```html
<script>
        'use strict';
        let map = new Map([["张三",78],['李四',77],['王五',89]]);
        var name = map.get("李四");
        map.set("李华",99);//新增或修改，delete(key)删除
        console.log(name);
        console.log(map);
    </script>
```

![image-20210804153859762](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804153859762.png)

Set:

```javascript
        //set会去重
        let set = new Set([1,1,1,3,'nihao']);;
        console.log(set);
        set.delete(3);//删除
		console.log(set);
		set.add(2);//新增
```

![image-20210804154331400](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804154331400.png)

#### iterator

```html
    <script>
        'use strict';
        //通过fot of 实现迭代，for in 可以用下标迭代
        let arr = [1,23,3];
        for (let a of arr){
            console.log(a);
        }
        let map = new Map([['zhangsan',12],['lisi',21],['wanger',45]])
        for (let a of map){
            console.log(a)
        }
        let set = new Set([3,4,5,"世界"]);
        for (let b of set){
            console.log(b);
        }
    </script>
```

![image-20210804162408892](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804162408892.png)

### 函数

#### 定义函数

绝对值函数

```javascript
		function abs(a) {
            if (a >= 0){
                return a;
            } else
                return -a;
        }
 		//等于
        var abs = function (a) {
            if (a >= 0){
                return a;
            } else
                return -a;
        }
```

一旦执行到return代表函数结束，返回结果！

function(x){...}这是一个匿名函数，但是可以把结果赋值给abs，通过abs就可以调用函数

![image-20210804163258694](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804163258694.png)

js可以传任意个参数，也可以不传参数。

可以手动抛出异常：

```javascript
        var abs = function (a) {
            if (a !== 'number'){
                throw "NOT A NUMBER!";
            }
            if (a >= 0){
                return a;
            } else
                return -a;
        }
```

![image-20210804163644124](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804163644124.png)

> arguments

arguments可以判断传进来的参数个数，是一个数组

```javascript
            for (let x=0;x<arguments.length;x++){
                console.log(arguments[x]);
            }
```

![image-20210804164047993](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804164047993.png)

> rest   ES6新特性，获取除了已经定义的参数之外的所有参数

#### 变量的作用域

```html
    <script>
        'use strict';
        function demo() {
            var x = 1;
            x = x + 1;
        }
        x += 2;//Uncaught ReferenceError: x is not defined

    </script>
```

在javascript中，var定义的变量实际是有作用域的。

假设在函数体内声明，则在函数体外不能使用。（非要想实现的话就需要闭包）。

如果两个函数使用了相同的变量名，只要在函数内部就不会冲突。

```javascript
		function a() {
            var x = 0;
            function b() {
                var y = x +1;
            }
            var z = y + 1;//Uncaught ReferenceError: y is not defined
        }
```

内部函数可以访问外部函数的成员，反之则不行。

![image-20210804165554705](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804165554705.png)

假设内部函数变量和外部函数的变量重名，在函数查找变量从自身函数开始，由“内”向“外”查找，即内部函数变量会屏蔽外部函数变量。

#### 全局对象window

```javascript
        var x = "xxx";
        alert(x);
        alert(window.x)//默认所以的全局变量都是绑定在window对象下
        var old_alert = window.alert;
        old_alert(x);
        window.alert = function () {

        }
        //发现alert失效了
        alert(x);
        //恢复
        window.alert = old_alert;
        alert(x);
```

alert()本身就是一个window变量

js实际上只有一个全局作用域，任何变量（函数也可以视为变量），假设没有在函数作用范围内找到，就会向外查找，如果在全局作用域都没有找到，报错`ReferenceError`

#### 规范

由于所有的全局变量都会绑定到window上，如果不同的js文件，使用了相同的全局变量，冲突-->减少冲突。

```javascript
        //唯一全局变量
        var all = {};
        //定义全局变量
        all.name = "张三";
        all.add = function (a,b) {
            return (a += b);
        }
```

把自己的代码全部放入自己定义的唯一空间名字中，降低全局命名冲突问题。

##### 局部作用域let

```javascript
        function aaa() {
            for (var i = 0 ;i< 100 ; i++){
                console.log(i);
            }
            console.log(i+1)//可以看到i出了for循环的作用域
        }
```

![image-20210804172423632](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804172423632.png)

let关键字，解决局部作用域冲突问题

```javascript
        function aaa() {
            for (let i = 0 ;i< 100 ; i++){
                console.log(i);
            }
            console.log(i+1)//用了let关键字后就不能在作用域外起作用了
        }
```

![image-20210804172512733](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804172512733.png)

**所以建议在变量声明的时候用let关键字去定义局部作用域的变量**

#### 常量const

在ES6之前：约定只要用全部大写字母命名的变量就是常量，建议不要修改这样的文字。

```javascript
        //定义常量
        const PI = 3.14;
        //PI = 123;//发现定义常量后不能改变pi的值。
```

### 方法

方法就是把函数放在对象的里面，对象只有两个东西：属性和方法；

```javascript
        var zhangsan = {
            name:'张三',
            id:101,
            birth:1999,
            age:function () {
                //今年-出生年份
                var now = new Date().getFullYear();
                return (now - this.birth);
            }
        }
        console.log(zhangsan.age())
```

![image-20210804173734033](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804173734033.png)

this代表调用他的对象。this在java中是无法指向的。

##### apply

在js中可以控制this的指向：

```javascript
function getAge() {
    var now = new Date().getFullYear();
    return (now - this.birth);
}
var person = {
    name: "张三",
    birth:1998,
    age:getAge
}
var a = getAge.apply(person,[]);//this指向了person对象，参数为空，即指定函数对象，主动调用
console.log(a);
```

![image-20210804174435158](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210804174435158.png)

#### 内部对象

```javascript
typeof 123
"number"
typeof '123'
"string"
typeof true
"boolean"
typeof NaN
"number"
typeof []
"object"
typeof {}
"object"
typeof Math.abs
"function"
```

#### Date

```javascript
        var date = new Date();
        console.log(date);
        date.getFullYear();//年
        date.getMonth();//月 0-11
        date.getDate();//日期
        date.getDay();//星期几
        date.getHours();//时
        date.getMinutes();//分
        date.getSeconds();//秒
        date.getTime();//时间戳，全世界统一，从1970年1月1号开始到现在的毫秒数
		console.log(new Date(date.getTime()));//获取当前时间
```

### JSON对象

#### JSON是什么

**[JSON](https://baike.baidu.com/item/JSON)([JavaScript](https://baike.baidu.com/item/JavaScript) Object Notation, JS 对象简谱) 是一种轻量级的数据交换格式。**它基于 [ECMAScript](https://baike.baidu.com/item/ECMAScript) (欧洲计算机协会制定的js规范)的一个子集，采用完全独立于编程语言的文本格式来存储和表示数据。简洁和清晰的层次结构使得 JSON 成为理想的数据交换语言。 **易于人阅读和编写，同时也易于机器解析和生成，并有效地提升网络传输效率。**

在JavaScript中一切皆为对象，任何js支持的类型都可以用JSON来表示；

格式：

​		对象都用{}

​		数组都用[]

​		所有键值对，都是用key:value

json字符串和js对象的转化：

```javascript
		var user = {
            name:"zhangsan",
            age:12,
            id:101
        }
        console.log(user);
        //对象转化为json字符串
        var juser = JSON.stringify(user);
        console.log(juser);
        //json字符串解析成对象
        var user1 = JSON.parse(juser);
        console.log(user1);
```

![image-20210805092533912](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805092533912.png)

### 面向对象

#### 面向对象原型继承

```javascript
var User = {
    name : "User",
    age : 100,
    run : function () {
        console.log(this.name + "正在跑步！")
    }
}

var zhangsan = {
    name : "张三"
}

//张三的原型是User
zhangsan.__proto__ = User;
```

![image-20210805093714017](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805093714017.png)

![image-20210805093918667](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805093918667.png)

#### 面向对象class继承

```javascript
        //ES6  之前
/*        function Student(name) {
            this.name = name;
        }

        //给student新增一个方法
        Student.prototype.hello = function () {
            alert("hello");
        }*/

        //ES6之后
        //定义一个student的类
        class Student{
            constructor(name){
                this.name = name;
            }

            hello(){
                alert("hello");
            }
        }

        var zhangsan = new Student("张三");
        var lisi = new Student("李四");
        var 王二 = new Student("王二");
```

![image-20210805095023363](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805095023363.png)

#### 继承

```javascript
        //继承
        class litteStudent extends Student{
            constructor(name,grade) {
                super(name);
                this.grade = grade;
            }

                myGrade(){
                    alert(this.name+"是一名小学生");
                }
        }

        var lihua = new litteStudent("李华",3);
        lihua.myGrade();
```

![image-20210805095444163](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805095444163.png)

**本质：还是查看对象原型**

![image-20210805095623532](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805095623532.png)

![image-20210805100944211](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805100944211.png)

### 操作BOM对象(浏览器对象模型)

浏览器对象模型

javascript和浏览器关系

js的诞生就是为了能够在浏览器中运行



> window对象

window代表浏览器窗口

```javascript
window.innerHeight;
window.innerWidth;
window.outerHeight;
window.outerWidth;
window.innerWidth;
```

> Navigator

Navigator 封装了浏览器信息

```javas
navigator.appVersion;
"5.0 (Windows)"
navigator.userAgent;
"Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:90.0) Gecko/20100101 Firefox/90.0"
navigator.platform;
"Win32"
```

大多数时候不会使用`navigator`对象，因为会被人为改变

不建议使用这些属性来判断和编写代码



> screen



```javascript
screen.width;
1920
screen.height;
1080
```



> location（*）



location代表当前页面的URL信息

```javascript
host: "localhost:63342"
href: "http://localhost:63342/demo_week3/JavaScript/%E9%9D%A2%E5%90…class%E7%BB%A7%E6%89%BF.html?_ijt=kl6vuqv612ga6m0uvkq1mh0plm"
protocol: "http:"//协议
reload: function reload()//刷新网页
//设置新的地址
location.assign('https://www.baidu.com')
```



> document

document代表当前页面文档信息

```javascript
document.title;
"百度一下，你就知道"
document.title = "youxin";
"youxin"
```

![image-20210805102936127](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805102936127.png)

获取具体的文档树节点：

```html
    <script>
        var dl1 = document.getElementById("dl1");
    </script>
</head>
<body>
<dl id="dl1">
    <dt>java</dt>
    <dd>javaEE</dd>
    <dd>javaSE</dd>
</dl>
```

获取cookie:

```javascript
document.cookie;
```

![image-20210805103441944](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805103441944.png)



> history



```javascript
history.back();//后退
history.forward();//前进
```



### 操作DOM对象（文档对象模型）

> 核心

浏览器网页就是一个DOM树形结构

- 更新：更新DOM节点
- 遍历DOM节点：得到DOM节点
- 删除：删除一个DOM节点
- 添加：添加一个新的节点

要操作一个DOM节点，就必须要先获取这个DOM节点

> 获取DOM节点

```html
<body>
<div id="father">
<h1>标题1</h1>
<p id="p1">p1</p>
<p class="p2">p2</p>
</div>


<script>
    'use strict';
    var h1 = document.getElementsByTagName("h1")//获取标签名
    console.log(h1)
    var p1 = document.getElementById('p1');
    console.log(p1);
    var p2 = document.getElementsByClassName('p2');
    console.log(p2);
    var father = document.getElementById('father');
    var children = father.children;
    var firstChild = father.firstChild;
    var lastChild = p1.lastChild;
</script>
</body>
```



> 更新节点

```html
<div id="div1">

</div>


<script>
    var div1 = document.getElementById('div1');
    console.log(div1);
    div1.innerText = "hello world";//修改文本的值
</script>
```

![image-20210805110517603](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805110517603.png)

```javascript
div1.innerHTML = '<b>hello world</b>'//可以解析html标签
```

![image-20210805110705173](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805110705173.png)

操作样式：

```javascript
    div1.style.color = 'red';//属性使用字符串
    div1.style.fontSize = '100px';//注意驼峰命名
```

![image-20210805110904910](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805110904910.png)



> 删除节点

删除节点的步骤，先获取父节点，再通过父节点删除自己

```html
<div id="father">
    <h1>标题1</h1>
    <p id="p1">p1</p>
    <p class="p2">p2</p>
</div>


<script>
    var son = document.getElementById('p1');
    var father = son.parentElement;
    father.removeChild(son);
</script>
```

![image-20210805111847812](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805111847812.png)

```javascript
    var childrens = father.children;//删除是一个动态的过程
    father.removeChild(childrens[2]
```

注意：删除多个节点的时候，children是在时刻变化的，删除节点的时候一定要注意。



> 插入节点

获得了某个DOM节点，假设这个DOM节点是空的，通过innerHTML就可以增加一个元素了，但是如果这个DOM节点已经存在元素了，就不能这么干了！会产生覆盖。



追加：

```html
<p id="js">JavaScript</p>
<div id="list">
    <p id="ee">JavaEE</p>
    <p id="se">JavaSE</p>
    <p id="me">JavaME</p>
</div>


<script>
    var js = document.getElementById('js');
    var list = document.getElementById('list');
    list.appendChild(js);//追加到后面
</script>
```

![image-20210805112904411](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805112904411.png)

![image-20210805112918654](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805112918654.png)

创建一个新的节点然后追加：

```javascript
    //创建一个新的节点
    var newP = document.createElement('p');
    newP.id = 'newP';
    newP.innerText = "Hello World";
    list.appendChild(newP);
```

![image-20210805113150879](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805113150879.png)

![image-20210805113203857](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805113203857.png)

```html
<div id="div0">
<p id="js">JavaScript</p>
<div id="list">
    <p id="ee">JavaEE</p>
    <p id="se">JavaSE</p>
    <p id="me">JavaME</p>
</div>
</div>


<script>
    //var body = document.getElementsByTagName('body');//注意：因为是获取的标签，所以这里获取的是一个数组
    var div0 = document.getElementById('div0');
    var js = document.getElementById('js');//已存在的节点
    var list = document.getElementById('list');
    list.appendChild(js);
    //创建一个新的节点
    var newP = document.createElement('p');
    newP.id = 'newP';
    newP.innerText = "Hello World";
    list.appendChild(newP);
    var div2 = document.createElement('div2');
    div2.id = 'div2';
    div2.innerHTML = '<p>first</p>' +
                     '<p>second</p>'+
                     '<p>third</p>';
    div0.appendChild(div2);
    //body[0].appendChild(div2);//注意: 因为是数组，所以这里是需要用第一个body添加子元素
```

![image-20210805114206806](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805114206806.png)

```javascript
    //创建一个标签节点(通过这个属性，可以设置任意的值)
    var script = document.createElement("script");
    script.setAttribute('type','text/javascript');
    script.setAttribute('src','js/script.js');
    div0.appendChild(script);
```

![image-20210805115026044](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805115026044.png)



> insert

```javascript
	var js = document.getElementById('js');//已存在的节点
    var list = document.getElementById('list');
    var ee = document.getElementById('ee');
	//要包含的节点，insertBefore(newNode,目标节点)
	list.insertBefore(js,ee);
```

![image-20210805141507323](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805141507323.png)



> 密码md5加密

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src=https://cdn.bootcss.com/blueimp-md5/2.10.0/js/md5.min.js></script>
</head>
<body>
<form action="#" method="get">
    <p>
        <span>用户名</span><input type="text" id="username" name="username"><br>
    </p>
    <p>
        <span>密码:</span><input type="password" id="input_password"><br>
    </p>
    <input type="hidden" name="password" id="pwd">
        <button type="submit" onclick="login()">提交</button><br>
</form>

<script>
    function login() {
        var uname = document.getElementById('username');
        var input_pwd = document.getElementById('input_password');
        var md5_pwd = document.getElementById('pwd');
        //md5算法
        md5_pwd.value = md5(input_pwd.value);
        // input_pwd.value = md5(input_pwd.value);
        console.log(uname.value+'  :  '+input_pwd.value);
    }
</script>
</body>
</html>
```

![image-20210805150129648](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805150129648.png)



## JQuery

JavaScript 和 JQuery：

**1.JavaScript 是通过==<script></script>==标签插入到HTML页面，可由所有的现代浏览器执行的一种轻量级的编程语言。**

**2.JQuery是一个JavaScript函数库。或者说是JavaScript中最流行的一种框架。**



#### 获取JQuery

可以获取网络CDN或者下载JQuery库到本地引用

如：

```html
<script src="http://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
```

```html
<a href="" id="test_jquery">点击一下</a>
<script>
    /*
    * 公式：$(选择器).action()
    * */

    $("#test_jquery").click(function () {
        alert("hello Jquery")
    })
</script>
```

附：[JQuery查看方法大全网址](https://jquery.cuishifeng.cn/index.html)

### 事件

鼠标事件，键盘事件，其他事件

![image-20210805160827246](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805160827246.png)

```html
<!-- 获取鼠标当前坐标 -->
mouse:<span></span>
<div id="divMove">
    在这里移动鼠标
</div>

<script>
    <!-- 当网页元素加载完毕后响应事件 -->
    $(function () {
        $('#divMove').mousemove(function (e) {
            $('#divMove').text('x:'+ e.pageX+"Y:"+e.pageY);
        })
    })
</script>
```

![image-20210805153915083](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805153915083.png)



### JQuery操作DOM元素

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="https://code.jquery.com/jquery-latest.min.js"></script>
</head>
<body>
<ul id="ul">
    <li id="js">JavaScript</li>
    <li name="java">java</li>
    <li id="c_plus">c++</li>
</ul>
<script>

    var text = $('#ul li[name = java]').text();//获取值
    console.log(text);
    var text1 = $('#ul li[name = java]').text('javaEE');//设置值
</script>
</body>
</html>
```

![image-20210805155220567](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805155220567.png)

```javascript
$('#ul').html('<b>你好</b>');//设置值
```

操作css:

```javascript
$("#ul li[id=js]").css("color","blue");
$('#ul li[id=c_plus]').css({'color':'red','font-size':'20px'});
```

![image-20210805160229159](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210805160229159.png)

元素的显示和隐藏：

```javascript
$('#ul li[id=c_plus]').hide();
$('#ul li[id=c_plus]').show();
```

本质 hide() = display : none

