# Java 自增自减运算符

<br>
<br>

> + **++** 对变量自身的值 + 1  
> + **--**对变量自身的值 - 1

<br>
<br>

>|表达式|执行方式|结果（num1=2)|  
>|:-:|:-:|:-:|
>|num2 = ++ num1|num1 = num1 + 1;  num2 = num1|num1=3;  num2=3;|
>|num2 = num1 ++|num2 = num1; num1 = num1 + 1|num1 = 2; num2 = 1;|
>|num2 = -- num1|num1 = num1 - 1; num2 = num1|num1 = 1; num2 = 1;|
>|num2 = num1 --|num2 = num1; num1 = num1 - 1|num1 = 1; num2 = 2;|

<br>
<br>
<br>
<br>


```java

package Java操作符;

public class AutoIncreReduOperator {
    public static void main(String[] args){

        // autoIn ++
        int autoIn = 6;
        int autoIncResult = (autoIn++) + 2;
        System.out.println("自增前：");
        System.out.println("autoIn=" + autoIn + ", autoIncResult=" + autoIncResult);

        //  ++ autoIn
        autoIn = 6;
        autoIncResult = (++ autoIn) + 2;
        System.out.println("autoIn=" + autoIn + ", autoIncResult=" + autoIncResult);

        //  autoRedu --
        int autoRedu = 6;
        int autoReduResult = (autoRedu --) +2;
        System.out.println("自减后：");
        System.out.println("autoRedu=" + autoRedu + ", autoReduResult=" + autoReduResult);

        //  -- autoRedu
        autoRedu = 6;
        autoReduResult = (-- autoRedu) +2;
        System.out.println("autoRedu=" + autoRedu + ", autoReduResult=" + autoReduResult);

    }
}


```

<br>
<br>
<br>
<br>

# Java 赋值运算符

<br>

> + 格式：变量 = 表达式;
> + 赋值运算符是自右至左运算  

例子：
```java
int n = 3;      //  将3赋值给变量n
double doubleValue1 = 123.569;
double  doubleValue2 = doubleValue1;

//  错误的写法
double d; 
123.569 = d;
```


<br>
<br>
<br>
<br>

# Java 复合赋值运算符 

<br>
<br>

> |运算符|表达式|计算|结果（x=10）|  
> |:-:|:-:|:-:|:-:|
> |+=|x += 5|x = x + 5 |15|
> |-=|x -= 5|x = x - 5|10|
> |*=|x *= 5|x = x * 5|50|
> |/=|x /= 5|x = x / 5|2|
> |%=|x %= 5|x = x % 5|0|

<br>
<br>
<br>
<br>

# Java 关系运算符

<br>

> + 比较两个值的大小、是否相等的操作符我们叫做关系运算符
> + 返回值是Boolean（true 和 false)


<br>
<br>

> |运算符|名称|表达式|结果|
> |:-:|:-:|:-:|:-:|
> |>|大于|5 > 3|true|
> |<|大于|5 > 3|false|
> |>=|大于等于|5 >= 3|true|
> |<=|小于等于|5 <= 3|false|
> |==|等于|5 == 3|false|
> |!=|不等于|5 != 3|true|

<br>
<br>

> + 例：
> + 'A'>'B' 结果为 false，比较的是字符的 ASCII 值
> + 5 != 6  结果为 true，比较数值是否相等
> + true == false 结果为 false
> + float floatValue = 5.0f; long longValue = 5; floatValue == longValue;   结果为true,浮点型与整数进行比较，值相等就返回true


<br>
<br>

```java

package Java操作符;

public class RelateOperator {
    public static void main(String[] args){

        //  大于
        int intValue1 = 3, intValue2 = 5;
        System.out.println("大于：");
        System.out.println("intValue1 > intValue2 = " + (intValue1 > intValue2));

        //  小于
        System.out.println("小于：");
        System.out.println("intValue1 < intValue2 = " + (intValue1 < intValue2));

        //  大于等于
        System.out.println("大于等于：");
        System.out.println("intValue1 >= intValue2 = " + (intValue1 >= intValue2));


        //  小于等于
        System.out.println("小于等于：");
        System.out.println("intValue1 <= intValue2 = " + (intValue1 <= intValue2));

        // 等于
        System.out.println("等于：");
        System.out.println("intValue1 = intValue2 = " + (intValue1 == intValue2));

        // 不等于
        System.out.println("不等于：");
        System.out.println("intValue1 != intValue2 = " + (intValue1 != intValue2));
    }
}


```