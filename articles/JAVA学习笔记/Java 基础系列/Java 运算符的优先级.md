# Java 运算符的优先级


<br>
<br>
<br>
<br>

#### 运算符优先级按照表格排列**由高到低**

<br>
<br>

> |运算|描述|
> |:-:|:-:|
> |**()**|圆括号|
> |**!**、**++**、**--**|逻辑非、自增、自减|
> |**\* **、**/**、**%**|乘法、除法、取余|
> |**+**、**-**|加法、减法|
> |**>**、**<**、**>=**、**<=**|大于、小于、小于等于、大于等于|
> |**==**、**!=**|等于、不等于|
> |**&&**|逻辑与|
> |**\|\|**|逻辑或|
> |**=**、**+=**、***=**、**/=**、**%=**、**-=**|赋值运算符、复合赋值运算符|

<br>
<br>


```java

package Java操作符;

import java.util.Scanner;

public class LeapYearDemo {
    public static  void main(String[] args){
        /*
            使用 if-else 语句判断输入的年份是否为闰年
            闰年的判断规则：能被4整除但不能被100整除的年份，或者能被400整除的年份
        */


        //  输入一个年份

        System.out.print("请输入一个年份：");
        Scanner Year = new Scanner(System.in);
        int year = Year.nextInt();

        //  判断年份

        if(year % 4 == 0 && year % 100 != 0 || year % 400 == 0){
            System.out.println(year + "是闰年");
        }else{
            System.out.println(year + "是平年");
        }
    }
}


```