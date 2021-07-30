## String、StringBuffer、StringBuilder

#### String和StringBuilder本质区别

- String是一个不可改变的字符串序列
- StringBuilder是一个可以改变的字符串序列

```java
/*
* String类比较特殊，直接写一个双引号，实际上就是创建了一个字符创对象
* */
public class StringTest01 {
    public static void main(String[] args) {
        String s = "abc";
        s = "def";//这一步只是记录了一个新的对象的地址，而原来“abc”对象的内容根本没有改变
        
        System.out.println(s);
    }
}

//StringBuilder：可以改变的字符序列，字符串的缓冲区（提高效率）
        StringBuilder sb = new StringBuilder("aaaaabbbbb");
        sb.delete(3,5);
        System.out.println(sb);
```

String 和StringBuilder速度比较：

```java
public static void main(String[] args) {
        getStringResult();
        getStringBuilderResult();
    }

    private static void getStringBuilderResult() {
        //耗时11ms
        StringBuilder sb = new StringBuilder("");
        Long start = System.currentTimeMillis();
        for (int i =0;i < 100000;i++){
            sb.append(i);//使用的是拼接而不是+了
        }
        System.out.println(sb);
        Long end = System.currentTimeMillis();
        System.out.println("总共耗时：" + (end - start) + "ms");
    }

    private static void getStringResult() {
        //耗时20411ms
        String s = "";
        Long start = System.currentTimeMillis();
        for (int i =0;i < 100000;i++){
            s += i;
        }
        System.out.println(s);
        Long end = System.currentTimeMillis();
        System.out.println("总共耗时：" + (end - start) + "ms");
    }
```

输出：

![image-20210727165328199](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727165328199.png)

所以对常见字符串拼接推荐使用StringBuilder

字符串效率低的原因是因为字符串在用“+”做拼接的时候每一次都会产生一个新的字符串， Java语言为字符串连接运算符（+）提供特殊支持，并为其他对象转换为字符串。  字符串连接是通过`StringBuilder` （或`StringBuffer`  ）类及其`append`方法实现的。字符串是通过toString()实现的。

![image-20210727170232246](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727170232246.png)

而StringBuilder通过所有拼接都在一个StringBuilder缓冲区中同一拼接后进行一次toString完成拼接。

![image-20210727170414251](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727170414251.png)

#### 问题：

在工作中如果在业务层进行拼接sql，使用String去接收嘛？

答：如果Sql语句拼接的内容较少的话，可以y用String拼接，如果Sql语句拼接的内容很多，就应该用StringBuilder。

在项目中如果频繁是用拼接，最好用StringBuilder

#### StringBuffer和StringBuilder区别

##### StringBuffer:

线程安全，可变的字符序列。字符串缓冲区就像一个[`String`](../../java/lang/String.html) ，但可以修改。在任何时间点，它包含一些特定的字符序列，但可以通过某些方法调用来更改序列的长度和内容。

字符串缓冲区可以安全地被多个线程使用。  这些方法在必要时进行同步，以便任何特定实例上的所有操作都按照与所涉及的各个线程所执行的方法调用顺序一致的顺序发生。 

StringBuffer的主要`StringBuffer`是`append`和`insert`方法，它们被重载以便接受任何类型的数据。  每个都有效地将给定的数据转换为字符串，然后将该字符串的字符附加或插入到字符串缓冲区。  `append`方法总是在缓冲区的末尾添加这些字符;  `insert`方法将`insert`添加到指定点。

每当涉及源序列（例如从源序列追加或插入）的操作发生时，该类仅在执行操作的字符串缓冲器上进行同步，而不在源上。  请注意，虽然`StringBuffer`被设计为可以安全地从多个线程并发使用，但如果构造函数或`append`或`insert`操作被传递通过线程共享的源序列，则调用代码必须确保该操作具有一致且不变的视图在操作期间的源序列。  呼叫者通过使用不可变的源序列，或者不跨线程共享源序列，可以在呼叫期间持有锁来满足这一点。 

每个字符串缓冲区都有一个容量。  只要字符串缓冲区中包含的字符序列的长度不超过容量，就不必分配新的内部缓冲区数组。  如果内部缓冲区溢出，则会自动变大。 

从版本JDK 5开始，这个类别已经被一个等级类补充了，这个类被设计为使用一个线程`StringBuilder` 。  `StringBuilder`应该使用`StringBuilder`类，因为它支持所有相同的操作，但它更快，因为它不执行同步。

##### StringBuilder:

一个可变的字符序列。此类提供与`StringBuffer`的API，但不保证同步。此类设计用作简易替换为`StringBuffer`在正在使用由单个线程字符串缓冲区的地方（如通常是这种情况）。在可能的情况下，建议使用这个类别优先于`StringBuffer` ，因为它在大多数实现中将更快。

StringBuilder的主要`StringBuilder`是`append`和`insert`方法，它们是重载的，以便接受任何类型的数据。  每个都有效地将给定的数据转换为字符串，然后将该字符串的字符附加或插入字符串构建器。  `append`方法始终在构建器的末尾添加这些字符;  `insert`方法将`insert`添加到指定点。

例如，如果`z`引用当前内容为“ `start`  ”的字符串构建器对象，那么方法调用`z.append("le")`将导致字符串构建器包含“ `startle`  ”，而`z.insert(4, "le")`会将字符串构建器更改为包含“ `starlet` ”。

每个字符串构建器都有一个容量。  只要字符串构建器中包含的字符序列的长度不超过容量，则不需要分配新的内部缓冲区。  如果内部缓冲区溢出，则会自动变大。 

StringBuilder的`StringBuilder`不能安全使用多线程。 如果需要同步，  [那么](../../java/lang/StringBuffer.html)建议使用[`StringBuffer`](../../java/lang/StringBuffer.html) 。 

**相同点**：

StringBuffer和StringBuilder的功能是完全一样的

**不同点**：

- StringBuffer是JDK1.0出现的，线程安全的
- StringBuilder是jdk1.5出现的，线程不安全（不同步）
- 安全：效率低
- 不安全：效率高

开发过程中一对sql拼接一般是单线程，一般还是用StringBuilder。