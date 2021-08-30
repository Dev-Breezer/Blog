# Java 接口

&emsp;

### Java中只支持单继承  
### 如何解决一个类型中需要兼容多种类型特征的问题?-以及多个不同类型具有相同特征的问题呢?

&emsp;


&emsp;

### 定义接口并测试

&emsp;

```java
package com.demo.tel;

public class FourthPhone extends ThirdPhone implements IPhoto{

    @Override
    public void photo() {
        
        System.out.println("手机可以拍照");
    }

    public void network(){
        System.out.println("手机可以上网");
    }
    public void game(){
        
        System.out.println("手机可以玩游戏");
    }


}
```

&emsp;

```java
package com.demo.tel;

public class Camera implements IPhoto{

    @Override
    public void photo() {
        System.out.println("相机可以拍照");
    }
}

```

&emsp;

```java
package com.demo.tel;

/**
 * 具有照相能力的接口
 * @author Dev-Breezer
 */
public interface IPhoto {
    //  具有拍照的能力
    public void photo();

}
```

&emsp;

```java
package com.demo.test;

import com.demo.tel.*;

public class PhoneTest {
    public static void main(String[] args) {
        IPhoto ip = new FourthPhone();
        ip.photo();
        ip = new Camera();
        ip.photo();
```

&emsp;

### 接口

&emsp;

> - 接口定义了某一批类所需要遵守的规范
> -接口不关心这些类的内部数据，也不关心这些类里方法的实现细节，它只规定这些类里必须提供某些方法。
> -

&emsp;

### 接口成员——抽象方法、常量

&emsp;

```java
package com.demo.tel;

//  接口访问修饰符：public、默认修饰符
public interface INet {
    /* 接口抽象方法可以不写 abstract 关键字
       访问修饰符默认 public
       当类实现接口时，需要去是实现接口当中所有抽象方法
       如果有部分方法未实现，同时不想使其报错，此时我们需要把当前的类设定成抽象类
    */
    public void network();
    public void connection();

    //  接口当中可以包含常量，在接口中定义常量，默认加入 public static final
    int TEMP = 20;
}
```

&emsp;

```java
package com.demo.tel;

/**
 * 具有照相能力的接口
 * @author Dev-Breezer
 */
public interface IPhoto {
    //  具有拍照的能力
    public void photo();

}
```

&emsp;

```java
package com.demo.test;

import com.demo.tel.*;

public class PhoneTest {
    public static void main(String[] args) {
        FourthPhone phone = new FourthPhone();
        phone.call();
        phone.message();
        phone.vedio();
        phone.music();
        phone.photo();
        phone.network();
        System.out.println("==============================");
        IPhoto ip = new FourthPhone();
        ip.photo();
        ip = new Camera();
        ip.photo();
        System.out.println("==============================");
        System.out.println(INet.TEMP);
        INet net = new SmartWatch();
        System.out.println(net.TEMP);
    }
}
```

&emsp;

### 接口继承

&emsp;

#### 接口也可以实现继承，并且可以继承多个父接口

&emsp;

```java
package com.demo.test;

public interface IFather {
    void say();

    default void connection(){
        System.out.println("IFather中的connection");
    }
}
```

&emsp;

```java
package com.demo.test;

public interface IFather2 {
    void fly();
    default void connection(){
        System.out.println("IFather2中的connection");
    }
}
```

&emsp;

```java
package com.demo.test;

//  接口也可以实现继承，并且可以继承多个父接口
public interface ISon extends IFather,IFather2{
    void run();
    default void connection(){
        System.out.println("ISon中的connection");
    }

}
```