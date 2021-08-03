# Java 包装类

&emsp;

### 包装类与基本数据类型

&emsp;

    基本数据类型不具有对象特征 即：没有属性、方法；无法对象化交互。
    通过包装类，可以让基本数据类型获得对象的相应特征；即：拥有属性、方法，可以对象化交互。

&emsp;

<center>  

|基本数据类型|对应的包装类|  
|:-:|:-:|  
|byte|Byte|
|short|Short|
|int|Integer|
|long|Long|
|float|Float|
|double|Double|
|char|Character|
|boolean|Boolean|
</center>

&emsp;

### **包装类常用方法**

&emsp;

    参考 Java API -- java.lang 包

&emsp;

### **基本数据类型和包装类之间的转换**

&emsp;

    装箱：在 Java 当中，装箱就是把基本数据类型的值转换成对应包装类的对象。
    拆箱：相对于装箱而言的逆操作；即：包装类的对象转换成基本数据类型对应的值
    
    装箱和拆箱的操作方式分为自动和手动

 
 &emsp;

```java
package wrap;

public class WrapTestOne {
    public static void main(String[] args) {
        //  装箱：把基本数据类型转换成包装类

        // 1. 自动装箱
        int t1 = 2;
        Integer t2 = t1;
        
        // 2. 手动装箱
        int t3 = new Integer(t1);

        //  测试
        System.out.println("int 类型变量t1 = " + t1);
        System.out.println("Integer 类型对象t2 = " + t2);
        System.out.println("Integer 类型对象t3 = " + t3);

        System.out.println("****************************************************");


        //  拆箱：把包装类转换成基本数据类型

        // 1. 自动拆箱
        int t4 = t2;

        // 2. 手动拆箱
        int t5 = t2.intValue();


        //  测试

        System.out.println("Integer 类型对象t2 = " + t2);
        System.out.println("自动拆箱后，int 类型变量t4 = " + t4);
        System.out.println("手动拆箱后，int 类型变量t5 = " + t5);
        double t6 = t2.doubleValue();
        System.out.println("手动拆箱后，double 类型变量t6 = " + t6);
    }
}
```

&emsp;


### **基本数据类型和字符串之间的转换**

&emsp;

```java
package wrap;

public class WrapTestTwo {
    public static void main(String[] args) {

        //  基本数据类型转换为字符串

        int t1 = 2;
        String t2 = Integer.toString(t1);

        //  测试
        System.out.println("int 类型转换为 String 类型对象 t2 = " + t2);
        System.out.println("*********************************");
        //  字符串转基本数据类型


        // 1. 包装类的 parseInt() 方法
        int t3 = Integer.parseInt(t2);

        // 2. 包装类的 valueOf() 方法，先将字符串装换成包装类对应对象，再通过自动拆箱完成基本数据类型的转换
        int t4 = Integer.valueOf(t2);

        //  测试

        System.out.println("String 类型转换为 int 类型变量 t3 = " + t3);
        System.out.println("String 类型转换为 int 类型变量 t4 = " + t4);
    }
}
```

&emsp;

### 扩展知识

&emsp;

    - 包装类对象的初始值
    - 包装类兑现间的比较

```java
package wrap;

public class WrapperTest {
    public static void main(String[] args) {

            Integer one=new Integer(100);
            Integer two=new Integer(100);
            System.out.println("one==two的结果︰"+(one==two));//1

            Integer three=100;  // 自动装箱
            //  Integer four = Integer.valueOf(100);
            System.out.println("three==100的结果: "+(three==100)); //2

            //  Integer four=100;
            Integer four = Integer.valueOf(100);
            System.out.println("three==four的结果:"+(three==four)); //3

            Integer five=200;
            System.out.println("five==200的结果:"+(five==200));//4

            Integer six=200;
            System.out.println("five==six的结果∶"+(five==six));//5

            Double d1 = Double.valueOf(100);
            System. out.println("d1==100的结果:"+(d1==100));Double d2=Double.valueOf(100;
            System.out.println("d1==d2的结果:"+(d1==d2));

    }
}


```


&emsp;

### 对象常量池（缓存区、对象池）

    对象 大于等于-128且小于等于127,如果有，直接产生，如果对象超出这个范围或者没有，直接隐式的实例化 Integer

&emsp;

### 注意：

&emsp;

    八种基本数据类型对应的包装类重，除了 Float、Double 其余的数据类型都可以应用于对象常量池这个概念