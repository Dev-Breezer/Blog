# Java if选择结构语句

<br>
<br>
<br>

### if语句

> + if语句——条件选择结构语句
> + 根据不同条件去执行不同的操作

```java

package Java操作符;

public class ConditionDemo {
    public static void main(String[] args) {
        // 例：商场打折，如果两件商品的价格大于100则减20，把原价和折后价格分别输出。

        // 定义两个变量，分别存放两件衣服的价格
        double price1, price2;
        price1 = 80;
        price2 = 50;

        // 计算商品总价
        double sum = price1 + price2;

        // 判断两件商品的总价是否大于100
        System.out.println("原价：" + sum);
        if (sum >= 100) {
            sum -= 20;
        }
        System.out.println("折扣后价格" + sum);


    }
}


```

<br>
<br>
<br>
<br>
<br>


# Java if-else条件结构语句


<br>
<br>


### if-else语句 

<br>

例子：
```java

package Java操作符;

import java.util.Scanner;

public class ConditionDemo2 {
    public static void main(String[] args){

        //  int num = 6;
        //  从键盘接收数据，打印一条输出语句
        System.out.println("请输入一个整数：");
        Scanner inputValue = new Scanner(System.in);
        int num = inputValue.nextInt();
        if(num % 2==0){
            System.out.println("数值" + num + "是一个偶数");
        }
        else{
            System.out.println("数值" + num + "是一个奇数");
        }
    }
}

```