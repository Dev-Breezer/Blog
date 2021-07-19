# Java 方法

<br>

### 什么是方法

<br>

> + 方法就是用解决一类问题的代码的有序组合，是一个功能模块

<br>
<br>


### 方法声明

<br>

> + 语法格式：
<br>
```java
访问修饰符 返回类型 方法名(参数列表){
    方法体
}
```

<br>
<br>
<br>

### 方法分类

<br>

#### 根据方法是否带参数、是否返回值，可分为四类:

<br>

> + **无参无返回值 方法**
> + **无参带返回值 方法**  
> + **带参无返回值 方法**  
> + **带参带返回值 方法**  

<br>

### **无参无返回值方法**

<br>

```java
package JavaMethod;

public class MethodDemo1 {
    public void printStar(){
        //  打印输出*号的方法
        System.out.println("*************************************");
    }

    public static void main(String[] args){
        //  不用方法的方式
        System.out.println("*************************************");
        System.out.println("欢迎来到 Java 的世界!");
        System.out.println("*************************************");

        //  使用方法的方式
        //  创建一个 MethodDemo1 类的对象 star
        MethodDemo1 star = new MethodDemo1();
        //  使用对象名.方法名()去调用方法
        star.printStar();
        System.out.println("欢迎来到 Java 的世界!");
        star.printStar();
    }

}
```

<br>

### **无参有返回值方法**

<br>

```java
package JavaMethod;

public class Rectangle {

    //  求长方形面积的方法
    public int area(){
        int length = 10;
        int width = 5;
        int getArea = length * width;
        return getArea;    //  返回语句，有一个返回值，类型为int
    }

    public static void main(String[] args){
        Rectangle rc = new Rectangle();
        int area = rc.area();
        System.out.println("面积：" + area);
    }
}


```

<br>

### **有参无返回值方法**

<br>

```java
package JavaMethod;

public class MaxDemo {

    //  求最大值的方法
    public void max(float numValue1, float numValue2){
        float max;
        if(numValue1 > numValue2){
            max = numValue1;
        }
        else{
            max = numValue2;
        }
        System.out.println(numValue1 + "和" + numValue2 + "的最大值是：" + max);
    }

    public static void main(String[] args){

        MaxDemo MaxDemo = new MaxDemo();
        int a = 5, b = 3;
        MaxDemo.max(3,2);
        MaxDemo.max(a,b);

    }
}
```

<br>

### **有参有返回值方法（一）**

<br>

```java
 package JavaMethod;

public class Factorial {

    //  方法不能嵌套定义
    //  求阶乘的方法
    public int factorial(int n){
        int s = 1;
        for(int i=1; i<=n; i++){
            s*=i;
        }
        return s;
    }

    public static void main(String[] args){

            Factorial fac = new Factorial();
            int sum = fac.factorial(3);
            System.out.println("3 != " + sum);
            int s = 0;
            //  求1!+2!+3!+4!+5!
            for(int i=1; i<=5; i++){
                sum = fac.factorial(i);
                s+=sum;
            }
            System.out.println("1!+2!+3!+4!+5! = " +s);
    }
}
```

<br>

### **数组作为方法参数（二）**

<br>

```java
package JavaArray;

import JavaMethod.ArrayMethod;

import java.util.Scanner;

public class ArraySearch {
    //  例:查找数组元素的值

    //  查找数组元素的值的方法
    public boolean search(int n,int[] arr){
        boolean flag = false;   //  默认：未找到
        for(int i=0; i<arr.length; i++){
            if(arr[i] == n){
                flag = true;    //  已找到元素值
                break;
            }
        }
        return flag;
    }
    public static void main(String[] args){

        int[] array={23,45,30,50,60,98};
        System.out.print("请输入要查找的数据：");

        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();

        ArraySearch as = new ArraySearch();
        boolean flag= as.search(num,array);

        if(flag){
            System.out.println("找到了！");
        }
        else{
            System.out.println("未找到！");
        }
    }
}
```

<br>

### **方法重载**

<br>

> + **方法名相同，参数列表不同**&emsp;的方法我们叫方法重载 
> + 可以是**数据类型不同**、可以是**参数长度不同**

<br>

```java

定义三个方法，实现int、double和数组类型和的问题

```

<br>

### **参数传递问题——基本数据类型的传值**

<br>

> + 基本数据类的传值只会进行值传递（不会指向同一片内存空间），其值的改变不会影响主方法中的值

<br>

```java
package JavaMethod;

public class ExchangeNumber {
    //  对两个变量的值进行交换并打印输出

    //  值交换方法
    public void swap(int a, int b){
        int temp;
        System.out.println("交换前：a = " + a + ",b = " + b);
        temp = a; a = b; b = temp;
        System.out.println("交换后：a = " + a + ",b = " + b);
    }

    public void swapTest(){
        int m =4, n=5;
        System.out.println("交换前：m = " + m + ",n = " + n);
        swap(m, n);
        System.out.println("交换后：m = " + m + ",n = " + n);
    }

    public static void main(String[] args){

        ExchangeNumber en = new ExchangeNumber();
        en.swapTest();
    }
}
```

<br>

```java
package JavaMethod;

public class Exchange {
    public void add(int n){
        n++;
        System.out.println("方法中 n = " + n);
    }

    public static void main(String[] args){
         int n = 10;
         System.out.println("方法调用前 n = " + n);
         Exchange ec = new Exchange();
         ec.add(n);
        System.out.println("方法调用后 n = " + n);
    }
}
```

<br>

### **参数传递问题——数组作为方法参数的传值问题**

<br>

> + 数据作为方法参数传值会指向同一片连续的内存空间，主方法中的值会受到影响

<br>

```java
package JavaMethod;

public class ArrayDemo {
    //  定义一个修改某个数组元素值的方法
    public void updateArray(int[] arr){
        arr[3] = 15;
        System.out.println("数据 arr 的元素为：");
        for(int n : arr){
            System.out.print(n + "  ");
        }
        System.out.println();   //  换行

    }
    public static void main(String[] args){
        ArrayDemo ad = new ArrayDemo();
        int[] array = {1, 2, 3, 4, 5};
        System.out.println("方法调用前 array 的数组元素为：");
        for(int n : array){
            System.out.print(n + "  ");
        }
        System.out.println();
        ad.updateArray(array);
        System.out.println("方法调用后 array 的数组元素为：");
        for(int n : array){
            System.out.print(n + "  ");
        }
    }
}
```

<br>

### **可变参数 (也可以叫 可变元参数) 列表**

<br>

> + 可变参数：参数的数量是不确定的，可以随时变化
> + 参数列表中如果有两个以上的参数，可变参数要放在最后,因为可变参数必须放在参数列表最后，所以一个方法中只能有一个可变参数
> + 数组作为参数传递，不能加多个值传递给数组
> + 数组可以向可变参数传值，可变参数列表不能向数组传值

<br>

#### 可变参数(可变元参数)的形式

<br>

```java
public void sum(int... n){}
```
<br>

```java
package JavaMethod;

public class VariableParameterSearch {
    //  查找
    public void search(int n, int... a){
        boolean flag = false;
        for(int v:a){
            if(v == n){
                flag = true; break;
            }
        }
        if(flag){
            System.out.println("找到了！" + n);
        }
        else{
            System.out.println("未找到了！" + n);
        }

    }

    /*
    public void search(int n, int[] array){}
    语句与 public void search(int n, int... a){}
    重复定义 int[] array 和 int... a 等价，所以不是方法重载
    */

    public static void main(String[] args){
        VariableParameterSearch vps = new VariableParameterSearch();
        vps.search(3, 1, 2, 3, 4, 5);
        int[] arr = {1, 2, 3, 4, 5};
        vps.search(0, arr);
    }
}

```

<br>

### **可变参数 (也可以叫 可变元参数) 列表作为方法参数的重载问题**

<br>

> + 

<br>

```java
public void sum(int... n){}
```