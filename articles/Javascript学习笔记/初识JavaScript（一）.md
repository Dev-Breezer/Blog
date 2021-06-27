# 初识JavaScript（一）

## 一、在学习JavaScript之前，有必要知道一下几点

> ### 1.JavaScript是一门面向Web的编程语言
> ### 2.JavaScript不等于Java
> ### 3.JavaScript是一门动态类型(弱类型)的编程语言

---

## 二、JavaScript的名字和版本

> <a href="https://baike.baidu.com/item/JavaScript/321142?fr=aladdin">JavaScript的名字和版本--来自百度百科</a>

## Javascript快速概览

+ JavaScript的注释

```Javascript
//这是一个单行注释

/*这是一个多行注释*/
```

+ 声明一个变量

```Javascript
//声明一个变量
var number;
//接下来是一个赋值操作
var number=2;
/*****************************************
 *
 *你没有看错，在这里等号就是一个赋值运算符
 *
 ****************************************/

```

+ Javascript拥有多种不同数据类型

```Javascript
var number = 2;         //这是一个数字
var float = 0.1;        //这也是一个数字，但它和上面的不同，我们称它为实数，它和上面的整数共用一种数据类型，我们称它们为数字型
var str = "Hello,World";    //这是一个由双引号构成的字符串
var string = 'Hello,World';     //这是一个由单引号构成的字符串
var boolean = true;         // 这是一个布尔值
var boole = false;          // 这是另一个布尔值
var none = null;            //这是一个很特殊的值 意为空
var no = undefined;         //它和null很相似
```

+ JavaScript最重要的是类型和对象
+ 对象是Key/Value的集合，这一点和Python种Dict【字典】数据类型很像

```JavaScript

var object = {
    objectName: "JavaScript",
    fat: true
};

/**********************************
 * {-表示对象集合的开始
 * 属性objectName的值是Javascript
 * 属性fat的值是true
 * }-表示对象集合的结束
 **********************************/

```

----

### Python中的Dict数据类型展示

```python

# Dict数据类型

value={"id":"1", "name":"Breezer"}

```

---

+ 访问、创建、对象属性

```JavaScript

var object = {
    objectName: "JavaScript",
    fat: true
    
object.objectName;       //使用“.”访问对象属性  result: "JavaScript"
object[fat];             //使用“[]”访问对象属性  result: true

object.author = "Dev-Breezer";  //通过赋值创建一个新属性
objct.contents = {};     //{}是一个空对象，所以contents是一个空对象 
```

+ JavaScript中的数组

```JavaScript

var array=[1,2,3,4,5];       //创建了一个数组，面向过程风格创建数组
var array = new Array(1,2,3,4,5);   //另一种创建方式， 面向对象风格创建数组

array[0];                    //访问数组中的元素 result: 1
array.length;                //获取数组中的元素个数，result: 5
array[array.length - 1];     //获取数组最后一个元素 result: 5
array[5] = 16;               //通过赋值添加新元素
array[5] = 32;               //通过赋值改变以后元素

/********************************************************************
 *
 * length是一个由JavaScript内置的函数,可以用它来获取字符串、数组的长度
 *
 ********************************************************************/
```

+ JavaScript运算符

```Javascript
//下面是常见的JavaScript运算符

3+2;        //result: 5 加法
3-2;        //result: 1 减法
3*2;        //result: 6 乘法
3/2;        //result: 1.5 除法
"3"+"2";    //result: "32" 字符串拼接
 
 //复合运算符
 
 var count = 0; //定义一个变量
 count++;       //自增1
 count--;       //自减1
 count += 2;    //自增2: 和“count = count + 2”写法一样
 count *= 3;    //自乘3: 和“count = count * 3”写法一样

```

+ 比较运算符

```JavaScript
var n = 3, y=4;     //普通赋值,等号是赋值运算符，要和== === 相区分
var [b,z] = [6, 9];  //解构赋值
n == y;     //result: false 比较值是否相等
n != y;     //result: true  比较值是否不相等
n > y;      //result: false 比较值是否大于另一个值
n >= y;     //result: false 比较值是否大于等于另一个值
n < y;      //result: true  比较值是否小于另一个值
n <= y;     //result: true  比较值是否小于等于另一个值
"hello" > "world";     //result: false  比较一个字符串是否大于另一个字符串
"h" == "H";      //result: false  比较两个字符串是否相等
```

+ JavaScript逻辑运算符

```JavaScript
var n = 3, y=4;
(n == 3) && (y == 4);     //result: true  两个比较都为真，&& 相当于 and，表示“与”
(n > 3) || (y < 4);      //result: false 两个比较都为假，|| 相当于 or，表示“或”
!(n == y);      //取反
```
