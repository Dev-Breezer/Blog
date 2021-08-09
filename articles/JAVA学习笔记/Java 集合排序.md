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

#### **对宠物猫按名字升序**

&emsp;

```java
package com.demo.sort;

public class Cat {
    private String name;    //  名字
    private int month;  //  年龄
    private String species; //  品种

    //  构造方法

    public Cat(String name, int month, String species) {
        this.name = name;
        this.month = month;
        this.species = species;
    }

    // Getter 方法和 Setter 方法

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getMonth() {
        return month;
    }

    public void setMonth(int month) {
        this.month = month;
    }

    public String getSpecies() {
        return species;
    }

    public void setSpecies(String species) {
        this.species = species;
    }

    @Override
    public String toString() {
        return "{" +
                "姓名：" + name +
                ", 年龄：" + month +
                ", 品种：" + species +
                '}';
    }
}
```

&emsp;

```java
package com.demo.sort;

import java.util.Comparator;

public class NameComparator implements Comparator<Cat> {

    @Override
    public int compare(Cat o1, Cat o2) {

        //  按名字升序排列
        String name1 = o1.getName();
        String name2 = o2.getName();
        int n = name1.compareTo(name2);
        //  倒序排序： name2.compareTo(name1);
        return n;
    }
}
```

&emsp;

```java
package com.demo.sort;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CatTest {
    public static void main(String[] args) {

        //  按名字进行升序排序
        Cat tom = new Cat("tom", 5, "英国短毛猫");
        Cat fan = new Cat("fan", 2, "中华田园猫");
        Cat mao = new Cat("mao", 5, "中华田园猫");

        List<Cat> catList = new ArrayList<>();
        catList.add(tom);
        catList.add(fan);
        catList.add(mao);

        //  排序前
        System.out.println("按名字排序前：");
        for(Cat cat : catList){
            System.out.println(cat);
        }

        //  按名字进行升序排序
        Collections.sort(catList, new NameComparator());

        //  排序后
        System.out.println("按名字排序后：");
        for(Cat cat : catList){
            System.out.println(cat);
        }
    }
}
```

&emsp;

#### **年龄降序进行排列**

&emsp;

```java
package com.demo.sort;

import java.util.Comparator;

public class AgeComparator implements Comparator<Cat> {
    @Override
    public int compare(Cat o1, Cat o2) {

        //  按年龄降序排序
        int age1 = o1.getMonth();
        int age2 = o2.getMonth();
        return age2 - age1;
    }
}
```
&emsp;

```java
package com.demo.sort;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CatTest {
    public static void main(String[] args) {

        //  按名字进行升序排序
        Cat tom = new Cat("tom", 3, "英国短毛猫");
        Cat fan = new Cat("fan", 2, "中华田园猫");
        Cat mao = new Cat("mao", 5, "中华田园猫");

        List<Cat> catList = new ArrayList<>();
        catList.add(tom);
        catList.add(fan);
        catList.add(mao);

        //  排序前
        System.out.println("排序前：");
        for(Cat cat : catList){
            System.out.println(cat);
        }

        //  按名字进行升序排序
        Collections.sort(catList, new NameComparator());

        //  排序后
        System.out.println("按名字升序排序后：");
        for(Cat cat : catList){
            System.out.println(cat);
        }

        //  按年龄进行降序排序
        Collections.sort(catList, new AgeComparator());

        //  排序后
        System.out.println("按年龄降序排序后：");
        for(Cat cat : catList){
            System.out.println(cat);
        }
    }
}
```

&emsp;

### **Comparable 接口**

&emsp;

    此接口强行对实现它的每个类的对象进行整体排序。
    这种排序被称为类的自然排序，类的compareTo方法被称为它的自然比较方法。
    对于集合，通过调用Collections.sort方法进行排序。对于数组，通过调用Arrays.sort方法进行排序。
    
    int compareTo(T o)方法

    该对象小于、等于或大于指定对象，则分别返回负整数、零或正整数。

&emsp;

#### **对商品价格降序排列**

&emsp;

```java
package com.demo.sort;

public class Goods implements Comparable<Goods>{

    private String id;//商品编号
    private String name;//商品名称
    private double price;//商品价格
    //构造方法
    public Goods(String id,String name,double price){
        this.id=id;
        this.name=name;
        this.price=price;
    }

    //getter和setter方法
    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }
    public String toString(){
        return "商品编号："+id+",商品名称："+name+"，商品价格："+price;
    }

    @Override
    public int compareTo(Goods o) {

        //  对商品价格进行降序排序
        //  1.取出商品价格
        double price1 = this.getPrice();
        double price2 = o.getPrice();
        int n =  new Double(price2 - price1).intValue();
        return n;
    }
}
```

&emsp;

```java
package com.demo.sort;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class GoodsTest {
    public static void main(String[] args) {
        Goods g1 = new Goods("s000001", "手机", 2000);
        Goods g2 = new Goods("s000002", "冰箱", 5000);
        Goods g3 = new Goods("s000003", "电视机", 3000);
        List<Goods> goodsList = new ArrayList<>();
        goodsList.add(g1);
        goodsList.add(g2);
        goodsList.add(g3);

        //  排序前
        System.out.println("排序前：");
        for(Goods goods : goodsList){
            System.out.println(goods);
        }
        Collections.sort(goodsList);

        //  排序后
        System.out.println("排序后：");
        for(Goods goods : goodsList){
            System.out.println(goods);
        }
    }
}
```

&emsp;

### **Comparator 和 Comparable 的区别**

&emsp;

|Comparator|Comparable|
|:-:|:-:|
|位于 java.util 包|位于 java.lang 包|
|在要比较的类的外部实现该接口|在要比较的类上实现该接口|
|调用sort方法时，要指定Comparator的实现类|调用sort方法时，只需指定集合名即可|

&emsp;

#### Comparator 接口

    第一步实现要比较的类  
    第二步实现Comparator接口第三步测试  

#### Comparable 接口

    第一步∶定义要比较的类，并实现Comparable接口
    第二步:测试
