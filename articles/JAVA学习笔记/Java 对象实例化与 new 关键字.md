# Java 对象实例化


<br>

### **new** 关键字（一）

<br>

> + 实例化对象的过程可以分为两部分
> + &emsp;&emsp; - 声明对象 CatOne
> + &emsp;&emsp; - 实例化对象 new Cat();
> + new 关键字的作用：**开辟新的对象空间** ，（与之前实例化的对象是互不相干的）

<br>

```java
package com.demo.animal;

/**
 *
 */

public class CatTest {
    public static void main(String[] args){
        //  对象实例化
        //  Cat one; //  声明对象
        Cat one = new Cat();
        Cat two = new Cat();
        one.name = "Tom";
        one.month = 2;
        one.weight = 2000;
        one.species = "加菲猫";

        two.name = "Ali";
        two.month = 3;
        two.weight = 4000;
        two.species = "英国短尾猫";
        /*
          测试
          one.eat();
          one.run();
        */
        System.out.println("昵称:" + one.name);
        System.out.println("年龄:" + one.month);
        System.out.println("体重: " + one.weight);
        System.out.println("品种: " + one.species);
        System.out.println("----------------------------------------------");
        System.out.println("昵称:" + two.name);
        System.out.println("年龄:" + two.month);
        System.out.println("体重: " + two.weight);
        System.out.println("品种: " + two.species);
        //  one.run(one.name);


    }
}


```

<br>

### **new** 关键字（二）

<br>

### 疑点一：对象实例化是不是只有 new 一种实现方式呢

<br>

> + 实例化对象的过程可以分为两部分
> + &emsp;&emsp; - 声明对象 CatOne
> + &emsp;&emsp; - 实例化对象 new Cat();
> + new 关键字的作用：**开辟新的对象空间** ，（与之前实例化的对象是互不相干的）

<br>

```java
package com.demo.animal;

public class CatTest {
    public static void main(String[] args){
        /*
          对象实例化
          Cat one; //  声明对象
          Cat two = new Cat();
        */
        Cat one = new Cat();
        Cat two = one;
        one.name = "Tom";
        one.month = 2;
        one.weight = 2000;
        one.species = "加菲猫";

        two.name = "Ali";
        two.month = 3;
        two.weight = 4000;
        two.species = "英国短尾猫";
        /*
          测试
          one.eat();
          one.run();
        */
        System.out.println("昵称:" + one.name);
        System.out.println("年龄:" + one.month);
        System.out.println("体重: " + one.weight);
        System.out.println("品种: " + one.species);
        System.out.println("----------------------------------------------");
        System.out.println("昵称:" + two.name);
        System.out.println("年龄:" + two.month);
        System.out.println("体重: " + two.weight);
        System.out.println("品种: " + two.species);
        //  one.run(one.name);


    }
}


```
<br>

### 注意事项

<br>

> + 需要多次访问同一个对象，必须进行声明  
> + **如果我们只是需要调用 Cat 类下的 run() 方法，我们可以通过匿名对象进行方法调用**（即：省略对象声明操作）
> + **在相同的作用范围内，不能出现同名的对象**

<br>

```java
public class CatTest {
  public static void main(Stringargs){
    new Cat).run();     //  匿名对象进行方法调用
    
    }
}
```

<br>

> + **可以同时声明多个引用，用逗号分隔**
> + **也可以在一行同时实例化多个对象，用逗号分隔**

<br>

```java
public class CatTest {
  public static void main(String[args){
    Cat one,two;
    one=new Cat();
    two=new Cat();
    
    Cat three = new Cat(), four = new Cat();
    }
}

```

<br>

### 关于构造方法的注意事项：
> + 如果你个普通方法无返回值恰好与类同名，并不会产生语法错误，而且可以运行，但是我们不推荐这么做，构造方法不能直接被对象调用，需要搭配 new 关键字使用
> + 如果需要在一个带参构造方法中调用无参构造方法可以通过 **this()**，调用并且必须放在方法体的第一行

<br>

```java
  public Cat(String name, int month, double weight, String species){
        this();
        this.name = name;
        this.month = month;
        this.weight = weight;
        this.species =species;
    }
```

<br>

#### 调用带参构造方法在 this() 中加入参数
<br>

```java
  public Cat(String name, int month, double weight, String species){
        this("阿七");
        this.name = name;
        this.month = month;
        this.weight = weight;
        this.species =species;
    }
```