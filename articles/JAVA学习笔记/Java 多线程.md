# Java 多线程

&emsp;

### 主要内容

&emsp;

    什么是多线程
    线程的创建
    线程状态和生命周期
    线程调度
    同步与死锁

&emsp;

### 进程的概念

&emsp;

    进程是指可执行程序并存放在计算机存储器的一个指令序列，它是一个动态执行的过程。
    
    进程：线程是比进程还要小的运行单位，一个进程包含多个线程

    线程：线程可以看作一个子程序

&emsp;

### 线程的创建

&emsp;

    创建一个Thread类，或者一个Thread子类的对象
    创建一个实现Runnable接口的类的对象
    
&emsp;

### Thread 类（java.lang 包下）

&emsp;

<center>

|构造方法|说明|
|:-:|:-:|
|Thread()|创建一个线程对象|
|Thread(String name)|创建一个具有指定名称的线程对象|
|Thread(Runnable target)|创建一个基于 Runnable 接口实现类的线程对象|
|Thread(Runnable target, String name)|创建一个基于 Runnable 接口实现类，并且具有指定名称的线程对象|

</center>

### Thread类的常用方法

&emsp;

|方法|说明|
|:-:|:-:|
|public void run()|线程相关的代码写在该方法中，一般需要重写|
|public void start)|启动线程的方法|
|public static void sleep(long m)|线程休眠m毫秒的方法|
|public void join()|优先执行调用join()方法的线程|

&emsp;

### Runnable接口

&emsp;

    只有一个方法run();
    Runnable是Java中用以实现线程的接口任何实现线程功能的类都必须实现该接口

&emsp;

### 线程创建

&emsp;

    通过继承Thread类的方式创建线程类，重写run()方法。

&emsp;

#### **过继承Thread类的方式创建线程类，重写run()方法**

&emsp;

```java
package com.demo.thread1;

//  通过继承Thread类的方式创建线程类，重写run()方法。
//  由于多线程线程代码较少，为方便编写，故写同一文件下，事实上，我们并不推荐这么做
class MyThread extends Thread{
    public void run(){
        System.out.println(getName()+"该线程正在执行！");
    }
}

public class ThreadOne {
    public static void main(String[] args) {
        System.out.println("主线程1");
        MyThread mt = new MyThread();
        mt.start(); //  启动线程
        System.out.println("主线程2");
    }
}

```

&emsp;

```java
package com.demo.thread2;

class MyThread extends Thread{
    public MyThread(String name){
        super(name);

    }
    public void run(){
        for(int i=1 ; i<=10 ; i++){
            System.out.println(getName() + "正在运行" + i);
        }
    }
}

public class ThreadTwo {
    public static void main(String[] args) {

        MyThread mt1 = new MyThread("线程1");
        MyThread mt2 = new MyThread("线程2");
        mt1.start();
        mt2.start();
    }

}
```

&emsp;

#### **通过 Runnable 接口的方式创建**

&emsp;

#### 为什么要实现Runnable接口?  

&emsp;

    Java不支持多继承
    不打算重写Thread类的其他方法

&emsp;

```java
package com.demo.runnable;

class PrintRunnable implements Runnable{
    int i = 1;
    @Override
    public void run() {

        while(i <= 10){

            System.out.println(Thread.currentThread().getName() + "正在运行！" + (i++)); // 调用 Thread 类的静态方法 Thread.currentThread()
        }
    }
}

public class RunnableOne {
    public static void main(String[] args) {
        PrintRunnable pr1 = new PrintRunnable();
        Thread t1 = new Thread(pr1);
        t1.start();

        PrintRunnable pr2 = new PrintRunnable();
        Thread t2 = new Thread(pr2);
        t2.start();
    }
}

```

&emsp;

### 线程的状态

&emsp;

    - 新建状态（New）
        - 当你创建 Thread 或 Thread 子类对象时，线程进入了新建状态
    
    - 可运行状态（Runnable）（也叫做 就绪状态）
        - 当已创建好的线程对象，去调用 start() 方法，这时候线程对 象就进入了可运行状态
    
    - 正在运行状态（Running）
        - 当处于可运行状态的线程，一旦获取了 CPU 的使用权，就可以进入正在运行状态

    - 阻塞状态（Blocked）
        - 当线程遇到干扰，线程将进入阻塞状态。
    
    - 终止状态（Dead）


&emsp;

### 线程的生命周期

&emsp;

    线程从创建到启动直至运行结束的这一阶段的时间我们称之为线程的生命周期

&emsp;

### sleep() 方法的使用

&emsp;

### 将线程从正在运行状态转换为阻塞状态

&emsp;

### Thread 类的方法

&emsp;

```java
public static void sleep(long millis)
```
    作用：在指定的毫秒内让正在执行的线程休眠（暂停执行）
    参数为休眠时间，单位是毫秒

```java
package com.demo.sleep;

class MyThread implements Runnable{
    @Override
    public void run() {

        for (int i = 0; i <= 30; i++){
            System.out.println(Thread.currentThread().getName() + "执行第" + i + "次！"); // 调用 Thread 类的静态方法 Thread.currentThread()
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

public class SleepDemo {
    public static void main(String[] args) {
        MyThread mt = new MyThread();
        Thread t1 = new Thread(mt);
        t1.start();
        Thread t2 = new Thread(mt);
        t2.start();
    }
}
```

&emsp;

### join() 方法的使用

&emsp;

### Thread 类的方法

&emsp;

```java
public final void  join()
```
    作用：等待调用该方法的线程结束后才执行

&emsp;

```java
package com.demo.join;

class MyThread extends Thread{
    public void run(){
        for (int i = 1; i <= 10; i++) {

            System.out.println(getName()+"正在执行! " + i + "次");
        }
    }
}
    public class JoinDemo {
        public static void main(String[] args) {
            MyThread mt = new MyThread();
            mt.start();
            try {
                mt.join();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            for (int i = 1; i <=20 ; i++) {
                System.out.println("主线程运行第" + i + "次！");
            }
            System.out.println("主线程运行结束!");
        }
    }
```

&emsp;

```java
public final void join(long millis)
```
    作用：等待该线程最终的最长时间为 millis 毫秒

&emsp;

```java
package com.demo.join;

class MyThread extends Thread{
    public void run(){
        for (int i = 1; i <= 500; i++) {

            System.out.println(getName()+"正在执行! " + i + "次");
        }
    }
}
    public class JoinDemo {
        public static void main(String[] args) {
            MyThread mt = new MyThread();
            mt.start();
            try {
                mt.join(1);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            for (int i = 1; i <=20 ; i++) {
                System.out.println("主线程运行第" + i + "次！");
            }
            System.out.println("主线程运行结束!");
        }
    }
```

&emsp;

### 线程的优先级

&emsp;


    Java为线程类提供了10个优先级
    
    优先级可以用整数1-10表示（数字越大，表示的优先级越高），超过范围会抛出异常

    主线程默认优先级为5

    优先级常量表示线程优先级：

        - MAX_PRIORITY：线程的最高优先级10
        - MIN_PRIORITY：线程的最低优先级5
        - NORM_PRIORITY：线程的默认优先级5
        
&emsp;

### 优先级相关方法

&emsp;

<center>

|方法|说明|
|:-:|:-:|
|public int getPriority()|获取线程优先级的方法|
|public void setPriority(int newPriority)|设置线程优先级的方法|

</center>
