# Java static 关键字

<br>
<br>
<br>

```java
/*  public  -- 访问修饰符
    void    -- 方法返回值类型
    main    --  方法名
    String[] args   -- 方法参数
*/
public static void main(String[] args){} 
```

&emsp;

### static 关键字

&emsp;

> static -- 表示静态的，使用 static 修饰的成员我们称为：**静态成员、****类成员**  
> **在 Java 程序当中&emsp;static&emsp;修饰的成员，具有一个特征：无论这个类实例化出多少个对象，都会共用同一块静态空间（存储空间）**  
> **作用：**  
> **特点：**  
&emsp; 1.类对象功效  
&emsp; 2.类加载时产生，销毁时释放、生命周期长

&emsp;

#### 对于普通成员而言，当某个类的对象实例化产生，实例化对象的相关成员会产生，当实例化对象被销毁，实例化对象的相关成员也会被销毁。  
#### 对于静态成员而言，从类第一次加载（静态成员）时就会产生，直到这个类不会再有任何对象被使用（彻底销毁），静态资源才会被释放  
#### 当 static 加在属性前时称之为静态属性、类属性，当把 static 加在方法前时，称之为静态方法、类方法
&emsp;

### 静态成员的访问方法：

&emsp;
> + 对象 . 成员（属性或方法）
> + 类 . 成员（属性或方法）

&emsp;

#### **静态成员方法或静态成员属性推荐调用方式：类.静态成员（属性或方法）**

&emsp;

```java
    package com.demo.test;

import com.demo.animal.Cat;

public class Test {
    public static void main(String[] args){
        Cat one = new Cat();
        one.setName("tom");
        one.setMonth(2);
        one.setSpecies("英国短毛猫");

        //  静态成员的两种访问方法
        one.price = 2000;
        Cat.price = 3000;



        System.out.println(one.getName() + "的售价" + one.price);
    }
}

```

&emsp;

### 疑点：static 在 Java 程序中可以和哪些信息组合使用？

> + static 可以用来修饰**成员属性**和**成员方法**
> + _class 不能用来修饰类，修饰类只能使用 public、abstract、final_
> + _在局部变量前不能添加 static 只能添加 final_
> + 静态方法中无法直接调用同一个类中非静态成员（方法和属性），只能直接调用同一个类中的静态成员（方法和属性）
> + 如果要调用同一个类中的非静态成员，只能通过对象实例化后，**对象.成员方法**的方式访问
> + 静态方法中不能使用 this，同时不能使用静态方式访问一个非静态成员（字段）

&emsp;

### 静态方法或类方法调用

&emsp;
```java
package com.demo.test;

import com.demo.animal.Cat;   //  加载 com.demo.animal 下的 Cat 类（即：加载 com.demo.animal 包下的指定类）

public class Test {
    public static void main(String[] args){
        Cat one = new Cat();
        Cat.eat();  //  推荐使用这种方法调用类方法
        one.eat();

    }
}


```

&emsp;

### 普通成员方法调用静态方法、静态属性
### 静态方法调用同一类下的非静态方法

&emsp;

```java
package com.demo.animal;

/**
 * 宠物猫类
 * @author Dev-Breezer
 */

public class Cat {
    //  成员属性：昵称、年龄、体重、品种
    // 封装步骤：1.修改属性的可见性 -- private --限定只能在当前类内被访问

    private String name;    //  昵称  String 类型默认值：null, 该属性只能在当前类内被访问
    private int month;      //  年龄  int 类型默认值：0
    private double weight;  //  体重  double 类型默认值 0.0
    private String species; //  品种

    public static int price;   //  售价

    public Cat(){
        System.out.println("我是宠物猫");
    }

    public Cat(int month){
        this.setMonth(month);
    }
//  成员方法：跑动、吃
    //  跑动的方法
    public void run(){
        this.eat();
        this.name = "阿九";
        this.price = 20;
        System.out.println("小猫在跑");
        System.out.println("售价是"+ Cat.price +this.name + "快跑");
    }

    //  方法重载
    public void run(String name){
        System.out.println("售价是"+ Cat.price +this.name + "快跑");
    }

        //  吃东西的方法
        public static void eat(){
            Cat temp = new Cat();   
            temp.run();
            System.out.println("小猫吃鱼干");
        }

}
```

&emsp;

```java
package com.demo.test;

import com.demo.animal.Cat;

public class Test {
    public static void main(String[] args){
        Cat one = new Cat();
        one.setName("tom");
        one.setMonth(2);
        one.setSpecies("英国短毛猫");
        one.price = 2000;
        Cat.price = 3000;
        Cat.eat();
        one.run();
    }
}
```