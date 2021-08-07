# Java 集合之 Map

&emsp;

### Map

&emsp;

    Map中的数据是以键值对(key-value )的形式存储的key-value以Entry类型的对象实例存在
    可以通过key值快速地查找value
    一个映射不能包含重复的键

&emsp;

### HashMap 类

&emsp;

    基于哈希表的Map接口的实现
    允许使用null值和null键
    key值不允许重复
    HashMap中的Entry对象是无序排列的

&emsp;

### 案例

&emsp;

#### 在字典中添加内容并显示

&emsp;

```java
package com.demo.set;

import java.util.*;

public class DictionaryDemo {
    public static void main(String[] args) {

        //  定义 HashMap 对象
        //  TODO: 此处引入了泛型的概念
        Map<String, String> animal = new HashMap<>();

        System.out.println("请输入三组单词对应的注释，并存放到HashMap中");
        Scanner console = new Scanner(System.in);

        // 添加数据
        int i = 0;
        while(i < 3){
            System.out.print("请输入 Key 值（单词）：");
            String key = console.next();
            System.out.print("请输入 Value 值（注释）：");
            String value = console.next();
            animal.put(key, value);
            i++;

        }

        //  第一种：使用 Iterator（迭代器） 打印输入 value 的值
        System.out.println("************************************");
        System.out.println("使用迭代器输出所有的 value值：");
        Iterator<String> it = animal.values().iterator();
        while(it.hasNext()){
            System.out.print(it.next() + "，");
        }

        //  打印输出 key 和 value 值
        //  通过 entrySet 方法
        System.out.println("\n************************************");
        System.out.println("通过 entrySet 方法得到 key-value 值：");
        Set<Map.Entry<String, String>> entrySet =  animal.entrySet();
        for (Map.Entry<String, String> entry : entrySet) {
            System.out.print(entry.getKey() + "-");
            System.out.println(entry.getValue());


        }

    }
}
```