# 初识JavaScript（二）

+ 自定义函数

```JavaScript
//函数是带有一段参数的javascrpt代码，可以多次调用，这也是把功能封装成函数的主要原因之一

//加法-这是一个简单的单向值传递自定义函数
function plus(num){   //函数声明 num是一个形参，形式参数
  return num+1;       //返回结果 result: 9
}
plus(8);  //函数调用，此处的8是一个实参=>实际参数

//乘法 - 这是一个函数表达式,把一个函数赋给square变量，也可以叫做匿名函数
var square = function(num){       
  return num*num;     
}
square(8);              //返回结果 result: 64
square(plus(8));    //在一个表达式种调用两个函数 result: 81
```
