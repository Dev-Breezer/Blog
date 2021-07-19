# Java 数组

<br>
<br>
<br>
<br>

### 什么是数组

<br>

> + ***相同* 类型的数据 *按顺序* 组成的一种 *引用数据类型***
> + 引用数据类型：类、接口、数组

<br>
<br>

### Java 数组声明

<br>

> + 语法格式：
```java
//  数组类型[] 数组名;
int[]   myIntArray;
int myIntArray[];
char[] ch;
//  String本身是一个类，所以字符串数组也叫对象数组
String[] strArray;

```

<br>

> + C语言数据声明
```c
//  数据类型 数组名[]
int arr[];

```

<br>

### Java 数组创建

<br>

#### 语法格式一：先声明后创建

<br>

> + 数据类型[] 数组名;
> + 数据名 = new 数据类型[数据长度];

<br>

```java
//  创建一个长度为10的整型数组

int[] arr;
arr = new int[10];
```

<br>


#### 语法格式二：声明同时并创建数组  

<br>

> + 数据类型[] 数组名 = new 数据类型[数组长度];
> + **注意：长度必须指定**

<br>

```java
//  创建一个长度为10的整型数组

int[] arr = new int[10];
```

<br>

### 数组在内存中的存储

<br>

> + *数组会被分配连续的内存空间*

<br>

### 数组的初始化

<br>

> + 声明数组的同时给数组赋值，叫做数组的初始化
> + 数组长度就是初始化数组所给的元素个数

<br>

例：

```java
int[] arr = {1,2,3,4,5,6,7,8,9,10}
```

<br>

### 数组元素的引用

<br>

#### 语法格式：
> + 数组名[下标]
> + 注意：下标从0开始


<br>

![Java 数组引用](/images/Java/java数组引用.png)

<br>


### 数组长度


<br>

> + int[]a={1,2,3,4,5,6,7,8,9,10};
> + 属性length表示数组的长度，如a.length

<br>
<br>

### 一维数组的应用

<br>

```java

package JavaArray;

public class ArrayDemo {
    public static void main(String[] args){
        //  声明一个数组
        int[] intArray;

        //  声明一个字符串数组
        String strArray[];

        //  创建数组
        intArray = new int[5];
        strArray = new String[10];

        //  声明数组同时并创建,推荐这种写法
        float[] floatArray = new float[4];

        //  初始化数组
        char[] ch = {'a', 'b', 'c', 'd'};

        //  输出ch数组的长度
        System.out.println("ch数组的长度：" + ch.length);

        //  输出数组的默认值，数组的引用
        System.out.println("intArray数组第2个元素的默认值为：" + intArray[1]);
        System.out.println("strArray数组第5个元素的默认值为：" + strArray[5]);
        System.out.println("floatArray数组的最后一个元素的默认值为：" + floatArray[floatArray.length-1]);

        //  循环为整型数组赋值
        for(int i=0; i<5; i++){
            intArray[i] = i+1;
        }
        System.out.print("整型数组intArray元素为：");
        for(int i=0; i<5; i++){
            System.out.print(intArray[i] + "  ");
        }
    }
}
```

<br>
<br>

### 案例：求数组元素的累加和

<br>


```java
package JavaArray;

import java.util.Scanner;

public class ArrayDemo2 {
    public static void main(String[] args){
        //  求整型数组累加和

        //  定义整型数组
        int[] array = new int[5];
        Scanner  sc = new Scanner(System.in);
        //  从键盘接收数据，为数据元素赋值
        for(int i=0; i<array.length; i++){
            System.out.print("请输入第" + (i + 1) + "个元素：");
            array[i] = sc.nextInt();
        }
        System.out.print("数组元素的内容为：");
        for(int i = 0; i<array.length; i++){
            System.out.print(array[i] + "  ");
        }
        //  求数组元素的累加和
        int sum = 0;
        for(int i = 0; i<array.length; i++){
            sum += array[i];

        }
        System.out.println();   //  换行;
        System.out.println("数组元素的累加和：" + sum);
    }
}
```

<br>
<br>

### 案例：求数组元素的最大值

<br>

```java
package JavaArray;

public class ArrayMax {
    public static void main(String[] args){
        //  求数组元素的最大值

        int[] array = {15, 32, 83, 94, 65};
        int max=array[0];
        for(int i=1; i<array.length; i++){
            if(max < array[i]){
                max = array[i];

            }
        }
        System.out.println("max = " + max);
    }
}

```

<br>
<br>

### 增强型 for 循环

<br>

> + 增强型 for 循环又叫 foreach 循环

<br>

#### foreach 循环应用：

<br>

```java
int [] arr={1, 2, 3, 4, 5};
for(int n : arr){
    System.out.println(n)
}
```

<br>
<br>
<br>


### 案例：冒泡排序算法

<br>

```java
package JavaArray;

public class BubbleSort {
    public static void main(String[] args){
        //  算法：冒泡排序，从小到大排序

        int temp;   //    临时存放值变量
        int[] array = {34, 53, 12, 32, 56, 17};
        System.out.print("排序前的数组元素为：");
        for(int n : array){
            System.out.print(n + "  ");
        }
        System.out.println();   //  换行
        //  外重循环控制排序轮数
        for(int i=0; i<array.length-1; i++){
            //  内重循环控制循环次数
            for(int j=0; j<array.length-i-1; j++){
                if(array[j] > array[j+1]){
                    temp = array[j];
                    array[j] = array[j+1];
                    array[j+1] = temp;
                }
            }
        }
        System.out.print("从小到大排序后的数组元素为：");
        for(int n : array){
            System.out.print(n + "  ");
        }


    }
}
```

<br>
<br>
<br>

### 二维数组的应用

<br>

```java

package JavaArray;

public class TwoDimensionalityArray {
    public static void main(String[] args){
        //  二维数组的声明
        //  三种形式

        //  声明 int 类型的二维数组
        int[][] intArray;

        //  声明一个 float 类型的二维数组
        float floatArray[][];

        //  声明 double 类型的二维数组
        double[] doubleArray[];


        //  二维数组的创建

        //  创建一个三行三列的 int 类型的数组
        //  第一个中括号表示行，第二个中括号表示列
        intArray = new int[3][3];
        System.out.println("intArray 数组的第3行第2列的元素为：" + intArray[2][1]);

        //  为第2行第3个元素赋值为9
        intArray[1][2]=9;
        System.out.println("intArray 数组第2行第3个元素为：" + intArray[1][2]);

        //  声明数组的同时创建
        char[][] ch = new char[3][5];

        //  创建 float 类型的的数组时，只指定行数
        floatArray = new float[3][];

        //  错误写法
        //  floatArray = new float[][3];
        //  floatArray = new float[][];

        //  System.out.println(floatArray[0][0]);

        //  二维数组每行相当于一个一维数组，需要创建
        floatArray[0] = new float[3];   //  第一行有三列
        floatArray[1] = new float[4];   //  第二行有四列
        floatArray[2] = new float[5];   //  第三行有五列
        System.out.println(floatArray[0][0]);
        //  System.out.println(floatArray[0][3]);   数组下标越界——ArrayIndexOutOfBoundsException


        //  二维数组的初始化
        int[][] num = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        System.out.println("num 数组第1行第2列的元素为：" + num[0][1]);
        System.out.println("num 数组的行数为：" + num.length);
        System.out.println("num 数组的列数为：" + num[0].length);

        int[][] number ={{78, 79}, {65, 75, 63}, {98}};
        System.out.println("number 数组的第1行的列数为：" + number[0].length);
        System.out.println("number 数组的第2行的列数为：" + number[1].length);

        //  循环输出二维数组的内容
        System.out.println("number 数组的内容：");
        for(int i=0; i< number.length; i++){
            for(int j=0; j<number[i].length; j++){
                System.out.print(number[i][j] + "\t");
            }
            System.out.println();
        }
    }
}
```

<br>
<br>
