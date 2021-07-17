# Java变量声明  

<br>
<br>  


+ ### 整型字面值  

> + Java中有三种整数表示方法：
> + 十进制  
&emsp;&emsp; 以0开头到9的数字
> + 八进制  
&emsp;&emsp; 符号：0开头，以0开头到7的数字 
> + 十六进制  
&emsp;&emsp; 符号：0x开头,以0开头到9的数字和A-F(a-f)代表10-15的十六进制数  

> 如：123、023、0x1357、0X3c、0x1abcL  

```java

//变量声明
    

//格式：数据类型  变量名

int age ;    //声明整型变量age

/*

变量初始化

声明整型变量 childAge 
并把变量值3赋值给变量 childAage
*/

int childAge = 3; 

long count;  //声明长整型变量count
```  
<br>  
<br>  

### 变量定义  
```java
int octal = 037;    //定义整型变量存放八进制数据  
long longNumber = 0xa2cdf3ffL  //定义变量存放十六进制长整型数据
short shortNumber = 60;     //定义短整型变量存放短整型数据
byte bin = 10;  //定义变量存放byte类型数据

```


<br>  

> ### 专用术语解释
> + 赋值：使用赋值运算符 &emsp;“=”&emsp;给变量赋值
> + 变量初始化：在声明变量的同时赋值