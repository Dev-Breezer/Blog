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

