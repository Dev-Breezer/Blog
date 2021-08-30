# Java 运算符概述

<br>

### 表达式
> + 表达式是由 **运算符** 和 **操作数**组成

<br>

### 例子：

```java
5   //只写一个常量，可以作为独立的表达式  
varNumber    //只有一个变量，例如 varNum 也可以作为一个独立的表达式  
varNumber1+varNumber2  //这也是一个表达式，其中，加号（+）是操作符，varNumber1和varNumber2是操作数
sum = varNumber1+varNumber2 //一个拥有两步运算的表达式
```


<br>
<br>

### 运算符

> + 算术运算符
> + 赋值运算符
> + 关系运算符
> + 逻辑运算符
> + 条件运算符
> + 位运算符


<br>
<br>


### 算术运算符

<br>

作用：  
> + 进行基本的算术运算，例如加、减、乘、除

<br>

> |算术运算符|名称|举例|  
> | :-: | :-: | :-:|
> |+|加法|2+10=12|
> |-|减法|10-10=0|
> |*|乘法|2*6=12|
> |/|除法|25/5=5|
> |%|求余数|13%4=1|
> |++|自增1|int num=1;n++或（++n）|
> |--|自减1|int num=5;n--或（--n）|

<br>
<br>

```java

package Java操作符;

public class MathOperator {
    public static void main(String[] args){
        int intNum1 = 2, intNum2 = 10;
        int result;     // 存放结果

        // 加法
        result = intNum1 + intNum2;
        System.out.print("加法：");
        System.out.println(intNum1 + "+" + intNum2 + "=" + result);

        //  TODO: 这里的字符串连接操作要清楚作用
        System.out.print("字符串连接效果：");
        System.out.println(""+intNum1+intNum2);

        //  减法
        result = intNum2 - intNum1;
        System.out.print("减法：");
        System.out.println(intNum2 + "-" + intNum1 + "=" + result);

        //  乘法
        result = intNum1 * intNum2;
        System.out.print("乘法：");
        System.out.println(intNum1 + "x" + intNum2 + "=" + result);

        //  除法
        result = intNum2 / intNum1;
        System.out.print("除法：");
        System.out.println(intNum2 + "/" + intNum1 + "=" + result);

        //TODO: 另一种情况：当分子分母都为int类型，结果为整除结果，为保证最终结果的精度，我们需要使分子或分母之中的一个为浮点型

        //  当分子分母都为int类型的情况
        System.out.print("当分子分母都为int类型的情况：\n");
        System.out.println("13/5=" + 13/5);

        //  当分子或分母之一为浮点型的情况
        System.out.print("当分子分母其中一个为浮点型的情况：\n");
        System.out.println("13/5=" + 13.0/5);

        //  求余数
        result = 13 % intNum1;
        System.out.print("求余数：");
        System.out.println(13 + "%" + intNum1 + "=" + result);
        System.out.print("求余数：");
        System.out.println("13.5%" + intNum1 + "=" + 13.5 % intNum1);
    }
}


```
