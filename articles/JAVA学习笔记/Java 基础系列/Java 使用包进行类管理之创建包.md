# Java 使用包进行类管理

<br>

### 使用包对类进行管理的一些注意事项：

<br>

> + 在 Java 当中，一个包下面不允许存在同名的类
> + 单一职责原则：建议每个包内存储信息功能单一

<br>

### 定义包

<br>

语法格式：

<br>

```java
package 包名;
package com.demo.test;
```
<br>

#### 注意：   

<br>

> + package 语句必须放在 Java 源文件第一行
> + 一个 Java 源文件中有且只能有一个 package 语句
> + 包名全部小写
> + 推荐 Java 包命名：域名倒序 + 模块名称 + 功能

<br>

### Java 跨包调用

<br>

#### 导入包

<br>

> 使用加载语句导入包实现跨包调用：

<br>

```java
//  import 包名信息
import java.util.Scanner;
```
<br>

> 第一种方式： 加载 com.demo.animal 下的所有类

<br>

```java
import com.demo.animal.*;   //  加载 com.demo.animal 下的所有类
```


<br>

> 第二种方式： 加载 com.demo.animal 包下的指定类  
<br>

```java
import com.demo.animal.Cat;   //    加载 com.demo.animal 下的 Cat 类（即：加载 com.demo.animal 包下的指定类）
```

<br>

> **注意事项：在 Java 中导入不同包下的同名类是不被允许的，会使 Java 无法识别你想导入的那一个类**

<br>

```java
import com.demo.animal.Cat;   //  加载 com.demo.animal 下的 Cat 类
import com.demo.rebocat.Cat;  //  加载 com.demo.rebocat 下的 Cat 类
```

<br>

> 解决方案一、修改其中一条导入语句

<br>

```java
import com.demo.animal.Cat;   //  加载 com.demo.animal 下的 Cat 类（即：加载 com.demo.animal 包下的指定类）
import com.demo.rebocat.*;  //  加载 com.demo.rebocat 下的所有类  
```

<br>

### 总结

<br>

> + **推荐使用 import 包名.类名 方式加载包中的类，以提高效率**
> + **加载类的顺序跟 import 导入语句的位置无关**  
> + **import 包名 只能访问指定包名下的类，无法访问子包下的类**
> + 包的作用：  
&emsp;1.管理 Java 文件  
&emsp;2.解决同名文件冲突