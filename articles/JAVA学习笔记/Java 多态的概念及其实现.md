# Java 多态的概念及其实现

### 多态的概念

&emsp;

### 多态满足的必要条件：

&emsp;

> - 满足继承关系
> - 父类引用指向子类对象


### 案例场景描述及实体类编写

&emsp;

### 向上转型（又名：隐式转型、自动转型）

&emsp;

> - 把一个子类对象转型位父类对象（即：向上转型）
> - 父类引用指向子类实例，可以调用子类重写父类的方法以及父类派生的方法，无法调用子类独有方法

&emsp;


### 向上转型（又名：隐式转型、自动转型）

&emsp;

> - 子类引用指向父类对象，此处必须进行强转
> - 可以调用子类特有的方法
>-  必须满足转型条件才能进行强转

&emsp;

### instanceof运算符

&emsp;

> - instanceof判断某个对象满足某个类的实力特征 返回值 true/false    （true：满足，false：不满足）


&emsp;


```java
package com.demo.animal;

public class Animal {
    //  属性：昵称，年龄
    private String name;
    private int month;


    public Animal(){

    }

    public Animal(String name, int month){
        this.setName(name);
        this.setMonth(month);
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

    //  方法，吃东西
    public void eat(){
        System.out.println("动物都有吃东西的能力！");
    }


}
```

&emsp;

```java
package com.demo.animal;

public class Cat extends Animal{
    // 属性：体重
    private  double weight;

    public Cat(){

    }

    public Cat(String name, int month, double weight){
        super(name,month);
        this.setWeight(weight);

    }

    public double getWeight() {
        return weight;
    }

    public void setWeight(double weight) {
        this.weight = weight;
    }

    //  方法： 跑动
    public void run(){
        System.out.println("小猫快乐的奔跑");
    }

    // 重写父类的 eat 方法
    @Override
    public void eat(){
        System.out.println("猫吃鱼~");
    }
}

```

&emsp;

&emsp;

```java
package com.demo.animal;

public class Dog extends Animal{
    // 属性：性别
    private String sex;

    public Dog(){

    }

    public Dog(String name, int month, String sex){
        this.setName(name);
        this.setMonth(month);
        this.setSex(sex);
    }

    public String getSex() {
        return sex;
    }

    public void setSex(String sex) {
        this.sex = sex;
    }

    // sleep 方法
    public void sleep(){
        System.out.println("小狗有午睡的习惯~");
    }

    // 重写父类吃东西方法
    @Override
    public void eat(){
        System.out.println("狗吃肉~");
    }
}
```

&emsp;

```java
package com.demo.test;

import com.demo.animal.Animal;
import com.demo.animal.Cat;
import com.demo.animal.Dog;
import javafx.beans.binding.ObjectExpression;

public class Test {
    public static void main(String[] args) {
        Animal one =new Animal();   //  1.
        Animal two = new Cat();     //  2.
        Animal three = new Dog();   //  3.
        /*
         向上转型（又名：隐式转型、自动转型）--> 父类引用指向子类实例
        父类引用指向子类实例，可以调用子类重写父类的方法以及父类派生的方法，无法调用子类独有方法
         小类转换为大类
        */
        one.eat();
        two.eat();
        three.eat();
        System.out.println("=======================================================");
        /*
         * 向下转型（又名：强制类型转换）
         * 类引用指向父类对象，此处必须进行强转
         * 可以调用子类特有的方法
         * 必须满足转型条件才能进行强转
         */

        if(two instanceof Cat){

            Cat temp = (Cat)two;
            temp.eat();
            temp.run();
            temp.getMonth();
            System.out.println("two 可以转换为 Cat 类型");
        }

        if(two instanceof Dog){
            Dog temp2 = (Dog)two;
            temp2.eat();
            temp2.sleep();
            temp2.getMonth();
            System.out.println("two 可以转化为 Dog 类型");
        }

        if(two instanceof Animal){
            System.out.println("Animal");
        }

        if(two instanceof Object){
            System.out.println("Object");
        }
    }
}

```

&emsp;

### 类型转换案例

&emsp;

案例一：

&emsp;

```java
package com.demo.animal;

public class Master {
    /*
    *喂宠物
    *  喂猫咪：吃完东西，主人会带着去玩线球
    *  喂狗：吃完东西后：主人会带着狗狗去睡觉
    */

    //  方案1：编写方法，传入不同类型的动物，调用各自得方法
    public void feed(Cat cat){
        cat.eat();
        cat.playBall();
    }

    public void feed(Dog dog){
        dog.eat();
        dog.sleep();
    }

    //  方案2：编写方法传入动物的父类，方法通过类型转换，调用指定子类的方法
    public void feed(Animal obj){
        if(obj instanceof Cat){
            Cat temp=(Cat) obj;
            temp.eat();
            temp.playBall();
        }
        else if(obj instanceof Dog){
            Dog temp = (Dog)obj;
            temp.eat();
            temp.sleep();
        }
    }
}
```

&emsp;

```java
package com.demo.animal;

public class Dog extends Animal{
    // 属性：性别
    private String sex;

    public Dog(){

    }

    public Dog(String name, int month, String sex){
        this.setName(name);
        this.setMonth(month);
        this.setSex(sex);
    }

    public String getSex() {
        return sex;
    }

    public void setSex(String sex) {
        this.sex = sex;
    }

    // sleep 方法
    public void sleep(){
        System.out.println("小狗有午睡的习惯~");
    }

    // 重写父类吃东西方法
    @Override
    public void eat(){
        System.out.println("狗吃肉~");
    }

}

```

&emsp;

```java
package com.demo.animal;

public class Cat extends Animal{
    // 属性：体重
    private  double weight;

    public Cat(){

    }

    public Cat(String name, int month, double weight){
        super(name,month);
        this.setWeight(weight);

    }

    public double getWeight() {
        return weight;
    }

    public void setWeight(double weight) {
        this.weight = weight;
    }

    //  方法： 跑动
    public void run(){
        System.out.println("小猫快乐的奔跑");
    }

    // 重写父类的 eat 方法
    @Override
    public void eat(){
        System.out.println("猫吃鱼~");
    }
    public void playBall(){
        System.out.println("小猫喜欢玩线球");
    }
}
```

&emsp;

```java
package com.demo.test;

import com.demo.animal.Cat;
import com.demo.animal.Dog;
import com.demo.animal.Master;

public class MasterTest {
    public static void main(String[] args) {
        Master master = new Master();
        Cat one = new Cat();
        Dog two = new Dog();
        master.feed(one);
        master.feed(two);
    }
}
```
