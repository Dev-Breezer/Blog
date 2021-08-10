# Java 泛型

&emsp;

### 使用泛型的有点

&emsp;

    在Java中增加泛型之前，泛型程序设计使用继承来实现的坏处:
        
        需要强制转换
        可向集合中添加任意类型的对象，存在风险。


&emsp;

### 泛型的使用

&emsp;

```java
List<String> list = new ArrayList<String();

//  Java SE7及以后的版本中，构造方法中可以省略泛型类型。

List<String> list=new ArrayList<>);

```

&emsp;

### **多态与泛型**

&emsp;

```java
class Animal0
class Cat extends Animalt
List<Animal> list=new ArrayList<Cat>0;
//  变量声明的类型必须匹配传递给实际对象的类型


//  其他的错误例子∶
List<Object> list=new ArrayList<Striring>();
List<Number> numbers=new ArrayLiist<Integer>();
```

&emsp;

### 学习重点：

&emsp;

    泛型作为方法参数并且调用该方法、传参  
    自定义泛型类  
    自定义泛型方法

&emsp;

### 案例

&emsp;

#### **泛型作为方法参数**

&emsp;

    案例需求:  
    定义一个抽象类Goods，包含抽象方法sell()  
    分别定义类Book、Clothes和Shoes继承Goods，并实现sell0方法，输出─句话，如:sell books  
    定义一个商品销售类GoodsSeller，模拟销售，包括方法:public void sellGoods(List<Goods> goods),循环调用List对
    象的sell(方法。
    
    
&emsp;

```java
package com.demo.generic;

public abstract class Goods {
    public abstract void sell();
}
```

&emsp;

```java
package com.demo.generic;

public class Book extends Goods{

    @Override
    public void sell() {
        System.out.println("sell books");
    }
}
```

&emsp;

```java
package com.demo.generic;

public class Clothes extends Goods{

    @Override
    public void sell() {
        System.out.println("sell clothes");
    }
}
```

&emsp;


```java
package com.demo.generic;

public class Shoes extends Goods{

    @Override
    public void sell() {
        System.out.println("sell shoes");
    }
}
```

&emsp;

```java
package com.demo.generic;

import java.util.List;

public class GoodsSeller {
    public void sellGoods(List<? extends Goods> goods){

        //  调用集合重sell方法
        for(Goods g:goods){
            g.sell();
        }
    }
}
```

&emsp;

```java
package com.demo.generic;

import java.util.ArrayList;
import java.util.List;

public class GoodsTest {
    public static void main(String[] args) {

        //  定义 book 相关的 List
        List<Book> books = new ArrayList<>();
        books.add(new Book());
        books.add(new Book());

        //  定义 <clothes> 相关的 List
        List<Clothes> clothes = new ArrayList<>();
        clothes.add(new Clothes());
        clothes.add(new Clothes());

        //  定义 shoes 相关的 List
        List<Shoes> shoes = new ArrayList<>();
        shoes.add(new Shoes());
        shoes.add(new Shoes());

        //  泛型作为参数的方法
        //  1.定义一个泛型所在泛型方法它所在类的对象
        GoodsSeller goodsSeller = new GoodsSeller();
        goodsSeller.sellGoods(books);
    }
}
```

&emsp;

#### **自定义泛型（一）**

&emsp;

```java
package com.demo.generic;


//  自定义泛型类
public class NumGeneric <T>{
    private T num;

    public T getNum() {
        return num;
    }

    public void setNum(T num) {
        this.num = num;
    }
    //  测试
    public static void main(String[] args) {
        NumGeneric<Integer> intNum = new NumGeneric<>();
        intNum.setNum(10);
        System.out.println("Integer: " + intNum.getNum());

        NumGeneric<Float> floatNum = new NumGeneric<>();
        floatNum.setNum(5.0f);
        System.out.println("Float: " + floatNum.getNum());
    }
}
```
&emsp;

#### **自定义泛型（二）**

&emsp;

```java
package com.demo.generic;

public class TwoNumGeneric <T, X>{
    private T num1;
    private X num2;

    public void genNum(T num1, X num2){
        this.num1 = num1;
        this.num2 = num2;
    }

    public T getNum1() {
        return num1;
    }

    public void setNum1(T num1) {
        this.num1 = num1;
    }

    public X getNum2() {
        return num2;
    }

    public void setNum2(X num2) {
        this.num2 = num2;
    }

    //  测试
    public static void main(String[] args) {
        TwoNumGeneric<Integer, Float> numObj = new TwoNumGeneric<>();
        numObj.genNum(25, 5.0f);
        System.out.println("num1 = " + numObj.getNum1());
        System.out.println("num2 = " + numObj.getNum2());
    }
}
```

&emsp;

### **自定义泛型方法**

&emsp;

```java
package com.demo.generic;

public class GenericMethod {

    //  泛型方法
    public <T extends Number> void printValue(T t){
        System.out.println(t);
    }

    //  测试
    public static void main(String[] args) {
        GenericMethod gm = new GenericMethod();
        //  gm.printValue("hello");
        gm.printValue(458);
        gm.printValue(5.0f);
    }
}
```
