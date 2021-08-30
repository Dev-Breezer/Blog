# Java 流程控制语句

<br>
<br>

### 流程控制语句包含三种形式：
<br>

> +  顺序、选择、循环

<br>

### 多重if结构

<br>

```java
if(表达式1)
    语句1;
    ...
else if(表达式2)
    语句2;
    ...
else if(表达式3)
    语句3;
    ...
else
    语句n;

```

<br>

### 例子：

<br>
<br>

```java

package JavaFlow;

import java.util.Scanner;

public class ScoreAssess {
    public static void main(String[] args){

        /*  需求描述∶
            编写一个程序，根据考试成绩，输出相应的评定信息。成绩大于等于90分，输出“优”
            成绩大于等于80分且小于90分，输出“良”成绩大于等于60分小于80分，输出“中”成绩小于60分，输出“不及格”
        */


        //  输入分数
        System.out.print("请输入你的分数：");
        Scanner score = new Scanner(System.in);
        int scoreValue = score.nextInt();

        //  判断分数大小
        if(scoreValue >= 90){
            System.out.println("优");
        }
        else if(scoreValue < 90 && scoreValue>=80){
            System.out.println("良");
        }
        else if(scoreValue >= 60 && scoreValue<80){
            System.out.println("中");
        }
        else{
            System.out.println("不及格");
        }


    }
}


```

<br>
<br>
<br>
<br>

### 嵌套if语句结构

<br>
<br>

```java

if(表达式1)
    if(表达式2)
        if(表达式3)
            语句;

else
    语句;
```

<br>
<br>

### 例子：

<br>

```java

package JavaFlow;

import java.util.Scanner;

public class IntCompare {
    public static void main(String[] args){
        /*
            从键盘输入两个整数，经过判断输出他1的大参(大于，小与、等于)
        */

        //  输入数值
        System.out.print("请输入两个数值(空格分隔)：");
        Scanner value = new Scanner(System.in);
        int num1 = value.nextInt();
        int num2 = value.nextInt();


        //  判断num1和num2是否相等
        if(num1 != num2){

            if(num1 > num2){
                System.out.println("大于");
            }
            else{
                System.out.println("小于");
            }

        }
        else{
            System.out.println("等于");
        }


    }
}


```


<br>
<br>
<br>
<br>

# Java switch结构语句 

<br>

### if 和 switch 的区别

<br>

#### if 结构：

> + 判断条件是布尔类型
> + 判断条件是一个范围

<br>
<br>

#### switch 结构：

> + 判断条件是常量值

<br>

```java
switch(表达式){
case常量表达式1:
    语句1; 
    break;
case常量表达式2:
    语句2;
    break;
default:
    语句3;
}
```

<br>
<br>
<br>

```java

package JavaFlow;

import java.util.Locale;
import java.util.Scanner;

public class WeekDemo<num> {
    public static void main(String[] args){
        /*
        从键盘输入1-7之间的任意数字，分别输出对应的信息。
        1-星期一
        2-星期二
        3-星期三
        4-星期四
        5-星期五
        6-星期六
        7-星期日
        */

        //  输入数值
        System.out.print("请输入星期的英文单词：");
        Scanner weekday = new Scanner(System.in);
        String week = weekday.next();
        week = week.toUpperCase();  //  把字符串全部转换成大写

        // 判断输入的数值是否合法并判断星期几
            switch(week){
                case "MONDAY":
                    System.out.println("星期一");
                    break;
                case "TUESDAY":
                    System.out.println("星期二");
                    break;
                case "WEDNESDAY":
                    System.out.println("星期三");
                    break;
                case "THURSDAY":
                    System.out.println("星期四");
                    break;
                case "FRIDAY":
                    System.out.println("星期五");
                    break;
                case "SATURDAY":
                    System.out.println("星期六");
                    break;
                case "SUNDAY":
                    System.out.println("星期天");
                    break;
                default:
                    System.out.println("输入的数值不合法");
                    break;
            }
        }
    }
```