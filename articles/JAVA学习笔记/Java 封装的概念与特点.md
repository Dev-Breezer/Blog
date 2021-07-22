# Java 封装的概念与特点

<br>
<br>

### 封装

<br>

> + 将该类的某些信息隐藏在类内部，不允许外部程序直接访问
> + 通过该类提供的方法来实现对隐藏信息的操作和访问
> + **隐藏** 对象的信息
> + **留出** 访问的接口

<br>

#### 案例

在日常生活中我们可以通过 ATM机 存取款、转账、余额查询，而对于 ATM 机而言，钞票是 ATM 机的重要信息，但是我们在外部是无法看到这些钞票的，也不能够随意的拿取钞票，这就是 ATM 机对钞票这个重要信息的隐藏，与此同时，ATM 机提供了相应的操作接口（插卡槽、取钞口、操作屏），用户只需要通过简单的操作，就能获取到机器里存储的钞票。

<br>

### 封装的特点

<br>

> + 只能通过规定的方法访问数据
> + 隐藏类的实例细节、方便修改和实现


<br>

### 封装的代码实现（一）

<br>

#### Java 封装的实现步骤

<br>

>  1. 修改类当中属性的可见性，将其访问修饰符设置为 private（私有化）当属性或方法被 private 修饰，表示当前属性或方法只能在当前类内被访问
> 2. 设置开放的接口，我们需要去创建对应属性的公有的 getter()（取值）和 setter（赋值）方法（使用修饰符 public 描述） 
> 3. 在 getter() 和 setter() 方法中加入属性控制语句（对属性值的合法性进行判断）

<br>

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
    int month;      //  年龄  int 类型默认值：0
    double weight;  //  体重  double 类型默认值 0.0
    String species; //  品种




    //  封装步骤：2.设置开放接口，创建公有的get/set方法 -- public
    //  在 get/set 方法中添加对属性的限定
    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return "我是一只名叫："+ this.name + "的宠物猫";
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

        Cat one = new Cat();
        one.setName("凡凡");
        System.out.println("昵称:" + one.getName());

    }
}
```

<br>

<br>

### 封装的代码实现（二）

<br>


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


    public Cat(int month){
        this.setMonth(month);
    }



    //  封装步骤：2.设置开放接口，创建公有的get/set方法 -- public
    //  在 get/set 方法中添加对属性的限定
    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return "我是一只名叫："+ this.name + "的宠物猫";
    }

    public void setMonth(int month) {
        if(month <=0){
            System.out.println("输入错误，宠物猫年龄必须大于0");
        }
        else{

            this.month = month;
        }
    }

    public int getMonth() {
        return month;
    }

    public void setWeight(double weight) {
        this.weight = weight;
    }

    public double getWeight() {
        return weight;
    }

    public void setSpecies(String species) {
        this.species = species;
    }

    public String getSpecies() {
        return species;
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

        Cat one = new Cat(-3);
   
        if(one.getMonth()==0)
            return;
        System.out.println("年龄:" +one.getMonth());

    }
}


```