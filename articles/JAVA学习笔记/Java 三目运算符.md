# Java 三目运算符

<br>
<br>
<br>
<br>

### 单目或（双目）运算符

<br>

> + 运算符我们大致可以分为:  
> + **++**、**--** 单目运算符
> + **+**、**-**、<b>*</b> 双目运算符 

<br>
<br>

### 三目运算符

<br>

> + 三目运算符也可以叫做条件运算符
> + 三目运算符可以理解成是一个复合(简化) 的 **if-else** 语句

<br>
<br>

### 语法格式：**布尔表达式？表达式1:表达式2**

> + 当布尔表达式结果为true时，执行表达式1,反之，为false，执行表达式2

```java

package Java操作符;

import java.util.Scanner;

public class ConditionDemo3 {
    public static void main(String[] args){

        //  输入两个整数
        System.out.println("请输入两个数值：");
        Scanner inputValue = new Scanner(System.in);
        int number1 = inputValue.nextInt();
        int number2 = inputValue.nextInt();
        int max;

        // 使用常规的if-else语句解决
        if (number1 > number2) {
            max = number1;
        }else{

            max = number2;
        }
        System.out.println("使用常规的if-else语句解决：");
        System.out.println("最大值是：" + max);

        //   使用三目运算符比较两个数值的大小
        System.out.println("使用三目运算符解决：");
        max = number1 > number2 ? number1  :  number2;
        System.out.println("最大值是：" + max);

    }

}


```