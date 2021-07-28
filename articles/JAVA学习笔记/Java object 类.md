# Java Object 类

&emsp;

> - Object类
> - 一个类没有使用 extends 关键字明确标识继承关系，则 默认继承 Object 类（包括数组）
> - Java中的每个类都可以使用 Object 中定义方法

&emsp;

> - toString() 测试：  
         1. 输出对对象名时，默认会直接调用类的toString  
         2.equals: 继承 Object 中的 toString 方法时，输出对象的字符串表示形式：   类型信息+@+地址信息  
         3.子类可以通过重写 toString 方法的形式，改变输出内容以及表现形式  

&emsp;

```java
package com.demo.animal;

public class Animal {
    private String name = "sb";    //  昵称
    private int month = 2;  //  月份
    String species = "海王"; //  品种
    public int temp = 15;
    private static int st1 = 22;
    public static int st2 = 23;

    public Animal(){


    }

    public Animal(String name, int month){
        this.name = name;
        this.month = month;

    }

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

    //  吃东西
    public void eat(){
        System.out.println( this.getName()+ "在吃东西！(我是父类的方法)");
    }

    public boolean equals(Object obj) {
        if (obj == null)
            return false;
        Animal temp = (Animal) obj;
        if (this.getName().equals(temp.getName()) && (this.getMonth() == temp.getMonth()))
            return true;
        else
            return false;
    }

    public boolean equals(Animal obj){
        if (obj == null)
            return false;
        if (this.getName().equals(obj.getName()) && (this.getMonth() == obj.getMonth()))
            return true;
        else
            return false;
    }

     // 重写 Object 类中的 toString 方法
      public String toString(){
        return "昵称：" + this.getName()+";年龄："+this.getMonth();
    }
}

```

&emsp;

```java

package com.demo.test;

import com.demo.animal.Animal;

public class TestThree {
    public static  void main(String[] args){
        Animal one = new Animal("kkbsd", 2);
        Animal two = new Animal("kkbsd", 2);

        /*
        * equals: 继承 Object 中的 equals 方法时，比较的是两个引用是否指向同一个对象
        * 子类可以通过重写equals方法的形式，改变比较的内容
        * */
        boolean flag = one.equals(two);
        System.out.println("one 和 two 的引用比较" + flag);
        System.out.println("one 和 two 的引用比较" + (one==two));
        System.out.println("==================================");
        String str1 = new String("hello");
        String str2 = new String("hello");
        flag = str1.equals(str2);
        System.out.println("one 和 two 的引用比较" + flag);
        System.out.println("one 和 two 的引用比较" + (str1==str2));
         System.out.println("==================================");
        /* toString() 测试：
            1. 输出对对象名时，默认会直接调用类的toString
         *  2.equals: 继承 Object 中的 toString 方法时，输出对象的字符串表示形式：   类型信息+@+地址信息
         *  3.子类可以通过重写 toString 方法的形式，改变输出内容以及表现形式
         * */
        System.out.println(one.toString());
        System.out.println(one);
        System.out.println("==================================");
        System.out.println(str1);
    }

}

```