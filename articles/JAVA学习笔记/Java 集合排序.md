# Java 集合排序

&emsp;

    集合中的基本数据类型排序
    集合中的字符串排序
    Comparator接口Comparable接口

&emsp;


### 集合排序

    使用Collections类的sort()方法
        sort(List<T> list)
    
    根据元素的自然顺序对指定列表按升序进行排序。

&emsp;

### 案例

&emsp;

#### **对存放在List中的整型数据进行排序**

&emsp;

```java
package com.demo.sort;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class IntSort {
    public static void main(String[] args) {

        //  对存储在 List 中的整型数据进行排序
        List <Integer> list = new ArrayList<>();
        list.add(5);
        list.add(9);
        list.add(3);
        list.add(1);

        //  输出排序前的数据
        System.out.println("排序前：");
        for (int n : list) {
            System.out.print(n + ", ");
        }

        //  对 list 中的数据进行排序
        Collections.sort(list);
        //  输出排序后的数据
        System.out.println("\n排序后：");
        for (int n : list) {
            System.out.print(n + ", ");
        }

    }
}
```

&emsp;

#### **对存放在List中的字符串进行排序**

&emsp;

```java
package com.demo.sort;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class StringSort {
    public static void main(String[] args) {

        //  对存放在 List 中的字符串进行排序
        List<String> list = new ArrayList<>();
        list.add("orange");
        list.add("blue");
        list.add("yellow");
        list.add("gray");

        //  输出排序前的数据
        System.out.println("排序前：");
        for (String s: list) {
            System.out.print(s + "  ");
        }

        //  输出排序后的数据
        Collections.sort(list);
        System.out.println("\n排序后：");
        for (String s: list) {
            System.out.print(s + "  ");
        }
    }
}
```

&emsp;

### **Comparator 接口介绍**

&emsp;

    强行对某个对象进行整体排序的比较函数（比较器）
    可以将Comparator传递给sort方法（如Collections.sort或Arrays.sort )

    int compare(T o1,T o2)比较用来排序的两个参数
    如果o1<o2，返回负整数
    如果o1==o2，返回0-如果o1>o2，返回正整数

&emsp;

### 案例

&emsp;

#### **例:对宠物猫分别按名字升序、年龄降序进行排列**

&emsp;

