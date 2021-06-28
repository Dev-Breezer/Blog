# Java 字符型字面值


<br>  

### 字符型字面值表示

<br> 

> + 字符型字面值用单引号内单字符表示字符。
> + 如：'a'，'b'，'$' 
> + 如何定义字符型变量？ 

<br>  

```java
package Java数据类型;

public class CharDemo {
    public static void main(String[] args){
        //  定义一个变量赋值为a
        char charValue1 = 'a';
        //  定义一个变量赋值为65
        char charValue2 = 65;
        //  定义一个变量，值为65535，65535为char类型的的最大范围
        char charValue3 = 65535;
        //  定义一个变量，值为65536，65535为char类型的的最大范围,超过最大范围，需要强制转换类型，同时数据精度也会所有丢失。
        char charValue4 = (char)65536;
        System.out.println("charValue1 = " + charValue1);
        System.out.println("charValue2 = " + charValue2);
        System.out.println("charValue3 = " + charValue3);
        System.out.println("charValue4 = " + charValue4);
    }
}


```  

<br> 

### ASCII码  
<br>  

> - ASCII ( American Standard Code for  
> - Information  
> - Interchange，美国标准信息交换代码
> - 基于拉丁字母的一套电脑编码系统主要用于显示现代英语和其他西欧语言
> - 使用7位或8位二进制数组合来表示128或256种可能的字符。  
> - 7位二进制数组合一标准ASCII码  
> - 8位二进制数组合(后128位)——扩展ASCII码  

<br> 
<br>  
<br>  
<br>   
<br>  






# Unicode 编码  

<br> 

> - Unicode1码——又叫做统一码、万国码
> - Unicode编码的目标是支持世界上所有的字符集
> - Unicode表示法，在值前加前缀\u  
```java
package Java数据类型;

public class CharDemo {
    public static void main(String[] args){
            // 定义一个变量存放Unicode编码值
           char charValue5 = '\u005d';
        System.out.println("charValue5 = " + charValue5);
    }
}

```