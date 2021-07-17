# Java 数据类型转换

<br>
<br>

### 类型转换分为自动转换类型和强制转换类型 

<br>

```java 
long  n = 253;
// 定义一个变量名为ch的char类型变量，这里给出的值65536已经超出了char类型的范围，会报错。所以需要进行强制转换
char ch = 65536;
// 强制转换后,需要注意的是强制类型转换会引起数据丢失。
char ch = (char)65536;
```

<br>
<br>

> + 自动类型转换只能是低->高（比如int转long,float转double）

<br>
<br>

### 自动类型转换顺序

<br> 

> + 自动类型转换又叫隐式类型转换

<br>

> + 实线：无信息丢失的数据类型转换  
> + 虚线：可能在转换时，出现精度丢失

<br>


![Java 数据类型](/images/Java/java数据类型2.png)


<br>
<br>

### 强制类型转换

<br>
<br>

> + 如果一个数据类型（比如long类型）表示范围比另一个数据类类型（比如int类型）大,需要强制转换。

例子： 
```java
double doubleValue = 123.4;

// 强制数据类型转换格式：（数据类型）变量
float floatValue = (float)doubleValue;
```

<br>
<br>


###  数据类型转换案例


<br>
<br>


```java
package Java数据类型;

public class TypeExchange {
    public static void main(String[] args){
            //  char <--> int char类型范围0~65535
        char charValue1 = (char)65536;
        int intValue1;
        intValue1 = charValue1;     //隐式类型转换（数据类自动转换）
        charValue1 = (char)intValue1;

            //  int、long <--> float、double
        int intValue2 = 100;
        long longValue1 = intValue2;
        intValue2 = (int)longValue1;
        float floatValue1 = 100000000000000L;

        float floatValue2 = 1869789575347L;

        System.out.println("floatValue1=" + floatValue1);
        System.out.println("floatValue2=" + floatValue2);
    }
}

```