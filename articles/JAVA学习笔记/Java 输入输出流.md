# Java 输入输出流

&emsp;

### 主要内容

&emsp;


    File类的使用
    字节流
    字符流
    对象的序列化与反序列化

&emsp;

### File 类

&emsp;

    文件是相关记录或放在一起的数据的集合 
    在 Java 中，使用 java.io.File 类对文件进行操作


&emsp;

### File 类的常用方法

&emsp;

```java
package com.demo.file;

import java.io.File;
import java.io.IOException;

public class FileDemoOne {
    public static void main(String[] args) {

        // 第一种： 创建 File 对象
        //  File file1 = new File("E:\\Demo\\io\\score.txt");

        //  第二种：创建 File 对象
        //  File file1 = new File("E:\\Demo","io\\score.txt");

        //  第三种：创建 File 对象
        File file = new File("E:\\Demo");
        File file1 = new File(file, "io\\score.txt");
        File file3 = new File(file, "io\\score");


        //  判断是文件还是目录
        System.out.println("是否是目录：" + file1.isDirectory());    //  判断是否是目录，返回值：boolean
        System.out.println("是否是文件：" + file1.isFile());     //  判断是否是文件，返回值：boolean

        //  创建目录
        File file2 = new File("E:\\Demo\\set", "HashSet");
        if(!file2.exists()){
            file2.mkdirs();
        }

        //  创建文件
        if (!file3.exists()){
            try {
                file3.createNewFile();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

&emsp;

### 绝对路径与相对路径

&emsp;

    绝对路径：是从盘符开始的路径
    相对路径：是从前路径开始的路径

&emsp;

### 字节流

&emsp;

    字节输入流InputStream 
        - FileInputStream 文件输入流
        - PipedInputStream 管道输入流
        - FilterInputStream 过滤器输入流
            - PushbackInputStream 回压输入流
            - BufferedInputStream 缓冲输入流
            - DataInputStream 数据输入流
        - ObjectInputStream 对象输入流
        - SequenceInputStream 顺序输入流
        - ByteArrayInputStream 字节数组输入流
        - StringBufferInputStream 缓冲字符输入流

    字节输出流OutputStream
        - FileOutputStream 文件输出流
        - PipedOutputStream 管道输出流
        - FilterOutputStream 过滤器输出流
            - PrintStream 格式化输出流
            - BufferedOutputStream 缓冲输出流
            - DataOutputStream 数据输出流
        - ObjectOutputStream 对象输出流
        - ByteArrayOutputStream 字节数组输出流

&emsp;

### FileInputStream 文件输入流

&emsp;

#### FileInputStream 常用方法

&emsp;

> 如果返回值为-1，则表示已经达到文件末尾!

&emsp;

<center>

|方法|描述|
|:-:|:-:|
|public int read()|从输入流中读取一个数据字节|
|public int read(byte[] b)|从输入流中将最多 b.length 个字节的数据读入一个 byte 数组中|
|public int read(byte[] b, int off, int len)|将指定 byte 数组中从偏移量 off 开始的 len 个字节将此文件输入流|
|public void close()|关闭此文件输入流并释放与次流有关的所有系统资源|

</center>

&emsp;

```java
package com.demo.file;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class FileInputDemoTwo {
    public static void main(String[] args) {

        //  创建 FileInputStream 对象
        try {
            FileInputStream fis = new FileInputStream("helloworld.txt");

            // TODO：  read() 方法的使用

            //  第一种读取文件的方式
            //  int k = fis.read();
            //  while(k != -1){
            //      System.out.print((char)k);
            //      k = fis.read();
            //   }
            //   fis.read();

            // 第二种读取文件的方式
            int n=0;
            while((n = fis.read()) != -1){
                System.out.print((char)n);
            }
            fis.close();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e){
            e.printStackTrace();
        }
    }
}
```

&emsp;

```java
package com.demo.file;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class FileInputDemoThree {
    public static void main(String[] args) {
        //  创建 FileInputStream 对象
        try{
            FileInputStream fis = new FileInputStream("helloworld.txt");
            byte[] b = new byte[18];

            //  read 两种带参的使用方法
            //  fis.read(b);
            fis.read(b,0,5);
            System.out.println(new String (b));

            fis.close();    // 关闭
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e){
            e.printStackTrace();
        }
    }
}
```

&emsp;

### FileOutputStream 文件输出流

&emsp;

#### FileOutputStream 常用方法

&emsp;

> 如果返回值为-1，则表示已经达到文件末尾!

&emsp;

<center>

|方法|描述|
|:-:|:-:|
|public void write(int b)|将指定字节写入此文件输出流|
|public void write(byte[] b)|将 b.length 个字节从指定 byte 数组写入此文件输出流中|
|public void write(byte[] b, int off, int len)|将指定 byte 数组中从偏移量 off 开始的 len 个字节写入此文件输出流|
|public void close|关闭此文件输出流并释放与此流有关的所有系统资源|


</center>

&emsp;

```java
package com.demo.file;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

public class FileOutputDemoOne {
    public static void main(String[] args) {

        //  创建 FileOutputStream 对象
        try {
            FileOutputStream fos = new FileOutputStream("helloworld.txt", true);
            FileInputStream fis = new FileInputStream("helloworld.txt");
            fos.write(50);
            fos.write('a');
            System.out.println(fis.read());
            System.out.println((char)fis.read());
            fos.close();
            fis.close();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e){
            e.printStackTrace();
        }
    }
}
```

&emsp;

```java
package com.demo.file;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

public class FileOutputDemoTwo {
    public static void main(String[] args) {

        //  TODO: 代码没有运行错误，文件拷贝后为0kB且无法显示
        //  文件拷贝
        try {
            FileInputStream fis = new FileInputStream("cat.gif");
            FileOutputStream fos = new FileOutputStream("CatCopy.gif");
            int n = 0;
            byte[] b = new byte[1024];
            while(fis.read(b) != -1){
                fos.write(b,0, n);
            }
            fis.close();
            fos.close();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e){
            e.printStackTrace();
        }
    }
}
```

&emsp;

### 缓冲流

&emsp;

    之前的读写方式都是从硬盘当中读取数据，这种读取方式的缺点也很明显：读取速度慢，读取速度远不及从内存中读取数据，使用缓冲输入/输出可以提高读写数据的速度

    缓冲输入流 BufferedInputStream

        - 缓冲输入流不能直接读取系统中数据，需要与文件输入流结合
        
            源文件 —读取—> 缓冲输入流 —存入—> byte[] 数组

    缓冲输出流 BufferedOutputstream
        
        - 缓冲输出流不能直接写入数据，需要与文件输出流结合
        
            写入数据 —读取—> 缓冲输出流 —存入—> 源文件

&emsp;

```java
package com.demo.file;

import java.io.*;

public class BufferedDemo {
    public static void main(String[] args) {

        //  创建输出流和缓冲输出流
        try {
            FileOutputStream fos = new FileOutputStream("helloworld.txt");
            BufferedOutputStream bos = new BufferedOutputStream(fos);
            FileInputStream fis = new FileInputStream("helloworld.txt");
            BufferedInputStream bis = new BufferedInputStream(fis);
            bos.write(50);
            bos.write('a');
            bos.flush();    //  强制清空缓冲区


            System.out.println(bis.read());
            System.out.println((char)bis.read());

            fos.close();
            bos.close();
            fis.close();
            bis.close();

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e){
            e.printStackTrace();
        }
    }
}
```