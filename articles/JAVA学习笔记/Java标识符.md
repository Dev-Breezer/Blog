# Java 标识符  

+ 关键字
+ 变量
+ 数据类类型
+ 类型转换
+ 常量  

<br>
<br>  

### 1.标识符的命名规则 
<br>

> + .标识符可以由字母、数字、下划线(_)和美元符($)组成,不能以数字开头 
> + 严格区分大小写 
> + 标识符不能是Java关键字和保留字 
> + 标识符命名应该做到见名知义

<br>
<br>

### 2.关键字  
<br> 



> |abstract|boolean|break|byte|case|catch|  
> | :-: | :-: | :-: | :-: | :-: | :-: |
> |char|class|continue|default|do|double|  
> |else|extends|false|final|finally|float|  
> |for|if|implements|import|native|int|
> |interface|long|instanceof|new|null|package|
> |private|protected|public|return|short|static|
> |super|switch|synchronized|this|throw|throws|
> |transient|true|try|void|volatile|while|  

<br>

### 3.变量

<br>
(1)、什么是变量  
<br> 
<br> 

> + 变量是存储数据的场所  
> + 变量是存储在内存中的  
> + 变量包含三个元素：变量类型、变量名和变量值。 

<br>  
<br>

(2)、变量的命名规则  

> + 满足标识符命名规则 
> + 符号驼峰命名规范  
&emsp;&emsp; 如果变量由一个单词组成,则全部小写。  
&emsp;&emsp; 如果变量由多个单词组成,则全部第一个单词全部小写，第二个单词首字母大写其余全部小写   
> + 变量定义尽量简单，应该做到见名知意  
> + 变量名的长度没有限制，但上一条变量命名规则已经做出的限制，即：变量命名尽量简单。所以变量长度不一过长  

<br>  

```java
//关于驼峰命名法

// defined age variable

int age = 20;

// defined student name variable

char stuName = 'Breezer';
```  
<br>  
(3)、类的命名规则 
<br> 
<br> 

> + 满足Pascal（帕斯卡）命名法规范  

<br>

```java
// 关于Pascal（帕斯卡）命名法规范


//单个单词作为类名

class Students{
    
    // code block
}


// 多个单词作为类名

class AppMain{

    // code block
} 

```


