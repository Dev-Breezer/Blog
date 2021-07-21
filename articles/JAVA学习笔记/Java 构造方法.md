# Java 构造方法

<br>
<br>

### **构造方法——无参构造方法**

<br>

> + 别名：构造函数 或者 构造器
> + 面向对象当中重要的概念
> + **作用：经常性的使用构造方法来完成对象初始化的相关设置**
> + **构造方法不能直接被对象调用，需要搭配 new 关键字使用**
> + **构造方法与类同名且没有返回值**
> + **构造方法只能在对象实例化时调用**

<br>

#### 构造方法语法格式

<br>

> + 如果一个类的类名叫 Cat，那个构造方法名也 **_必须_** 是 Cat
```java

public 构造方法名(){
    //  初始化代码
}

```

<br>

### **构造方法的特点**

<br>

> + 当没有指定构造方法时，系统会自动添加无参的构造方法
> + 当有指定构造方法，无论z指定是有参、无参的构造方法，都不会自动添加无参的构造方法
> + 一个类中可以有多个构造方法

```java

package com.demo.animal;

/**
 * 宠物猫类
 * @author Dev-Breezer
 */

public class Cat {
    //  成员属性：昵称、年龄、体重、品种
    String name;    //  昵称  String 类型默认值：null
    int month;      //  年龄  int 类型默认值：0
    double weight;  //  体重  double 类型默认值 0.0
    String species; //  品种

    //  无参构造方法
    public Cat(){
        System.out.println("我是无参构造方法");
    }

    public Cat(String name){
        System.out.print("我是带参构造方法:");
        System.out.println(name);
    }

    //  成员方法：跑动、吃
    //  跑动的方法
    public void run(){
        System.out.println("小猫在跑");
    }

    //  方法重载
    public void run(String name){
        System.out.println( name + "快跑");
    }

    //  吃东西的方法
    public void eat(){
        System.out.println("小猫吃鱼干");
    }

}

```

<br>

```java
package com.demo.animal;

public class CatTest {
    public static void main(String[] args){

         // 对象实例化

          Cat one = new Cat();
          Cat two = new Cat("Tom");
          one.run();


    }
}
```

<br>

### **构造方法——带参构造方法**

<br>

```java
package com.demo.animal;

/**
 * 宠物猫类
 * @author Dev-Breezer
 */

public class Cat {
    //  成员属性：昵称、年龄、体重、品种
    String name;    //  昵称  String 类型默认值：null
    int month;      //  年龄  int 类型默认值：0
    double weight;  //  体重  double 类型默认值 0.0
    String species; //  品种

    //  无参构造方法
    public Cat(){
        System.out.println("我是无参构造方法");
    }

    public Cat(String name){
        System.out.print("我是带参构造方法:");
        System.out.println(name);
    }

    public Cat(String newName, int newMonth, double newWeight, String newSpecies){
        name = newName;
        month = newMonth;
        weight = newWeight;
        species = newSpecies;
    }

    //  成员方法：跑动、吃
    //  跑动的方法
    public void run(){
        System.out.println("小猫在跑");
    }

    //  方法重载
    public void run(String name){
        System.out.println( name + "快跑");
    }

    //  吃东西的方法
    public void eat(){
        System.out.println("小猫吃鱼干");
    }

}
```

<br>

```java
package com.demo.animal;

/**
 *
 */

public class CatTest {
    public static void main(String[] args){

         // 对象实例化

          Cat one = new Cat("tom", 2, 1000, "英国短毛猫");
          Cat two = new Cat("Tom");
          one.run();
          System.out.println(one.name);
          System.out.println(one.month);
          System.out.println(one.weight);
          System.out.println(one.species);

    }
}
```

<br>

### this 关键字

<br>

> +  作用：指向当前对象

<br>

```java
package com.demo.animal;

/**
 * 宠物猫类
 * @author Dev-Breezer
 */

public class Cat {
    //  成员属性：昵称、年龄、体重、品种
    String name;    //  昵称  String 类型默认值：null
    int month;      //  年龄  int 类型默认值：0
    double weight;  //  体重  double 类型默认值 0.0
    String species; //  品种

    //  无参构造方法
    public Cat(){
        System.out.println("我是无参构造方法");
    }

    public Cat(String name){
        System.out.print("我是带参构造方法:");
        System.out.println(name);
    }

    public Cat(String name, int month, double weight, String species){
        this.name = name;
        this.month = month;
        this.weight = weight;
        this.species =species;
    }

    //  成员方法：跑动、吃
    //  跑动的方法
    public void run(){
        this.eat();
        System.out.println("小猫在跑");
    }

    //  方法重载
    public void run(String name){
        System.out.println( name + "快跑");
    }

    //  吃东西的方法
    public void eat(){
        System.out.println("小猫吃鱼干");
    }

}
```

<br>

```java
package com.demo.animal;

public class CatTest {
    public static void main(String[] args){

         // 对象实例化

          Cat one = new Cat("tom", 2, 1000, "英国短毛猫");
          System.out.println(one.name);
          System.out.println(one.month);
          System.out.println(one.weight);
          System.out.println(one.species);
          one.run();

    }
}
```