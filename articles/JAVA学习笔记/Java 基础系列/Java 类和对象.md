# Java 类和对象

<br>
<br>
<br>

### 什么是对象

<br>

> + 现实存在的客观事物都是对象

<br>

### 什么是面向对象

<br>

> + 与对象面对面、关注对象
> + 从计算机的角度而言：关注现实存在的事物各方面的信息 

<br>

### 什么是类

<br>

> + 类就是模型，确定对象将会拥有的特征（属性）和行为（方法）

<br>

类和对象的关系  

<br>

> + 对象是类的实例化的表现
> + 类是对象的类型  
> + 对象是特定类型的数据  

<br>

> + 类  
> 所谓的类是一个 **抽象的概念** 现实中一个虚拟的存在，描述了一个 **模板** 它限定了一种类型当中应该有什么以及能做什么

<br>

> + 对象  
> 由一个类实例化产生的具体体现，真正意义上看的见、摸得着的具体实体



<br>

### 属性和方法

<br>

> + 属性：对象所具有的各种静态特征（即：对象有什么）
> + 方法：对象所具有的各种动态行为 （即：对象能做什么）

<br>

### 案例：

<br>

> 比如 我想去宠物店买一只猫，而宠物店的猫都有 **名字**、**毛色**、**年龄**、**品种**、**体重**，以上这些都是所有宠物猫拥有的特征（即：属性）  
> 而宠物猫能 **跑**、**跳**、**睡**、**吃**、**叫** 以上这些都是宠物猫所具有的行为（即：方法）

<br>

> + 在实际的项目开发过程中： 我们会首先定义一个类，然后根据类再去实例化一个对象，最后完成相应的程序逻辑

<br>
<br>

### **创建类**

<br>

> + 包名的推荐命名规范  
&emsp; - 英文字母小写   
&emsp; - 域名倒序

<br>

```java
package com.demo.animal;

/**
 * 宠物猫类
 * @author Dev-Breezer
 */

public class Cat {
    //  成员属性：昵称、年龄、体重、品种
    String name;    //  昵称
    int month;      //  年龄
    double weight;  //  体重
    String species; //  品种

    //  成员方法：跑动、吃
    //  跑动的方法
    public void run(){
        System.out.println("小猫在跑");
    }

    //  吃东西的方法
    public void eat(){
        System.out.println("小猫吃鱼干");
    }

}
```

<br>
<br>
<br>

### **实例化对象**

<br>

#### 语法格式：

<br>

```java
ClassName ObjectName = new ClassName();      //实例化对象

        Cat one = new Cat();
```

<br>

#### 定义Cat类
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

#### 调用 Cat 类中的属性和方法
<br>

```java
package com.demo.animal;

/**
 *
 */

public class CatTest {
    public static void main(String[] args){
        //  对象实例化
        Cat one = new Cat();
        one.name = "Tom";
        one.month = 2;
        one.weight = 2000;
        one.species = "加菲猫";

        //  测试
        one.eat();
        one.run();
        System.out.println("昵称:"+one.name);
        System.out.println("年龄:"+one.month);
        System.out.println("体重: "+one.weight);
        System.out.println("品种: "+one.species);
        one.run(one.name);


    }
}


```

<br>
<br>
<br>


## 疑点一：为什么 main 方法不直接写在 Cat类中而是写在 CatTest 类中？

<br>

### **单一职责原则（单一功能原则）**

<br>

> + 在单一职责原则中：我们建议一个类有且只有一个引起功能变化的原因（即：一个类，只有一个功能，只干一件事）

<br>

## 疑点二： CatTest 类是如何找到 Cat 类的呢？

<br>

### **Java 搜索机制**

<br>

> + 当 main 方法运行时，会首先在所在的类中查找相关的类是否存在（会先在在 CatTest 类中查找 Cat 类）
> + 如果发现 Cat 类不存在于 CatTest 类中，Java 会向上查找同一个包下的类（即：在 package com.demo.animal 包中寻找有没有 Cat 类，如果能够找到被**允许访问的 Cat 类**，进而查找 Cat 类中的成员属性和方法，如果Cat类中的**成员属性和方法也是可以允许被访问的**，则 CatTest 中的代码可以被执行，直到结束）

<br>
<br>

### 例题:
<br>

> + 定义 Person

<br>

```java
package com.demo.person;

public class Person {
    //  定义成员属性
    String name;
    int age;
    String grade;


    //  定义方法
    public void student(){
        System.out.println("我是一名学生!");
    }

    public void sex(int sex){
        System.out.println("我是一个男孩!");
    }

    public void mySelf(String name, int age, String grade){
        System.out.println("我叫" + name + "，今年" + age + "岁了，" + "读小学" + grade + "了。");
    }


}
```

<br>

> + 定义 PersonTest 类并调用 Person 类

<br>

```java
package com.demo.person;

public class PersonTest {
    public static void main(String[] args){
        Person student = new Person();
        student.name = "小明";
        student.age = 10;
        student.grade = "五年级";
        student.student();
        student.sex(student.age);
        student.mySelf(student.name, student.age, student.grade);
    }
}

```