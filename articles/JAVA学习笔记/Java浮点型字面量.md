## Java浮点型字面值  

<br>  
<br>  

> + 浮点型字面值默认情况下表示double类型，变量值后也可添加D或者d。   
如：123.43d或123.43D。  

<br>  

> +  表示浮点型float类型的，需要在字面值后加f或F。  
如：12.5f、12.5F

<br>  

```java

package Java数据类型;

public class FloatDemo {
    public static void main(String[] args){
            // 定义一个单精度浮点型变量，存放1234.328
            float floatNumber = 1234.328f;
            System.out.println("floatNumber = " + floatNumber);
            //  定义一个双精度浮点型变量，存放8966.542
            double doubleNumber1 = 8966.542;
            System.out.println("doubleNumber1 = " + doubleNumber1);
            // int类型字面值赋值给double类型字面量
            double doubleNumber2 = 189;
            System.out.println("doubleNumber2 = " + doubleNumber2);
            // double类型变量赋值为long类型的字面值。
            double douleNumber3 = 1234L;
            System.out.print("douleNumber3 = " + douleNumber3);


    }
}



```  

<br>    
<br>  

<center><h2>总结</h2></center>  
<br>   

> +  大范围数据类型定义的变量可以赋值小范围的字面值  
> +  相同范围的数据类型的变量可以直接赋值
> +  若无需求的情况下，不能像小范围数据类型变量赋值大范围字面值（比如   int d=123.56）这样会损失字面值的精度，造成返回结果与预期的结果不符。  
> + 应该清楚不同数据类型之间自动转换的优先级，自动转换后数据的变化