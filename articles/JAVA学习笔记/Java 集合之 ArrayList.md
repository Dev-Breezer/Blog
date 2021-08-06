# Java 集合之 ArrayList

&emsp;

### 集合概述与应用场景

&emsp;

    Java中的集合是工具类，可以存储任意数量的具有共同属性的对象。
    
    应用场景:
        
        无法预测存储数据的数量时我们使用集合
        同时存储具有一对一关系的数据
        需要进行数据的增删
        数据重复问题


&emsp;

### 集合框架的体系结构

&emsp;

    集合框架分类两类：

    Colleciton（接口）：存储类的对象
        三个子接口：
            List - 序列（列表）
                实现类：ArrayList（可以看作长度动态增长的数组）
            Queue - 队列
                实现类：LinkedList（同时实现了 List接口，表示链表的内容）
                List 和 Queue 中存放的数据要求是有序的并且允许重复
            Set - 集合
                实现类：HashSet
                Set 中存放的数据要求是无序的并且不允许重复
             
    Map：以键值对的形式存储信息
        实现类：HashMap（哈希表，以键值对[key,value]存储）
    

&emsp;

### List 概述

&emsp;

#### List（列表）

&emsp;

    List 是元素有序并且可以重复的集合，称为序列
    List 可以精确的控制每个元素的插入位置，或删除某个位置的元素
    List 的两个主要实现类是 ArrayList 和 LinkedList


&emsp;

#### ArrayList

&emsp;

    ArrayList底层是由数组实现的
    动态增长，以满足应用程序的需求
    在列表尾部插入或删除数据非常有效（如果在 ArrayList 中间插入或删除数组，会进行大量的数据复制，资源消耗很高）
    ArrayList 更适合查找和更新元素
    ArrayList 中的元素可以为 null 值

&emsp;

### 案例——在 List 中存储并操作字符串信息：

&emsp;

```java
package com.demo.set;

import java.util.ArrayList;

public class ListDemo1 {
    public static void main(String[] args) {
        //  案例:用ArrayList存储编程语言的名称，并输出。

        ArrayList list = new ArrayList();

        //  使用 add(E,e) 方法添加元素
        list.add("Java");
        list.add("C");
        list.add("C++");
        list.add("Go");
        list.add("Swift");

        //  输出列表中的元素个数 使用 size() 方法
        System.out.println("list 元素个数为：" + list.size());

        //   遍历输出所有的编程语言
        System.out.println("**************使用 for 语句输出 list 元素*******************");
        for(int i=0 ; i<list.size() ; i++){
            System.out.print(list.get(i) + ", \n");

        }

        //  TODO: 不知道是否推荐这种写法
        System.out.println("***************使用foreach语句输出 list 元素******************");
        for(Object n : list){
            System.out.println(n);
        }

        //  移除 C++ 、Swift 使用 remove() 方法移除

        /*
        * 1. 使用 remove(int index) 方法 返回值：boolean 类型，true：元素存在；false：元素不存在
        * 2. 使用 remove(Object o) 返回值：boolean 类型，true：元素存在；false：元素不存在
        */

        System.out.println("\n移除 C++ 、Swift 后的元素为：");

        list.remove(2);
        list.remove("Go");

        for(Object n : list){
            System.out.println("\t" + n);
        }
    }
}
```

&emsp;

### 案例：公告管理

&emsp;

#### **公告的添加和显示**

&emsp;

    需求
        -公告的添加和显示
        -在指定位置处插入公告
        -删除公告
        -修改公告
    公告类属性
        -编号id
        -标题title
        -创建人creator
        -创建时间createTime
    公告类方法
        -构造方法
        -获取和设置属性值的方法


&emsp;

```java

package com.demo.set;

import java.util.Date;

public class Notice {

    private int id;    // 编号
    private String title;  // 标题
    private String creator;    // 创建人
    private Date createTime;    // 创建时间

    public Notice(int id, String title, String creator, Date createTime) {
        this.id = id;
        this.title = title;
        this.creator = creator;
        this.createTime = createTime;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getCreator() {
        return creator;
    }

    public void setCreator(String creator) {
        this.creator = creator;
    }

    public Date getCreateTime() {
        return createTime;
    }

    public void setCreateTime(Date createTime) {
        this.createTime = createTime;
    }
}
```

&emsp;

```java
package com.demo.set;

import java.util.ArrayList;
import java.util.Date;

public class NoticeTest {
    public static void main(String[] args) {

        //  创建 Notice 类对象，生成三条公告

        Notice notice1 = new Notice(1, "欢迎来到 Java 的世界", "管理员", new Date());
        Notice notice2 = new Notice(2, "Java 是一门面向对象的高级编程语言", "软件开发工程师", new Date());
        Notice notice3 = new Notice(3, "请使用 JUnit测试 你的程序", "软件测试工程师", new Date());

        //  添加公告

        ArrayList noticeList = new ArrayList();
        noticeList.add(notice1);
        noticeList.add(notice2);
        noticeList.add(notice3);

        System.out.println("******************************");
        //  在第一条公告后面添加一条新公告
        Notice notice4 = new Notice(4, "C++ 必学", "管理员", new Date());
        noticeList.add(1, notice4);


        //  显示公告

        System.out.println("公告内容为：");
        for (int i = 0; i < noticeList.size(); i++) {

            System.out.println(i + 1 + "：" + ((Notice) (noticeList.get(i))).getTitle());

        }

        //  删除请使用 JUnit测试 你的程序公告
        System.out.println("******************************");
        noticeList.remove(2);

        //  删除并显示公告

        System.out.println("删除公告后内容为：");
        for (int i = 0; i < noticeList.size(); i++) {

            System.out.println(i + 1 + "：" + ((Notice) (noticeList.get(i))).getTitle());
        }

        //  将第二条公告改为计算机组成原理
        System.out.println("******************************");
        //  修改第二条公告中 title 的值
        notice2.setTitle("计算机组成原理");
        noticeList.set(2, notice2);     //  set(int index, E element)

        //  修改并显示公告

        System.out.println("修改公告后内容为：");
        for (int i = 0; i < noticeList.size(); i++) {

            System.out.println(i + 1 + "：" + ((Notice) (noticeList.get(i))).getTitle());
        }


    }
}
```



