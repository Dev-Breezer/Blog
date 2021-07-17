# Java 逻辑运算符

<br>
<br>
<br>
<br>

### 逻辑运算符

<br>

> + 连接一个或多个条件，判断条件是否成立
> + 逻辑运算符的操作数都是布尔类型、布尔类型变量或最终结果是布尔类型的表达式

<br>

> |名称|运算符|表达式|
> |:-:|:-:|:-:|
> |与|**&&** 或 **&**|operatorNumer1 && operatorNumber2|
> |或|**&#124;&#124;** 或 **&#124;**|operatorNumer1 &#124;&#124; operatorNumber2|
> |非|**!**|!operator|




<br>
<br>
<br>

### Java 逻辑与运算符

<br>
<br>

```java
int n = 3;
//  & 运算符
boolean b = (3 > 7) & ((n++) > 2);  //  result: b = false, n = 4
```

### Java 逻辑或运算符

<br>
<br>

```java
int n = 3;
//  | 运算符
boolean b = (3 < 7) | ((n++) > 2);  //  result: b = true, n = 4
```

<br>
<br>

### 短路运算符

> **&&** 运算符，如果第一个表达式的结果直接决定最终结果，运算符右边的表达式就不再计算.  
> **||** 运算符，如果第一个表达式的结果直接决定最终结果，运算符右边的表达式就不再计算。

<br>
<br>

```java

int n = 3;

//  && 短路运算符
boolean b = (3 > 7) && ((n++) > 2);  //  result: b = false, n = 3

// || 运算符
boolean b = (3 > 7) || ((n++) > 2);  //  result: b = true, n = 3


```

<br>
<br>
<br>
<br>

# Java 逻辑非运算符

<br>
<br>

> + **!** 运算符
> + 对原条件结果取反

<br>
<br>


```java
package Java操作符;

import java.util.Scanner;

public class LogicDemo1 {
    public static void main(String[] args){

        //  输入一个整数
        System.out.println("请输入一个整数：");
        Scanner inputValue = new Scanner(System.in);
        int num = inputValue .nextInt();

        //  判断数值是否可以被3整除
        if(!(num % 3 == 0)){
            System.out.println("数值" + num +"不能被3整除");
        }
        else{
            System.out.println("数值" + num +"能被3整除");
        }
    }
}
```