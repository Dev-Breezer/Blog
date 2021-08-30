# Java 循环结构

<br>
<br>
<br>
<br>

### while 循环

<br>

#### 语法格式：
<br>

```java
while(循环条件){
    语句;
}
```
<br>

### 问题：打印小于5的整数
<br>

```java
package JavaFlow;

public class WhileDemo {
    public static void main(String[] args){
        //  问题：打印小于5的整数

        int n = 1;
        int sum = 0;

        while(n < 5){
            sum+=n;
            n++;
        }
        System.out.println(sum);
    }
}
```

<br>
<br>
<br>

### do-while 循环

<br>

> + do-while 循环至少执行一次
> + 循环条件后的分号不能丢 

<br>
<br>

#### 语法格式：

```java

do{

语句;

}while();

```
### 问题：打印输出小于5的整数值  

<br>
<br>

```java

package JavaFlow;

public class DoWhileDemo {
    public static void main(String[] args){
         //  问题：打印小于5的整数

        int n = 1;  //  初始化值
        int sum = 0;
        do{
            sum+=n;
            n++;    //  输出n的值
        }while(n < 5);
        System.out.println(sum);
    }
}

```
<br>
<br>
<br>

### for 循环

<br>
<br>

#### 语法格式：

<br>

```java

for(表达式1;表达式2;表达式3;){
    语句;
}

```

 <br>
 <br>

 ```java

package JavaFlow;

public class ForDemo {
    public static void main(String[] args){
        //  问题：打印小于5的整数
        int sum=0;
        for(int n = 1;n < 5; n++){
            sum += n;

        }
        System.out.println(sum);
    }
}

 ```

<br>
<br>


### 案例：
```java
package JavaFlow;

import java.util.Scanner;

public class NumberInput {
    public static void main(String[] args){
        //  问题：循环输入数字1-10并输出，如果输入0则跳出循环

        System.out.println("请输入一个1到10之间的数字");
        int number;
        Scanner inValue = new Scanner(System.in);
        while(true){

            System.out.print("请输入你要你想输入的数字：");     //  提示信息
            number = inValue.nextInt();

            //  判断输入的数值是否符合条件
            if(number >= 0 && number <= 10) {
                System.out.println("你输入的数值是：" + number);
            }else{
                System.out.println("输入的数值不合法，请重新输入!");
            }
            //  判断输入的值是否满足结束条件
            if(number == 0)break;

        }

    }
}


```

<br>
<br>

### 嵌套 while 循环应用

<br>
<br>

```java
//  嵌套形式不止一种

while(循环条件){
    ......
    while(循环条件){
        ......
    }
    ......
}

```

<br>
<br>

### 案例：
```java

package JavaFlow;

public class StarDemo {
    public static void main(String[] args){
        int m = 1; //   外循环变量
        int n; //   内循环变量
        System.out.println("输出4行4列的星号");
        //  外循环控制输出行
        while(m <= 4){
            //  内循环控制输出的星号
            n = 1;
            while(n <= m){
                System.out.print("*");
                n++;
            }
            System.out.println();   //  外循环
            m++;
        }
    }
}
```

<br>
<br>

### 案例：阶乘累加的和

<br>

```java
package JavaFlow;

public class Factorial {
    public static void main(String[] args){
        //  问题：求1!+2!+3!+......+25!

        long s, sum = 0;
        for(int i=1;i<=25;i++){
            s = 1;
            for(int j=1;j<=i;j++){
                s*=j;   //  s存放阶乘计算的结果

            }
            sum+=s;
        }
        System.out.println("1!+2!+3!+......+25! = " + sum);
    }
}


```
<br>
<br>
<br>
<br>

### break 语句

<br>

> + **结束当前循环的执行**
> + 执行完 break 语句后面的语句就不会被执行
> + 在多重循环语句中，break只向外跳一层


<br>
<br>

```java

public static void main(String[] args) {
    //  从键盘接收数据
    Scanner sc=new Scanner(System.in);int n;
    while(true){
    n=sc.nextInt();
    if(n==0)break;      //  满足条件，break跳出
    System.out.println(n);
    
    }
}

//   ——————————————————————————华丽的分割线———————————————————————————————

public static void main(Stringl] args){
    int k=O;
    for(int i=1;i<5;i++){for(int j=1;j<5;j++){
        k=i+j;
        if(j==3)break;} .
    }
    System.outprintIn("k="+k);
}
```

<br>
<br>
<br>

### continue 语句

<br>

> + **continue只能用在循环里**
> + **continue语句可以结束当前循环的执行，但是要继续下一次的循环的执行**

<br>
<br>


```java

//  求1+3+5+7+9
public static void main(String[] args) {
    int sum=O;
    for(int i=1;i<=9;i++){
        if(i%2==0){
        continue;
        sum+=i;
    }
    System.out.println("sum="+sum);
    }
}

//   ——————————————————————————华丽的分割线———————————————————————————————


    public static void main(String[] args) {
		int k=0;
		for(int i=1;i<5;i++){
		for(int j=1;j<5;j++){
			if(j%2==0)continue;
			k=k+j;
	
        }
    }
System.out.println("k="+k);

}
```