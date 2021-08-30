# Java 布尔类型字面值
<br>
<br>  

> + Java 中 boolean 类型的字面值只能是 false 和 true
> + 例如 booleanValue = true;

<br> 
<br> 

# Java 字符串字面值  

<br>  

### 字符串不属于基本数据类类型，它是类。 
> + 字符串字面值表示方法: 使用双引号引起来  
&emsp;&emsp;双引号引起来的0个字符或多个字符



### 字符串字面量定义：  
### *在字符串中，空格也是一个字符*
```java
package Java数据类型;

public class StringDemo {
    public static void main(String[] args){
        // 定义一个字符串，存储Hello,java
        String stringValue1 = "Hello,java";
        // 定义一个空字符串
        String stringValue2 = "";
        //顶一个包含unicode字符的字符串
        String stringValue3 = "A\u005d\u005fB";


        System.out.println("stringValue1 = " + stringValue1);

        System.out.println("stringValue2 = " + stringValue2);

        System.out.println("stringValue3 = " + stringValue3);
    }
}


```  

<br>  
<br>  
<br>  

# Java 变量综合案例

```java
package Java数据类型;

public class VarDemo {
    public static void main(String[] args){
        //  定义两个整型变量
        //  int intVar1 = 3,intVar2 = 5;
        int intVar1,intVar2;
        intVar1 = 3;intVar2=5;
        //  定义一个汉字字符
        char charValue = '风';
        //  定义一个中文变量，但是我们不推荐这么做。
        String 风 = "清风";
        //  用科学计数法表示浮点型数据，以1.23*10的5次方为例。
        //  乘号被省略了,E(e)表示10的几次方，例如1.23E5就是1.23乘以10的5次方
        double doubleValue1 = 1.23E5;
        float  floatValue1 = 1.23e5f;
        // .2表示0.2
        double doubleValue2 = .2;

        /* 输出语句 */
        System.out.println("intVar1 = " + intVar1);
        System.out.println("intVar2 = " + intVar2);

        //  换行问题
        //  第二种换行方法 \n换行符,转义字符本质上是int类型，一下打印\t会显示27
        //System.out.print(intVar1+'\t'+intVar2 + '\n');
        //  解决方法1
        System.out.print(""+intVar1+'\t'+intVar2 + '\n');
        //  解决方法2
        System.out.print(+intVar1+""+intVar2 + '\n');
        //  第一种换行方法
        //  System.out.println();
        System.out.print(intVar1+","+intVar2);
        //  把intValue1括在双引号中输入
        System.out.println("\n\'" + intVar1 + "\'");

        System.out.println(charValue);

        System.out.println(风);
        System.out.println("doubleValue1 = " + doubleValue1);
        System.out.println("floatValue1 = " + floatValue1);
        System.out.println("doubleValue2 = " + doubleValue2);
    }

}

```