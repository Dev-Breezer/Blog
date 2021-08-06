# Java 集合之 HashSet

&emsp;

    Set 是元素无序并且不可以重复的集合，被称为集
    HashSet 是 Set 的一个重要实现类，称为哈希集
    HashSet 中只允许一个 null 元素
    HashSet 具有良好的存取和查找性能


&emsp;

### Iterator (迭代器)

&emsp;

    Iterator接口可以以统一的方式对各种集合元素进行遍历

        迭代器的两个重要方法：
            hashNext() 方法检测集合中是否还有下一个元素
                如果迭代具有更多元素，则返回 true 。
            next() 返回迭代中的下一个元素。


&emsp;

### Iterator (迭代器) 遍历流程

&emsp;

    假设我们在 Iterator（迭代器）当中有三条数据（如下表所示）
    由于 HashSet 中的数据是无序，我们做出了一下的假设：

    |Python|人生苦短，我用Python|
    |C|面向过程的通用编程语言|
    |Java|面向对象的高级编程语言|

    当我们第一次调用 HashNext() 方法时，这时指针（一个不存在的箭头）指向了第一条数据（即：|Python|人生苦短，我用Python|）,这时 HashSet() 方法会判断当前所指向的数据的下一条数据是否存在， 如果有，调用 Next() 方法，得到第一条数据（即：|Python|人生苦短，我用Python|），下一次循环再去判断 HashNext() 方法，判断下一条数据是否存在，如果有，继续执行 Next() 方法，直到最后没有数据，结束循环。


&emsp;

### 在集合中插入字符串

&emsp;

```java
package com.demo.set;

import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

public class WordDemo {
    public static void main(String[] args) {
        //  需求：用HashSet存储多个表示颜色的英文单词，并输出。

        //  将英文单词添加到 HashSet 中
        Set set = new HashSet();

        //  向集合中添加元素 “" . "“red" . “black "、" yellow”和“white”

        set.add("blue");
        set.add("red");
        set.add("black");
        set.add("yellow");
        set.add("white");

        //  显示集合的内容

        System.out.println("集合中的元素为：");
        Iterator it = set.iterator();

        //  遍历迭代器循环并输出元素

        while(it.hasNext()){    //  HashNext() 返回值：有数据 true，无数据 false
            System.out.print(it.next() + ", ");
        }

        //  在集合当中插入新的数据
        //  set.add("green");

        //  TODO: 插入失败但是不会报错
        set.add("white");
        it = set.iterator();
        System.out.println("\n*************************************");
        System.out.println("插入重复元素后的输出结果为：");
        while(it.hasNext()){    //  HashNext() 返回值：有数据 true，无数据 false
            System.out.print(it.next() + ", ");
        }

    }
}

```