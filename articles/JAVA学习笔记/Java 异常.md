# Java 异常

&emsp;

**Throwable** 是 Java 异常中得根类，其下有两个子类 Error 和 Exception 

&emsp;

> - Error是程序无法处理的错误，表示运行应用程序中较严重问题。此类错误大多数情况下与开发者编写的代码执行的操作没有关系。而表示代码运行中 JVM 出现的一系列问题。  
> - **常见错误：** 虚拟机错误（VirtualMachineError）、内存溢出错误（OutOfMemoryError）、线程死锁（ThreadDeath）

&emsp;

> - Exception是程序本身可以处理的异常，通常我们提到的异常处理是指对于 Exception 对于子类的处理，Exception 异常包括 检查异常（Checked Exception）、非检查异常（Unchecked Exception）
> - **非检查异常（Unchecked Exception）** 是指编译器不要求强制处理的异常  
> - 包含：RuntimeException（运行时异常）以及相关子类（比如：空指针异常   NullPointerException、数组下标越界异常 ArrayIndexOutOfBoundsException、算数异常 ArithmeticException、类型转换异常 ClassCastException）

&emsp;

> - **检查异常（Checked Exception）** 编译器要求必须处理的异常，在 Java 当中，除了 RuntimeException 异常及其子类异常，其它 Exception 类型的子类都是 CheckedException。（比如：IO 异常 IOException，SQL 异常 SQLException）

&emsp;

### 异常处理分类：

&emsp;

> - 在Java应用程序中，异常处理机制为：**抛出异常**、**捕获异常**
> - 对于运行时异常、错误或可查异常，Java技术所要求的异常处理方式有所不同。
> - Java规定: 对于检查异常必须捕捉、或者声明抛出（不能无视它），但是允许忽略不可查的 RuntimeException（包含其子类）和 Error（包含其子类）

&emsp;

#### 对于抛出异常和捕获异常，在 Java 当中可以通过5个关键字类实现：**try**、**catch**、**finally**、**throw**、**throws** 

&emsp;

### 捕获异常操作

&emsp;

> try     捕获异常 
> catch     处理针对 try 捕获的异常  
> finally       无论是否发生异常，代码总能执行

&emsp;

try 块后可接零个或多个 catch 块，如果没有 catch 块，则必须跟一个 finally 块 

&emsp;

```java
public void method(){
    try {
        //  代码段1
        //  产生异常的代码段2
        }
        catch(异常类型ex)
        {
        //  对异常进行处理的代码段3
        }
        finally{
    //  代码段4
    }
}


```

&emsp;

### 声明异常操作

&emsp;

> throws    声明可能要抛出的异常

&emsp;

### 抛出异常操作

&emsp;

> throw     手动抛出异常

&emsp;

### **使用 try-catch 结构处理异常**

&emsp;

```java
package com.demo.test;

import java.util.Scanner;

public class TryDemoOne {
    public static void main(String[] args) {
        //  要求：定义两个整数，输出两数之商
        /*
                int one = 12;
                int two = 2;

                System.out.println("one 和 two的商是：" + (one/two));
        */

        //  要求：定义两个整数，接收用户的键盘输入，输出两数之商
        Scanner input = new Scanner(System.in);
        System.out.println("===========运算开始==========");
        try {
            System.out.print("输入第一个整数：");
            int one = input.nextInt();
            System.out.print("输入第二个整数：");
            int two = input.nextInt();
            System.out.println("one 和 two的商是：" + (one / two));
        }
        catch (Exception e){
            System.out.println("程序出错！");
            e.printStackTrace();
        }
        //  无论 try-catch 语句块中是否会被执行，finally中的语句块一定会被执行
        finally {
            System.out.println("===========运算结束==========");
        }

    }
}
```

&emsp;

### **使用多重 catch 结构处理异常**

&emsp;

```java
package com.demo.test;

import java.util.InputMismatchException;
import java.util.Scanner;

public class TryDemoOne {
    public static void main(String[] args) {
        //  要求：定义两个整数，输出两数之商
        /*
                int one = 12;
                int two = 2;

                System.out.println("one 和 two的商是：" + (one/two));
        */

        //  要求：定义两个整数，接收用户的键盘输入，输出两数之商
        Scanner input = new Scanner(System.in);
        System.out.println("===========运算开始==========");
        try {
            System.out.print("输入第一个整数：");
            int one = input.nextInt();
            System.out.print("输入第二个整数：");
            int two = input.nextInt();
            System.out.println("one 和 two的商是：" + (one / two));
        }
        catch (ArithmeticException e){
            System.out.println("除数不允许为0");
            e.printStackTrace();
        }
        catch (InputMismatchException e){
            System.out.println("请输入整数");
            e.printStackTrace();
        }
        /*推荐在异常处理语句后写一个catch(Exception e)，以保证所有 Exception 都能被捕捉*/
        catch (Exception e){
            System.out.println("程序出错！");
            e.printStackTrace();
        }
        //  无论 try-catch 语句块中是否会被执行，finally中的语句块一定会被执行
        finally {
            System.out.println("===========运算结束==========");
        }

    }
}
```

&emsp;

### **终止 finally 执行的方法**

&emsp;

```java
/*
终止当前运行的Java虚拟机。 该参数作为状态代码; 按照惯例，非零状态码表示异常终止。
此方法调用exit类方法Runtime 。 此方法从不正常返回。
此方法的类 System 无法被实例化（即：不能被 new ）
*/
System.exit();  //终止当前运行的 Java 虚拟机

```

&emsp;

```java
package com.demo.test;

import java.util.InputMismatchException;
import java.util.Scanner;

public class TryDemoOne {
    public static void main(String[] args) {
        //  要求：定义两个整数，输出两数之商
        /*
                int one = 12;
                int two = 2;

                System.out.println("one 和 two的商是：" + (one/two));
        */

        //  要求：定义两个整数，接收用户的键盘输入，输出两数之商
        Scanner input = new Scanner(System.in);
        System.out.println("===========运算开始==========");
        try {
            System.out.print("输入第一个整数：");
            int one = input.nextInt();
            System.out.print("输入第二个整数：");
            int two = input.nextInt();
            System.out.println("one 和 two的商是：" + (one / two));
        }
        catch (ArithmeticException e){
            System.exit(1); //  终止程序运行
            System.out.println("除数不允许为0");
            e.printStackTrace();
        }
        catch (InputMismatchException e){
            System.out.println("请输入整数");
            e.printStackTrace();
        }
        /*推荐在异常处理语句后写一个catch(Exception e)，以保证所有 Exception 都能被捕捉*/
        catch (Exception e){
            System.out.println("程序出错！");
            e.printStackTrace();
        }
        //  无论 try-catch 语句块中是否会被执行，finally中的语句块一定会被执行
        finally {
            System.out.println("===========运算结束==========");
        }

    }
}
```

&emsp;

### **return 关键字在异常处理中的作用**

&emsp;

> - 由于 finally 的关系，在何种情况下，始终只执行 finally 下的 return 语句

&emsp;

```java
package com.demo.test;

import java.util.Scanner;

public class TryDemoTwo {
    public static void main(String[] args) {
        int result = test();
        System.out.println("one 和 two的商是：" + result);
    }

    public static int test() {
        Scanner input = new Scanner(System.in);
        System.out.println("===========运算开始==========");
        try {
            System.out.print("输入第一个整数：");
            int one = input.nextInt();
            System.out.print("输入第二个整数：");
            int two = input.nextInt();
            return one/two;
        } catch (ArithmeticException e) {
            System.out.println("除数不允许为0");
            return 0;
        }
        //  无论 try-catch 语句块中是否会被执行，finally中的语句块一定会被执行
        finally {
            System.out.println("===========运算结束==========");
            return -100000;
        }
    }
}
```

&emsp;

### **使用 throws 声明异常类型**

&emsp;

> - 可以通过throws声明将要抛出何种类型的异常，通过throw将产生的异常抛出。
> - 如果一个方法可能会出现异常，但没有能力处理这种异常，可以在方法声明处用throws子句来声明抛出异常。

&emsp;

- ### throws语句用在方法定义时声明该方法要抛出的异常类型。


&emsp;

```java
public void method() throws Exception1,Exception2,..ExceptionN {
//  可能产生异常的代码
)

```

&emsp;

- ###  当方法抛出异常列表中的异常时，方法将不对这些类型及其子类类型的异常作处理，而抛向调用该方法的方法，由他去处理。

&emsp;

> - 通过 throws 抛出异常时，针对可能出现多种异常情况，解决方案：  
    1. throws 后面接多个异常类型，中间用逗号分隔  
    2. throws 后面接 Exception  
    

&emsp;

```java
package com.demo.test;

import java.util.InputMismatchException;
import java.util.Scanner;

public class TryDemoThree {
    public static void main(String[] args) {
        try {

            int result = test();
            System.out.println("one 和 two的商是：" + result);
        } catch(ArithmeticException e){
            System.out.println("除数不允许为零");
            e.printStackTrace();
        } catch (InputMismatchException e){
            System.out.println("请输入整数");
            e.printStackTrace();
        }
    
        try {
            int result = test();
            System.out.println("one 和 two的商是：" + result);
        }catch(ArithmeticException e){
            System.out.println("除数不允许为零");
            e.printStackTrace();
        } catch (InputMismatchException e){
            System.out.println("请输入整数");
            e.printStackTrace();
        }catch (Exception e){

        }

    }

    /*通过 throws 抛出异常时，针对可能出现多种异常情况，解决方案：
    * 1. throws 后面接多个异常类型，中间用逗号分隔
    * 2. throws 后面接 Exception
    * */

    /**
     * 测试接收数据相除结果的方法
     * @return 接收两个整数相除的商
     * @throws ArithmeticException
     * @throws InputMismatchException
     */
    public static int test() throws ArithmeticException, InputMismatchException {
        Scanner input = new Scanner(System.in);
        System.out.println("===========运算开始==========");
        System.out.print("输入第一个整数：");
        int one = input.nextInt();
        System.out.print("输入第二个整数：");
        int two = input.nextInt();
        System.out.println("===========运算结束==========");
        return one / two;

    }


    public static int test() throws Exception{
        Scanner input = new Scanner(System.in);
        System.out.println("===========运算开始==========");
        System.out.print("输入第一个整数：");
        int one = input.nextInt();
        System.out.print("输入第二个整数：");
        int two = input.nextInt();
        System.out.println("===========运算结束==========");
        return one / two;

    }
}
```

&emsp;

### 使用 throw 抛出异常对象
###  throw 抛出的只能够是可抛出类 Throwable 或者其子类的实例对象

&emsp;

### 例如： 

&emsp;

```java
throw new IOException();
```
&emsp;
### 错误的示例： 

&emsp;

```java
throw new String();
```

&emsp;

对于异常对象的处理：  

    1、规避可能出现的风险  
    2、完成一些程序的逻辑

&emsp;

### throw 抛出异常对象的处理方案
    方案1：通过 try-catch 包含 throw 语句--自抛异常出自处理
    方案2：通过 throws 在方法声明出抛出异常类型-- 谁调谁处理--调用者可以自己处理，也可以继续上抛
    此时可以抛出与 throw对象相同的类型或者其父类，绝不能是子类

&emsp;

```java
package com.demo.test;

import java.util.Scanner;

public class TryDemoFour {
    public static void main(String[] args) {
        try {
            testAge();
        } catch (Throwable e) {
            e.printStackTrace();
        }
    }

    //  描述酒店的入住规则：限定年龄：18以下，80岁以上的住客必须有亲友陪同

   /* throw 抛出异常对象的处理方案
   *  方案1：通过 try-catch 包含 throw 语句--自抛异常出自处理
   *  方案2：通过 throws 在方法声明出抛出异常类型-- 谁调谁处理--调用者可以自己处理，也可以继续上抛
   *  此时可以抛出与 throw对象相同的类型或者其父类，绝不能是子类
   * */

    public static void testAge(){
            try {
                System.out.print("请输入年龄：");
                Scanner input = new Scanner(System.in);
                int age = input.nextInt();
                if(age < 18 || age > 80){
                    throw new Exception("18以下，80岁以上的住客必须有亲友陪同");
                }else {
                    System.out.println("欢迎入住本酒店！");
                }
            } catch (Exception e) {
                e.printStackTrace();
            }
    }

    public static void testAge() throws Throwable {
        System.out.print("请输入年龄：");
        Scanner input = new Scanner(System.in);
        int age = input.nextInt();
            if(age < 18 || age > 80){
                throw new Exception("18以下，80岁以上的住客必须有亲友陪同");
            }else {
                System.out.println("欢迎入住本酒店！");
            }
    }

}
```

&emsp;
### 自定义异常类

&emsp;

    -使用Java内置的异常类可以描述在编程时出现的大部分异常情况。
    -也可以通过自定义异常描述特定业务产生的异常类型。-所谓自定义异常，就是定义一个类，去继承Throwable类或者它的子类。

```java
package com.demo.test;

import java.util.Scanner;

public class TryDemoFour {
    public static void main(String[] args) {
        try {
            testAge();
        } catch (HotelAgeException e) {
            System.out.println(e.getMessage());
            System.out.println("酒店前台工作人员不允许办理入住登记");
        } catch (Exception e){
            e.printStackTrace();
        }
    }

    //  描述酒店的入住规则：限定年龄：18以下，80岁以上的住客必须有亲友陪同

    public static void testAge() throws HotelAgeException {
        System.out.print("请输入年龄：");
        Scanner input = new Scanner(System.in);
        int age = input.nextInt();
            if(age < 18 || age > 80){
                throw new HotelAgeException();
            }else {
                System.out.println("欢迎入住本酒店！");
            }
    }

}
```

&emsp;

```java
package com.demo.test;

public class HotelAgeException extends Exception{

    //  无参构造方法
    public HotelAgeException(){
        super("18以下，80岁以上的住客必须有亲友陪同");
    }
}
```

&emsp;

### 异常链简介

&emsp;

    有时候我们会捕获一个异常后在抛出另一个异常
    顾名思义就是:将异常发生的原因一个传一个串起来，即把底层的异常信息传给上层，这样逐层抛出,而形成的一种一种链条。


&emsp;

```java
package com.demo.test;

public class TryDemoFive {
    public static void main(String[] args) {

        try {
            testThree();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static void testOne() throws HotelAgeException{
        throw new HotelAgeException();
    }

    public static void testTwo() throws Exception{
        try {
            testOne();

        }catch (HotelAgeException e){
            throw new Exception("我是新产生的异常1", e);

        }
    }

    public static void testThree() throws Exception {
        try {
            testTwo();

        }catch (Exception e){
            Exception e1 = new Exception("我是新产生的异常  2");
            e.initCause(e);
            throw e1;
            //  throw new Exception("我是新产生的异常2", e);

        }
    }
}
```

