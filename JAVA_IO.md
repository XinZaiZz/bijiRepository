## JAVA IO

![img](https://www.bjsxt.com/wp-content/uploads/2018/08/11.jpg)

### 流的概念

内存与存储设备之间传送数据的通道。

按流向来分为输入流，输出流

按功能来分为节点流、处理流（包装流）节点流和处理流的关系：节点流处于io操作的第一线，所有操作必须通过他们进行；处理流可以对其他流进行处理（提高效率或操作灵活性）

按数据分为字节流、字符流：底层还是基于字节流操作，自动搜寻了指定的码表。

构造器：有构造器可以直接用，没有构造器要么是工具类，要么有静态方法，例如Math类和Runtime类。

##### 路径分隔符

```java
public class TestIO {
    public static void main(String[] args) {
        /*
        * "/"或"\" 名称分隔符 separator
        * */

        String path = "D:\\IdeaProject\\demo20210726\\src\\环境.txt";
        System.out.println(File.separatorChar);
        System.out.println(File.separator);
        //建议
        //1./
        path = "d:/IdeaProject/demo20210726/src/环境.txt";
        System.out.println(path);
        //2.常量拼接
        path = "d:" + File.separator + "IdeaProject" + File.separator + "demo20210726" + File.separator + "src" + File.separator + "环境.txt";
        System.out.println(path);
    }
}
```

输出：

![image-20210726201216629](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726201216629.png)

#####构建File对象：

```java
public class TestIO2 {
    /*
    * 构建File对象
    * */
    public static void main(String[] args) {
        //D:\IdeaProject\demo20210726\src\环境.txt
        String path = "D:/IdeaProject/demo20210726/src/环境.txt";
        //1.构建File对象
        File file = new File(path);
        System.out.println(file.length());
        //2.构建File对象
        file = new File("D:/IdeaProject/demo20210726/src","环境.txt");
        System.out.println(file.length());
        //3.构建File对象
        file = new File(new File("D:/IdeaProject/demo20210726/src"),"环境.txt");
        System.out.println(file.length());
    }
}
```

![image-20210726202116437](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726202116437.png)

##### 相对路径和绝对路径

```java
public class TestIO03 {
    /*
    * 相对路径和决定路径
    * 1、存在盘符：决定路径
    * 2、没有盘符：相对路径
    * */
    public static void main(String[] args) {
        String path = "D:/IdeaProject/demo20210726/src/环境.txt";
        //绝对路径
        File file = new File(path);
        System.out.println(file.getAbsolutePath());
        //相对路径
        file = new File("src/环境.txt");
        System.out.println(System.getProperty("user.dir"));
        System.out.println(file.getAbsolutePath());
    }
}
```

![image-20210726202728050](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726202728050.png)

File对象可以构建一个不存在的文件

![image-20210726202951698](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726202951698.png)

```java
public class TestIO04 {
    /*
    * 名称或路径
    * getName()
    * getPath()：相对，绝对
    * getAbsolutePath()
    * getParent()
    * */
    public static void main(String[] args) {
        //基本信息
        File file = new File("D:\\IdeaProject\\demo20210726\\src\\环境.txt");
        System.out.println("名称：" + file.getName());
        System.out.println("路径：" + file.getPath());
        System.out.println("绝对路径：" + file.getAbsolutePath());
        System.out.println("父路径：" + file.getParent());
        System.out.println("父对象：" + file.getParentFile().getName());
    }
}
```

![image-20210726204004221](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726204004221.png)

##### 文件状态

```java
public class TestIO05 {
    /*
    * 文件状态
    * 1.不存在：exists()
    * 2.存在
    *   文件：isFile()
    *   文件夹：isDirectory()
    * */
    public static void main(String[] args) {
        File file = new File("src/环境.txt");
        System.out.println("文件存在？"+file.exists());
        System.out.println("是否是文件？"+file.isFile());
        System.out.println("是否是文件夹？"+file.isDirectory());
    }
}
```

![image-20210726204623589](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726204623589.png)

##### 其他信息

```java
/*
    * 其他信息
    * length():字节数
    * */
    public static void main(String[] args) {
        File file = new File("D:\\IdeaProject\\demo20210726\\src\\环境.txt");
        System.out.println(file.length());
        file = new File("D:\\IdeaProject\\demo20210726\\src");
        System.out.println(file.length());
    }
```

![image-20210726205154373](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726205154373.png)

```java
/*
    * 其他信息
    * createNewFile():不存在才会创建成功
    * */
    public static void main(String[] args) throws IOException {
        File file = new File("D:\\IdeaProject\\demo20210726\\src\\test.txt");
        boolean newFile = file.createNewFile();
        System.out.println(newFile);
        file.delete();
    }
```

![image-20210726205457230](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210726205457230.png)

**不能创建文件夹**

```java
public class TestDir {
    /*
    * 创建目录
    * 1.mkdir()：确保上级目录存在，不存在创建失败
    * 2.mkdirs()：上级目录可以不存在，不存在一同来创建
    * */
    public static void main(String[] args) {
        File dir = new File("D:/IdeaProject/demo20210726/src/test");
        //创建目录
        boolean mkdir = dir.mkdir();
        boolean mkdirs = dir.mkdirs();
        System.out.println(mkdir);
        System.out.println(mkdirs);
    }
}
```

![image-20210727091214764](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727091214764.png)

```java
public class TestDir02 {

    /*
    * 列出下一级
    * 1.list():列出下一级名称
    * 2.listFiles()：列出下一级File对象
    * 打印子孙级目录和名称
    * */    
	public static void main(String[] args) {
        File dir = new File("D:/IdeaProject/demo20210726/src");

        //列出下一级名称
        String[] subNames = dir.list();
        for (String subName: subNames
             ) {
            System.out.println(subName);
        }

        //下级对象
        File[] files = dir.listFiles();
        for (File file: files
             ) {
            System.out.println(file);
        }
        printName(dir,0);
    }
        //打印子孙级目录和名称
    public static void printName(File dir,int deep){//deep用来记录层级
        for (int a = 0;a < deep; a++ ){
            System.out.print("-");
        }
        //打印路径和名称
        System.out.println("路径："+dir.getPath()+" 文件名称:"+dir.getName());
        if (null == dir||!dir.exists()){//递归头
            return;
        }else if (dir.isDirectory()){
            for (File file:dir.listFiles()
                 ) {
                printName(file,deep+1);//递归体
            }
        }
    }
}
```

![image-20210727093933770](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727093933770.png)

**统计文件夹大小**

```java
public class TestDir03 {
    /*
    * 统计文件夹的大小
    * */
    public static long length = 0;
    public static void main(String[] args) {
        File dir = new File("D:/IdeaProject/demo20210726/src");
        count(dir);
        System.out.println(length);
    }
    public static void count(File dir){
        //获取大小
        if (null != dir || dir.exists()){
            if (dir.isFile()){
                length += dir.length();
            }else {
                for (File file:dir.listFiles()){
                    count(file);
                }
            }
        }
    }
}
```

![image-20210727094847211](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727094847211.png)

#####InputStream 字节输入流

###### FileInputStream

public int read(byte[] b)//从流中读取多个字节，将读到内容存入b数组，返回实际读到的字节数；如果到达文件的尾部，则返回-1

```java
/*
*FileInputStream的使用
* 文件字节输入流
* */
public class IOputStreamTest {
    public static void main(String[] args) throws IOException {
        //1.创建FileInputStream,并指定文件路径
        FileInputStream fileInputStream = new FileInputStream("d:/aaa.txt");
        //读取文件read()方法只能读一个字节
        //fileInputStream.read();单个字节读取
//        int data = 0;
//        while ((data = fileInputStream.read()) != -1){
//            System.out.print((char)data);
//        }
        //一次读取多个字节
        /*byte[] bytes = new byte[3];
        int read = fileInputStream.read(bytes);
        System.out.println(new String(bytes));
        System.out.println(read);
        int read2 = fileInputStream.read(bytes);
        System.out.println(new String(bytes));
        System.out.println(read);*/
        //创建缓冲区
        byte[] bytes = new byte[1024];
        int count = 0;
        while ((count = fileInputStream.read(bytes)) != -1){
            System.out.println(new String(bytes,0,count));
        }
        //关闭
        fileInputStream.close();
    }
}
```



#####OutputStream 字节输出流

###### FileOutputStream

public void write(byte[] b)//一次写多个字节，将b数组中所有字节，写入输出流

```java
/*
* FileOutputStream
* 文件字节输出流
* */
public class OutputStreamTest {
    public static void main(String[] args) throws IOException {
        //创建文件字节输出流对象
        FileOutputStream fileOutputStream = new FileOutputStream("d:/bbb.txt",true);//true表示append添加到文件末尾
        //单个字节写入文件
//        fileOutputStream.write(97);
//        fileOutputStream.write('b');
        //多个字节写入
        String s = "hello world";
        fileOutputStream.write(s.getBytes());
        //关闭
        fileOutputStream.close();
    }

}
```

实现将aaa.txt中内容复制到bbb.txt中：

```java
/*\
* 使用文件字节流实现文件的复制
* */
public class IOputStreamTest {
    public static void main(String[] args) throws IOException {
        //文件字节输入流
        FileInputStream fileInputStream = new FileInputStream("d:/aaa.txt");
        //文件字节输出流
        FileOutputStream fileOutputStream = new FileOutputStream("d:/bbb.txt",true);
        //一边读，一边写
        byte[] bytes = new byte[1024];
        int count = 0;
        while ((count = fileInputStream.read(bytes)) != -1){
            fileOutputStream.write(bytes,0,count);
        }
        //关闭流
        fileInputStream.close();
        fileOutputStream.close();
        System.out.println("复制完毕");
    }
}
```

##### 字节缓冲流 BufferdInputStream/BufferedOutputStream

提高IO效率，减少访问磁盘的次数；

数据存储在缓冲区中，flush是将缓存区的内容写入文件中，也可以直接close().

```java
/*
* 使用字节缓冲流来读取文件
* */
public class BufferedInputStreamTest {

    public static void main(String[] args) throws IOException {
        //创建缓冲流
        FileInputStream fis = new FileInputStream("d:/aaa.txt");
        BufferedInputStream bis = new BufferedInputStream(fis);
        //读取
        int data = 0;
        while ((data = bis.read())!=-1){
            System.out.print((char)data);
        }
        //关闭
        bis.close();
    }
}
```

```java
/*
* 使用字节缓冲流写入对象
* */
public class BufferedOutputStreamTest{
    public static void main(String[] args) throws IOException {
        //创建字节缓冲流对象
        FileOutputStream fos = new FileOutputStream("d:/bbb.txt",true);
        BufferedOutputStream bos = new BufferedOutputStream(fos);
        //写入文件
        for (int i = 0 ;i< 10;i++){
            bos.write("hello world".getBytes());//先写入缓冲区8K
            bos.flush();//刷新到硬盘
        }
        //关闭
        bos.close();//内部会自动调用flush()
    }
}
```

##### 对象流

readObject()，writeObject(Object obj)

使用流传输对象的过程分为序列化和反序列化

**实体类中需要实现序列化接口，如`public class Student implements Serializable`**

```java
*
 * 使用ObjectOutputStream实现对象的序列化写入操作
  *要求：序列化类必须要实现Serializable接口
  * */
public class ObjectOutputStreamTest {
    public static void main(String[] args) throws IOException {
        //创建对象流
        FileOutputStream fos = new FileOutputStream("d:/bbb.txt");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        //实现序列化（写入操作）
        Student zhangsan = new Student("zhangsan" ,21);
        oos.writeObject(zhangsan);
        //关闭
        oos.flush();
        oos.close();
    }
```

反序列化

```java
/*
* 使用ObjectInputStream实现反序列化
* */
public class ObjectInputStreamTest {
    public static void main(String[] args) throws Exception {
        //创建对象流
        FileInputStream fis = new FileInputStream("d:/bbb.txt");
        ObjectInputStream ois = new ObjectInputStream(fis);
        //读取文件
        Student student = (Student)ois.readObject();
        //关闭
        ois.close();
        System.out.println(student.toString());
    }
}
```

![image-20210727113901227](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727113901227.png)

序列化版本号ID，保证序列化的类和反序列化的类是同一个类

使用transient修饰属性，这个属性就不能被序列化了如`private transient int age`

静态属性不能被序列化

序列化多个对象可以用集合

#### 字符流

当文件中有中文是字节流就不能读取了

##### Reader

###### FileReader：public int read(char[] c)//读取多个字符，将督导的内容存入c数组，返回实际读到的字符数；如果到达文件的尾部，则返回-1

```java
/*
* FileReader字节流读取文件数据
* */
public class FileReaderTest {
    public static void main(String[] args) throws IOException {
        //创建文件字符流
        FileReader fr = new FileReader("d:/aaa.txt");
        //读取
        //1.单个字符读取
        /*int data = 0 ;
        while ((data = fr.read()) != -1){
            System.out.print((char) data);
        }*/
        //2.缓冲区读取
        char[] chars = new char[1024];
        int count = 0;
        while ((count = fr.read(chars)) != -1){
            System.out.print(new String(chars,0,count));
        }
        //关闭
        fr.close();
    }
}
```



#####Writer

###### FileWriter：public void write(String str)//一次写多个字符，将b数组中的所有字符写入输出流

```java
/*
* 使用FileWriter写入文件
* */
public class FileWriterTest {
    public static void main(String[] args) throws IOException {
        //创建FileWriter对象
        FileWriter fw = new FileWriter("d:/aaa.txt",true);
        //写入
        fw.write("，昨天看起来天气不好！");
//        fw.append(",前天天气怎么样？",0,new String(",前天天气怎么样？").length());
        fw.flush();
        //关闭
        fw.close();
    }
}
```

用字符流实现文件复制：

```java
/*
* 使用FileReader和FileWriter复制文本文件，不能复制图片或其他二进制文件，只能复制有编码的文件
* */
public class FileCopyTest {
    public static void main(String[] args) throws IOException {
        //创建两个流
        FileWriter fw = new FileWriter("d:/bbb.txt");
        FileReader fr = new FileReader("d:/aaa.txt");
        //读写
        int data = 0 ;
        while ((data = fr.read()) != -1){
            fw.write(data);
            fw.flush();
        }
        //关闭
        fr.close();
        fw.close();
    }
}
```

字符流进行读取时是按编码进行字符读取，而图片或声音是二进制信息，不能用字符流读取。。

##### 字符缓冲流：BufferedReader/BufferedWriter 可以指定缓冲区大小，也可以使用默认的

```java
/*
* 使用字符缓冲流读取字符
* */
public class BufferedReaderTest {
    public static void main(String[] args) throws IOException {
        //创建字符缓冲流对象
        FileReader fr = new FileReader("d:/bbb.txt");
        BufferedReader br = new BufferedReader(fr);
        //读取
        /*char[] chars = new char[1024];
        int count = 0;
        while ((count = fr.read(chars)) != -1){
            System.out.print(new String(chars,0,count));
        }*/
        //第二种
        String s = null;
        while (( s = br.readLine()) != null){
            System.out.println(s);
        }
        //关闭
        br.close();
    }
}
```

```java
/*
* 使用BufferedWriter写入数据
* */
public class BufferedWriterTest {
    public static void main(String[] args) throws IOException {
        //创建对象
        FileWriter fw = new FileWriter("d:/ccc.txt");
        BufferedWriter bw = new BufferedWriter(fw);
        //写入
//        bw.write("好好学习，天天向上");
        for (int i = 1;i < 10 ;i++){
            bw.write("好好学习，每天向上");
            bw.newLine();
        }
        bw.flush();
        //关闭
        bw.close();
    }
}
```

![image-20210727133317924](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727133317924.png)

#### 打印流：PrintWriter

```java
/*
* 使用PrintWriter打印数据
* */
public class PrintWriterTest {
    public static void main(String[] args) throws FileNotFoundException {
        //创建PrintWriter对象
        PrintWriter pw = new PrintWriter("d:/ccc.txt");
        //打印
        pw.println(97);
        pw.println(true);
        pw.println("你好");
        pw.println(3.14);
        pw.println('a');
        pw.print(new Student("lisi",23));
        pw.flush();
        pw.close();
    }

}
```

![image-20210727133809432](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727133809432.png)

#### 转换流：InputStreamReader/OutputStreamWriter

可将字节流转换为字符流

可设置字符的编码方式