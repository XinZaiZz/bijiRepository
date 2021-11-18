## JAVA 多线程

### 多任务

- 多任务就是同时运行多个任务
- 操作系统改轮流让多个任务交替执行

### 程序（program）

是为完成特定任务、用某种语言编写的一组指令的集合。即指一段静态的代码，静态对象

### 进程(Process)

一个任务就是一个进程

如：运行中的QQ，运行中的MP3播放器

程序是静态的，进程是动态的

进程作为资源分配的单位，系统在运行时会为每个进程分配不同的内存区域

###线程（Thread）

在某些进程内部还需要同时执行多个子任务称之为线程

一个java应用程序至少有三个线程:main()主线程，gc()垃圾回收线程，异常处理线程。

#### 并行与并发

并行：多个CPU同时执行多个任务。比如：多个人同时做不同的事。

并发：一个CPU同时执行多个任务。比如：秒杀、多个人做同一件事。

#### 进程和线程的关系

- 一个进程可以包含一个或多个线程（至少一个线程）
- 线程是操作系统调度的最小任务单位
- 如何调度线程完全由操作系统决定

#### 实现多任务的方法

- 多进程模式（每个进程只有一个线程）
- 多线程模式（一个进程有多个线程）
- 多进程+多线程模式（复杂度最高）

![image-20210727173654277](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727173654277.png)

#### 多线程VS多进程

- 创建进程比创建线程开销大
- 进程间通信比线程间通信慢
- 多进程稳定性比多线程高

#### Java多线程

java语言内置多线程支持：

- 一个Java程序实际上是一个JVM进程
- JVM用一个主线程来执行main()方法
- 在main()方法中又可以启动多个线程

#### 多线程优点

1、提高应用程序的响应。对图形化界面更有意义，可以增强用户体验。

2、提高计算机系统CPU的利用率。

3、改善程序结构。将既长又复杂的进程分为多个线程，独立运行，利于理解和修改。

#### 创建线程

![image-20210727174200623](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727174200623.png)

![image-20210727174209966](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727174209966.png)

```java
public static void main(String[] args) {
        System.out.println("main start--");
        Thread thread = new Thread(){
            @Override
            public void run() {
                System.out.println("thread run--");
                System.out.println("thread end--");
            }
        };
        thread.start();
        System.out.println("main end--");
    }
```

![image-20210727174507732](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727174507732.png)

程序本身无法确定是先输出main end还是thread run因为主线程和thread线程是同步进行的。

线程开辟后直接调用run方法事无效的，必须调用start方法才能启动新线程

![image-20210727175448252](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727175448252.png)

####创建线程一：继承Thread类

```java
/*
 * 多线程的创建：方式一：继承与Thread类
 * 1.创建一个继承与Thread类的子类
 * 2.重写Thread类的run() --> 此线程执行的操作声明在run()中
 * 3.创建Thread类的子类的对象
 * 4.通过此对象调用start()
 * 例：遍历100以内的所有偶数
 * */

class MyThread extends Thread{
    //重写run()
    @Override
    public void run() {
        for (int i = 0;i<100;i++){
            if (i % 2 ==0){
                System.out.print(i+"   ");
            }
        }
    }
}
public class ThreadTest02 {
    public static void main(String[] args) {
        //创建Thread类的子类的对象
        MyThread myThread = new MyThread();
        //通过对象调用start()，启动线程，调用当前线程中的run()
        myThread.start();
        //如下操作仍然是在main线程中的执行的
        for (int i = 0;i<100;i++){
            if (i % 2 !=0){
                System.out.print(i+" * ");
            }
        }
    }

}
```

结果同时运行：

![image-20210727201112599](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727201112599.png)

问题：不能通过直接调用run()方法启动线程；线程只能start一次，不能将已经start的线程再次start,这时需要重新创建一个线程对象。

##### 线程的常用方法

void start()：启动线程，并执行对象的run()方法

run()：线程在被调度时执行的操作

String getName()：返回线程的名称

void setName(String name)：设置该线程名称

static Thread currentThread()：返回当前线程。在Thread子类中就是this,常用于主线程和Runable()实现类。

```java
/*
* 测试Thread中的常用方法
* void start()：启动线程，并执行对象的run()方法

run()：线程在被调度时执行的操作

String getName()：返回线程的名称

void setName(String name)：设置该线程名称

static Thread currentThread()：返回当前线程。

yield():释放当前CPU的执行权，可能又会被抢回来

join():在线程a中调用线程b的join(),此时线程a就进入到阻塞状态，知道b执行完后a才结束阻塞状态

stop():已过时，当执行此方法是强制结束线程

sleep()：睡眠，一毫秒为单位

isAlive():判断当前线程是否存活
* */

class HelloThread extends Thread{
    @Override
    public void run() {

        for (int i = 0;i<100;i++){
            try {
                sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            if (i % 2 == 0){
                System.out.println(Thread.currentThread().getName()+"--"+i);
            }
            if ( i % 20 ==0){
                this.yield();
            }
        }
    }
    public HelloThread(String name) {
        super(name);
    }

}
public class ThreadMethodTest {
    public static void main(String[] args) throws InterruptedException {
        HelloThread helloThread = new HelloThread("thread1");
//        helloThread.setName("线程1");
        helloThread.start();
        //给主线程命名
        Thread.currentThread().setName("主线程");
        for (int i = 0;i<100;i++){
            if (i % 2 == 0){
                System.out.println(Thread.currentThread().getName()+"--"+i);
            }
            if ( i == 20 ){
                helloThread.join();
            }
        }
    }

}
```

```java
/*
* 窗口卖票test
* 存在线程安全问题，即第一张票被每个窗口都卖了一次
* */
class TicketThread extends Thread{
    private static int ticket = 100;

    @Override
    public void run() {
        while(true){
            //只要还有票，就可以被卖出去一张
            if (ticket > 0){
                    System.out.println(Thread.currentThread().getName()+" :卖票，票号为: " + ticket);
                    ticket--;
            }else
                break;
        }

    }
}
public class ThreadTicketTest {
    public static void main(String[] args) {
        //创建线程对象
        TicketThread td1 = new TicketThread();
        TicketThread td2 = new TicketThread();
        TicketThread td3 = new TicketThread();

        //对线程起别名
        td1.setName("窗口1");
        td2.setName("窗口2");
        td3.setName("窗口3");

        //开启线程
        td1.start();
        td2.start();
        td3.start();
    }
}
```

![image-20210728092125908](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210728092125908.png)

#### 创建线程二：实现Runable接口

```java
/*
* 实现Runnable接口创建线程
* 1.创建一个实现了Runnable接口的类
* 2.实现类去实现Runnable中的抽象方法：run()
* 3.创建实现类的对象
* 4.将此对象作为参数传递到Thread类的构造器中
* 5.通过Thread类的对象调用start()
* */

//1.创建一个实现了Runnable接口的类
class RunnThread implements Runnable{

    //2.实现类去实现Runnable中的抽象方法：run()
    @Override
    public void run() {
        for (int i = 1; i<= 100;i++){
            System.out.println(Thread.currentThread().getName()+"-->"+i);
        }
    }
}
public class RunnableThreadTest {
    public static void main(String[] args) {
        //3.创建实现类的对象
        RunnThread rt = new RunnThread();
        //4.将此对象作为参数传递到Thread类的构造器中
        Thread thread = new Thread(rt);
        //5.通过Thread类的对象调用start()
        thread.start();
    }
}
```

实现Runnable接口开启线程实现窗口售票demo：

```java
/*
 * 窗口卖票test
 * 存在线程安全问题，即第一张票被每个窗口都卖了一次
 * */

class WindowThread implements Runnable{
    private int ticket = 100;
    @Override
    public void run() {
        while(true){
            //只要还有票，就可以被卖出去一张
            if (ticket > 0){
                System.out.println(Thread.currentThread().getName()+" :卖票，票号为: " + ticket);
                ticket--;
            }else
                break;
        }
    }
}
public class RunnableTicketTest {
    public static void main(String[] args) {
        //创建实现类对象
        WindowThread wt = new WindowThread();
        //传递参数到构造器中
        Thread thread1 = new Thread(wt);
        Thread thread2 = new Thread(wt);
        Thread thread3 = new Thread(wt);
        //起别名
        thread1.setName("窗口1");
        thread2.setName("窗口2");
        thread3.setName("窗口3");
        //开启线程
        thread1.start();
        thread2.start();
        thread3.start();
    }
}
```

##### 比较创建线程的两种方式

java为单继承存在局限性，实现类可以多个，所以用实现类更好，开发中优先选择实现Runnable接口的方式。

实现的方式可以体验一种共享数据的概念（只需要创建一个线程对象），而继承方式中每一次都会创建一个新的线程对象。

#### 线程池

```java
public class ThreadPool {
    public static void main(String[] args) {
        //corePoolSize:线程池核心线程大小，
        // maximumPoolSize:线程池最大线程数量，
        // keepAliveTime:空闲线程存活时间，
        // unit:空间线程存活时间单位，
        // workQueue:工作队列，
        // threadFactory:线程工厂，
        // handler:拒绝策略
        ThreadPoolExecutor threadPoolExecutor = new ThreadPoolExecutor(3, 5, 1L, TimeUnit.SECONDS, new ArrayBlockingQueue<>(3), Executors.defaultThreadFactory(), new ThreadPoolExecutor.AbortPolicy());

        for (int i = 0 ;i < 4;i++){
            threadPoolExecutor.execute(()->{
                System.out.println(Thread.currentThread().getName() + "===>办理业务");
            });
        }
    }
}
```

![image-20210825105457764](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210825105457764.png)



#### 线程优先级

![image-20210727175738139](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727175738139.png)

```java
/*
* 
* 用setPriority()设置线程优先级1--10级
* 1级用MIN_PRIORITY，十级用MAX_PRIORITY，5级为默认NORM_PRIORITY
* 不是优先级高的一定会先执行，只是一个概率问题
* */
class PriorityThread extends Thread{
    @Override
    public void run() {
        for (int i = 1;i <=100;i++){
            if (i % 2 ==0){
                System.out.println(Thread.currentThread().getName() + "-->" +i);
            }
        }
    }
}

public class ThreadPriorityTest {
    public static void main(String[] args) {
        //创建线程对象
        PriorityThread pt1 = new PriorityThread();
        PriorityThread pt2 = new PriorityThread();
        //设置线程优先级
        pt1.setPriority(Thread.MAX_PRIORITY);
        pt2.setPriority(Thread.MIN_PRIORITY);

        //设置线程别名
        pt1.setName("线程1");
        pt2.setName("线程2");
        //开启线程
        pt1.start();
        pt2.start();
    }
}
```

#### 线程概念总结

- java用Thread对象表示一个线程，通过调用start()启动一个线程
- 一个线程对象只能调用一个start()
- 线程的执行代码时run()方法
- 线程调度由操作系统决定，程序本身无法决定
- Thread.sleep()可以把当前线程暂停一段时间

#### 线程状态

![image-20210727180123101](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727180123101.png)

线程终止的原因：

run()方法执行到return语句返回（线程正常终止）

因为未捕获的异常导致线程终止（意外终止）

stop()方法

`thread.join();//等待线程thread执行结束再继续执行下一步`

#### 中断线程

如果一个线程需要执行一个长时间任务，就可能需要中断线程

![image-20210727192648688](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727192648688.png)

![image-20210727192701586](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727192701586.png)

![image-20210727192721616](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727192721616.png)

![image-20210727192756690](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210727192756690.png)

##### volatile

volatile关键字的目的是高数虚拟机：

每次访问变量时，总是获取主内存的最新值

每次修改变量后，立刻回写到主内存

