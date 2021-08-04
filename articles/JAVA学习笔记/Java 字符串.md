# Java 字符串

&emsp;

### Java 字符串概述

&emsp;

    1. 如何创建String对象

    2. String对象的常用方法
    
    3. ==和equals方法的区别
    
    4. String的不可变性


&emsp;

### 创建 String 对象的方法

&emsp;

```java
//  方法一：创建一个 String 对象 Dev-Breezer，名为 stringValue1
String stringValue1 = "Dev-Breezer";
//  方法二：new 一个空 String 对象（字符串对象），名为 stringValue2
String stringValue2 = new String();
//  方法三：new 一个 String 对象 Dev-Breezer，名为 stringValue3
String stringValue3 = new String("Dev-Breezer");
```

&emsp;

### String 对象的常用方法

&emsp;

<center>

|方法|说明|
|:-:|:-:|
|int length()|返回当前字符串的长度|
|int indexOf(int ch)|查找 ch 字符在该字符串中第一次出现的位置|
|int indexOf(String str)|查找 str 子字符串在该字符串中第一次初出现的位置|
|int lastIndexOf(int ch)|查找 ch 字符在该字符串中最后一次出现的位置|
|int lastIndexOf(String str)|查找 str 子字符串中在该字符串中最后一次出现的位置| 
|String substring(int beginIndex)|获取从 beginIndex 位置开始到结束的子字符串| 
|String substring(int beginIndex, int endIndex)|获取从 beginIndex 位置开始到 endIndex 位置的子字符串|
|String trim()|返回去除左右空格的字符串|
|boolean equals(Object obj)|将该字符串与指定对象比较，返回 true 或者 false|
|String toLowerCase()|将字符串转换为小写|
|String toUpperCase()|将字符串转换为大写|
|String charAt(int index)|获取字符串中指定位置的字符|
|String[] split(String regex, int limit)|将字符串分割为子字符串，返回字符串数组|
|byte[] getBytes()|将该字符串转换为 byte 数组|
</center>

&emsp;

### 案例：

&emsp;

```java
package com.demo.string;

public class StringDemo1 {
    public static void main(String[] args) {
        /*
        * 了解并掌握 length()、substring()、charAt() 的使用
        * length() 方法：获取字符串长度
        * substring() 方法：获取从 beginIndex 位置开始到结束的子字符串
        * charAt() 方法：获取字符串中指定位置的字符
        */

        //  定义一个 Java 编程 基础
        String str = "Java 编程 基础";

        //  打印输出字符串长度
        System.out.println("字符串的长度：" + str.length());
        //  获取字符串中指定的字符
        System.out.println("字符串获取的字符：" + str.charAt(6));

        // 获取子字符串”编程 基础“
        System.out.println("获取子字符串”编程 基础“：" + str.substring(5));

        // 获取子字符串”编程“ 注意：顾头不顾尾
        System.out.println("获取子字符串”编程“：" + str.substring(5,7));

    }
}
```

&emsp;

```java
package com.demo.string;

public class StringDemo2 {
    public static void main(String[] args) {
        /*
         * 了解并掌握 indexOf()、lastIndexOf() 的使用
         * indexOf() 方法：查找字符（子字符串）在字符串中第一次出现的位置
         * lastIndexOf() 方法：查找子字符串在字符串中最后一次出现的位置（或者，从指定位置开始查找，子字符串最后一次出现的位置）
         */

        //  定义一个 ”JAVA编程基础，我喜欢java编程“
        String str = new String("JAVA编程基础，我喜欢java编程");

        //  查找字符 'A' 在字符串中第一次出现的位置
        System.out.println("字符A在字符串中第一次出现的位置：" + str.indexOf('A'));

        //  查找子字符串 ”编程“ 在字符串中第一次出现位置
        System.out.println("查找子字符串 \"编程\" 在字符串中第一次出现位置：" + str.indexOf("编程"));

        //  查找字符 'A' 在字符串中最后一次出现的位置
        System.out.println("查找字符 'A' 在字符串中最后一次出现的位置：" + str.lastIndexOf('A'));

        //  查找子字符串 ”编程“ 在字符串中最后一次出现位置
        System.out.println("查找子字符串 \"编程\" 在字符串中最后一次出现位置：" + str.lastIndexOf("编程"));

        //  在字符串 index 值为 8 的位置开始，查找子串 “编程” 第一次出现的位置
        System.out.println("查找子字符串 \"编程\" 在字符串中第一次出现位置：" + str.indexOf("编程",8));
    }
}
```

&emsp;

### 字符串 StringBuilder

&emsp;

### String 和 StringBuilder 的区别：

&emsp;

    String具有不可变性，StringBuilder 具有可变性

    建议：当频繁操作字符串时，使用StringBuilder


&emsp;

### StringBuilder 和 StringBuffer

&emsp;

    StringBuilder 和 StringBuffer 方法基本相似
    但是我们推荐使用 StringBuilder。

    官方解释：StringBuffer是线程安全的，StringBuilder则没有，所以性能略高。

    为什么不使用较为安全的StringBuffer，而是使用 StringBuilder 呢？
    大部分情况下我们在处理字符串时，都是单线程。而线程安全主要是指多线程的情况下。在单线程的情况下我们使用 StringBuilder，除非有特殊需求，我们才会使用 StringBuffer


&emsp;

```java
package com.demo.string;

public class StringBuilderDemo1 {
    public static void main(String[] args) {
        //  定义一个字符串 “你好”

        StringBuilder str = new StringBuilder("你好");

        //  在你好后面添加内容，将字符串变成 “你好，Java”

        str.append('，');
        str.append("Java");
        System.out.println("str = " + str);
        System.out.println("str = " + str.append(',').append("Java！"));

        /*  将字符串变成 ”你好，JAVA！“
          两种方式：
          1. 使用 delete 方法删除小写 Java，然后插入大写 JAVA
          2. 使用 replace 方法直接替换
          */

        System.out.println("替换后：" + str.delete(3, 7).insert(3, "JAVA"));
        System.out.println("替换后：" + str.replace(3, 7, "JAVA"));

        //  在字符串 ”你好，Java！“ 中取出你好并输出

        System.out.println(str.substring(0, 2));


    }
}
```

