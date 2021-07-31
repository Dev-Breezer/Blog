# Java 内部类

&emsp;

> - 在Java中，可以将一个类定义在另一个类里面或者一个方法里面，这样的类称为内部类
> - 与之对应，包含内部类的类被称为外部类

```java
//外部类︰人
public class Person {
    int age;    //年龄
    public Heart getHeart()
        {
        return new Heart();
}
//内部类:心脏class Heart
    public String beat(){
        return "心脏在跳动";
        }
}
```

&emsp;

### 为什么要将类定义在另一个类里面呢?

&emsp;

> - 其目的：内部类隐藏在外部类之类，更好的实现了信息隐藏。

&emsp;

### 内部类分类：

&emsp;

> - 成员内部类
> - 静态内部类
> - 方法内部类
> - 匿名内部类

&emsp;

### 成员内部类

&emsp;

> 1. 内部类中最常见的就是成员内部类，也称为普通内部类
> 2. 内部类在外部使用时，无法直接实例化，需要借由外部信息才能完成实例化  
> 3. 内部类的访问修饰符可以任意，但访问范围会受到影响  
> 4. 内部类可以直接访问外部类的成员；如果出现同名属性，优先访问内部类中的定义的  
> 5. 可以使用外部类.this.成员的方式，访问外部类中同名的信息  
> 6. 外部类访问内部类信息，需要通过内部类实例，无法直接访问  
> 7. 内部类编译后.class文件命名：外部类$内部类.class  

```java
package com.demo.people;

//  外部类
public class Person {
    public int age;

    public Heart getHeart(){
        new Heart().temp = 12;
        return new Heart();
    }

    public  void eat(){
        System.out.println("人会吃东西");
    }

package com.demo.people;

//  外部类
public class Person {
    public int age;

    public Heart getHeart(){
        new Heart().temp = 12;
        return new Heart();
    }

    public  void eat(){
        System.out.println("人会吃东西");
    }

    //  成员内部类
    /*
    *   1. 内部类在外部使用时，无法直接实例化，需要借由外部信息才能完成实例化
    *   2. 内部类的访问修饰符可以任意，但访问范围会受到影响
    *   3. 内部类可以直接访问外部类的成员；如果出现同名属性，优先访问内部类中的定义的
    *   4. 可以使用外部类.this.成员的方式，访问外部类中同名的信息
    *   5. 外部类访问内部类信息，需要通过内部类实例，无法直接访问
    *   6. 内部类编译后.class文件命名：外部类$内部类.class
    */
            public class Heart{
                int age = 13;
                int temp = 22;
                public String beat(){
                    eat();
                    return Person.this.age + "心脏在跳动";

                }
    }
}

```

&emsp;

```java
package com.demo.people;

import com.demo.people.Person;

public class PeopleTest {
    public static void main(String[] args) {
        Person tom = new Person();
        tom.age = 12;

        //  获取内部类对象实例，方式1：new 外部类.new 内部类
        Person.Heart myHeart = new Person().new Heart();
        System.out.println(myHeart.beat());

        //  获取内部类对象实例，方式2：外部类对象.new 内部类
        myHeart = tom.new Heart();
        System.out.println(myHeart.beat());

        //  获取内部类对象实例，方式3：外部类对象.获取方法
        myHeart = tom.getHeart();
        System.out.println(myHeart.beat());
```

### 内部类中是否可以包含于外部类相同的方法签名的方法？ 

&emsp;

### 静态内部类

&emsp;

> 1. 静态内部类中，只能直接访问外部类中的静态成员，如果需要调用非静态成员，可以通过对象实例
> 2. 静态内部类实例时，可以不依赖于外部类
> 3. 可以通过外部类.内部类.静态成员的方式，访问内部类中的静态成员
> 4. 当内部类属性和外部类属性同名时，默认直接调用内部类中的成员，如果需要访问外部类中的静态属性，则可以通过外部类.属性的方式访问
如果需要方法外部类中的非静态属性，则可以通过 new 外部类().属性 的方式

&emsp;

```java
package com.demo.people;

//  外部类
public class Person {
    public int age;

    public Heart getHeart(){
        new Heart().temp = 12;
        return new Heart();
    }

    public  void eat(){
        System.out.println("人会吃东西");
    }



    //  静态内部类
    /*
    * 1. 静态内部类中，只能直接访问外部类中的静态成员，如果需要调用非静态成员，可以通过对象实例
    * 2. 静态内部类实例时，可以不依赖于外部类
    * 3. 可以通过外部类.内部类.静态成员的方式，访问内部类中的静态成员
    * 4. 当内部类属性和外部类属性同名时，默认直接调用内部类中的成员，如果需要访问外部类中的静态属性，则可以通过外部类.属性的方式访问
    * 如果需要方法外部类中的非静态属性，则可以通过 new 外部类().属性 的方式
    * */
    public static class Heart{
        int age = 13;
        int temp = 22;
        public static void say(){
            System.out.println("hello");
        }
        public String beat(){
            new Person().eat();
            return new Person().age + "心脏在跳动";

        }
    }
}
```

&emsp;

```java
    //  获取静态内部类实例

    Person.Heart myHeart = new Person.Heart();
    System.out.println(myHeart.beat());
    Person.Heart.say();
```

&emsp;

### 方法内部类

&emsp;

> + 方法内部类，定义在外部类方法中的内部类，也称局部内部类

&emsp;

### 方法内成员使用规则:

&emsp;

> - 方法内定义的局部变量只能在方法里使用
> - 方法内不能定义静态成员
> - 不能public、private、protected

&emsp;

> - 1. 定义在方法内部，作用范围也在方法内
> - 2. 和方法内部成员使用规则一样，class前面不可以添加public、private、protected、 static
> - 3. 类中不能包含静态成员
> - 4. 类中可以包含final、 abstract修饰的成员（不推荐）
```java
package com.demo.people;

//  外部类
public class Person {
    public static int age;

    public Object getHeart() {
        //  方法内部类
        /*
        * 1. 定义在方法内部，作用范围也在方法内
        * 2. 和方法内部成员使用规则一样，class前面不可以添加public、private、protected、 static
        * 3. 类中不能包含静态成员
        * 4. 类中可以包含final、 abstract修饰的成员（不推荐）
         * */
        class Heart {
            public int age = 13;
            int temp = 22;

            public void say() {
                System.out.println("hello");
            }

            public void eat() {
            }

            public String beat() {
                new Person().eat();
                return Person.age + "岁的心脏在跳动";
            }

        }
        return new Heart().beat();

```

&emsp;

匿名内部类

&emsp;

### 在某一些程序中，我们对某些类的实例只会使用一次，该类的名字对整个程序而言，就变得可有可无，这种情况，我可以把类的定义与类的创建，放到一起完成

&emsp;

```java
package com.demo.test;

import com.demo.anonymous.Person;

public class PersonTest {
    //  根据传入不同的人的类型，调用对应的read方法

    //  方案1：
    public void getRead(Man man){
        man.read();
    }
    public void getRead(Woman woman){
        woman.read();
    }

    //  方案2：
    public void getRead(Person person){
        person.read();
    }

    public static void main(String[] args) {
        PersonTest test = new PersonTest();
       Man one = new Man();
        Woman two = new Woman();
        test.getRead(one);
        test.getRead(two);

        // 方案3：匿名内部类
        /*
        * 1. 匿名内部类没有类型名称、实例对象名称
        * 2. 编译后的文件名称：外部类$数字.class
        * 3. 无法使用访问修饰符（private, public, protected, abstract, static）
        * 4. 无法在匿名内部类中编写构造方法，可以添加构造代码块
        * 5. 不能出现静态成员
        * 6. 匿名内部类可以实现接口也可以继承父类，但是不可兼得
        * */
        test.getRead(new Person() {
            @Override
            public void read(){
                System.out.println("男生喜欢看科幻类书籍");
            }
        });

        test.getRead(new Person() {
            @Override
            public void read(){
                System.out.println("女生喜欢看言情小说类书籍");
            }
        });
    }
}
```