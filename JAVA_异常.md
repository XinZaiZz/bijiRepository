## JAVA 异常

### 什么是异常：

在程序运行过程中出现的错误，称为`异常`。异常就是程序运行过程中出现了不正常现象导致程序的中断。

在Java中，把各种异常现象进行了抽象形成了异常类。

### 异常的分类

#### 异常的类图结构：

![img](https://img-blog.csdnimg.cn/20200524101154585.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NtaWxlaGFwcGluZXNz,size_16,color_FFFFFF,t_70)

#### 异常分类

异常主要分为：错误、一般性异常（受控异常）、运行时异常（非受控异常）

**错误**
如果应用程序出现了Error，那么将无法恢复，只能重新启动应用程序，最典型的Error的异常是：OutOfMemoryError

**受控异常**
这种异常属于一般性异常，出现了这种异常必须显示的处理，不显示处理java程序将无法编译通过。编译器强制普通异常必须try…catch处理，或用throws声明继续抛给上层调用方法处理，所以普通异常也称为checked异常。

**非受控异常**
非受控异常也即是运行时异常（RuntimeException），这种系统异常可以处理也可以不处理，所以编译器不强制用try…catch处理或用throws声明，所以系统异常也称为unchecked异常。

此种异常可以不用显示的处理，例如被0除异常，java没有要求我们一定要处理， 当出现这种异常时，肯定是程序员的问题，也就是说，健壮的程序一般不会出现这种系统异常。

### 异常的处理

java是采用面向对象的方式来处理异常的。处理过程：

1.抛出异常：在执行一个方法时，如果发生异常，则这个方法生成代表该异常的一个对象，停止当前执行路径，并把异常对象提交给JRE

2.捕获异常：JRE得到该异常后，寻找相应的代码来处理该异常。JRE在方法的调用栈中查找，从生成异常的方法开始回溯，直到找到相应的异常处理代码为止。

抛出异常：throw，throws

捕获异常：try，catch，finally

抛出异常throw

throw用在方法内，用来抛出一个异常对象，将这个异常对象传递到调用者处，并结 束当前方法的执行。

使用的格式：

```java
throw new 异常类名(参数)；
```

如：

```java
public class DemoThrow {
    public static void main(String[] args) {
      int a =   DemoThrow.div(4,0);
      System.out.println(a);
    }
 
   public static int div(int a,int b)
      {
            if(b==0)
              throw new ArithmeticException("异常信息：除数不能为0");//抛出具体问题，编译时不检测
            return a/b;
     }
}
```

声明抛出异常throws

运用于方法声明之上，用于表示当前方法不处理异常，而是提醒该方法的调用者来处理异常

使用格式：

```java
修饰符 返回值类型 方法名（参数） throws 异常类名1，异常类名2 ... { }
```

如：

```java
public class DemoThrows {
 
 
    public static void main(String[] args) throws FileNotFoundException{
        readFile();
    }
 
    public static  void readFile() throws FileNotFoundException {
        InputStream is = new FileInputStream("E:/iodemo/ch01.txt");
    }
}
```

try代码块

```java
try {
   ...  //监视代码执行过程，一旦返现异常则直接跳转至catch，
        // 如果没有异常则直接跳转至finally
} catch (SomeException e) {
    ... //可选执行的代码块，如果没有任何异常发生则不会执行；
        //如果发现异常则进行处理或向上抛出。
} finally {
    ... //必选执行的代码块，不管是否有异常发生，
        // 即使发生内存溢出异常也会执行，通常用于处理善后清理工作。
}
```

#### RuntimeException 运行时异常

这类异常通常是有编程错误导致的，所以在编写程序时，并不要求必须使用异常处理机制来处理这类异常，经常需要通过增加“逻辑处理来避免这些异常”

```java
public class ExceptionTest {
    public static void main(String[] args) {
        //除数为0异常
        /*
        * Exception in thread "main" java.lang.ArithmeticException: / by zero
	      at com.exception.ExceptionTest.main(ExceptionTest.java:5)
        */
        int a = 0;
        int b = 1;
        if(a != 0){
            System.out.println(b/a);
        }else {
            System.out.println("除数不能为零");
        }
    }
}
```

##### 常见异常：NullPointerException

如：

```java
String str = null;
System.out.println(str.length());
```

一般是对象为空，而调用了对象的方法

一般解决办法为

```java
		String str = null;
        if (str != null) {
            System.out.println(str.length());
        }else {
            System.out.println("str对象为空！！");
        }
```

##### 常见异常：ClassCastException(类型转换异常)

如：

```java

        class Animal{}
        class Dog extends Animal{}
        class Cat extends Animal{}
        Animal animal = new Dog();
        Cat c = (Cat) animal;
```

解决：

```java
		class Animal{}
        class Dog extends Animal{}
        class Cat extends Animal{}
        Animal animal = new Dog();
        if (animal instanceof Cat){
            Cat cat = (Cat) animal;
        }
```

##### 常见异常：ArrayIndexOutOfBoundsException(数组越界异常)

```java
        int[] a = new int[4];
        System.out.println(a[5]);
```

解决：

```java
        int[] a = new int[4];
        int b = 5;
        if (a.length > b){
            System.out.println(a[b]);
        }else {
            System.out.println("数组越界！");
        }
```

##### 常见异常：NumberFormatException(数字格式异常)

```java
        String str = "123abc";
        System.out.println(Integer.parseInt(str));
```

解决：

可以引入正则表达式判断是否为数字

#### 编译器异常：CheckedException

即在编写代码时就显示异常，需要在运行前解决

捕获异常用：try-catch-finally（可以使用多的catch，finally语句最多只能有一条，根据自己的需要可有可无）

![image-20210727152132333](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727152132333.png)

```java
/*
* 使用try-catch-finally处理
* */
public static void main(String[] args) {
        FileReader fr = null;
        try {
            fr = new FileReader("d:/aaa.txt");
            char read = (char)fr.read();
            System.out.println(read);
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException ioe){
            //如果有多个异常，并且有子类和父类关系，则要将子类写在前面，父类写在后面
            ioe.printStackTrace();
        }finally {
            try {
                if (fr != null) {
                    fr.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
            System.out.println("执行完毕！");
        }

    }
```

##### 方法二：throws

```java
/*
* 使用throws声明异常
* */
public class ThrowsExceptionTest {
    public static void main(String[] args) throws IOException {//抛出给jre
        demoException();
    }
    public static void demoException() throws IOException {//抛出给main方法
        FileReader fr = null;
            fr = new FileReader("d:/aaa.txt");
            char read = (char)fr.read();
            System.out.println(read);

                if (fr != null) {
                    fr.close();
                }

            System.out.println("执行完毕！");
        
    }
}
```

#### 自定义异常

在程序中，可能会遇到JDK提供的任何标准异常类都无法充分描述清楚我们想要表达的问题，这种情况下可以创建自己的异常类，即自定义异常类

自定义异常类只需从哪个Exception类或者它的子类派生一个子类即可。

自定义异常类如果继承Exception类，则为受检查异常，必须对其进行处理，吐过不想处理，可以让自定义异常类继承运行时异常RuntimeException类。

习惯上，自定义异常类应该包含两个构造器：一个是默认构造器，另一个是带有详细信息的构造器。

```java
/*
*
* 自定义年龄错误异常
* */
public class IllegalAgeException extends RuntimeException {

    public IllegalAgeException() {
    }

    public IllegalAgeException(String message) {
        super(message);
    }
}
```

在给age属性赋值时：

```java
    public void setAge(int age) {
        if (age < 0){
            throw new IllegalAgeException("年龄不能为负数");
        }
        this.age = age;
    }
```

编写：

```java
public void test01(){
    Student student = new Student();
    student.setAge(-2);
        System.out.println(student);
    }
```

报错：

![image-20210727161102662](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727161102662.png)

如果是自定义异常继承的是Exception类

在编写代码过程中出现了错误就会马上报错，必须通过try-catch或者throws处理异常

即

```java
if (age < 0){
            try {
                throw new IllegalAgeException("年龄不能为负数");
            } catch (IllegalAgeException e) {
                e.printStackTrace();
            }
        }
```

##### 使用异常机制建议

1、要避免使用异常处理代替错误处理，这样会降低程序的清晰性，并且效率低下；

2、处理异常不可以代替简单测试--只在异常情况下使用异常机制；

3、不要进行小粒度的异常处理--应该将整个任务包装在一个try语句块中；

4、异常往往在高层处理。