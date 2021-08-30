# XML的概念与用途




+ XML的全称是EXtensible Markup Language,可扩展标记语言
+ 编写XML就是编写标签，与HTML非常类似，扩展名.xml
+ 良好的人机可读性



```xml
<employee>
	<name>张三</name>
    <age>31</age>
    <height>178</height>
</employee>
```



#### XML与HTML的比较



+ XML 与 HTML 非常相似，都是编写标签
+ XML 没有预定义标签，HTML 存在大量的预定义标签
+ XML 重在保存与传输数据，HTML 用于显示信息



#### XML的用途



+ Java 程序的配置描述文件
+ 用于保存程序产生的数据
+ 网络间的数据传输



### XML文档结构



+ 第一行必须是XML声明
  + XML声明说明XML文档的基本信息，包括版本号与字符集，必须写在XML第一行。
+ 有且只有一个根节点
+ XML标签的书写规则与HTML相同



```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- 人力资源管理系统-->
<hr>
    <employee no="3309">
        <name>张三</name>
        <age>31</age>
        <salary>4000</salary>
        <department>
            <dname>会计部</dname>
            <address>xx大厦-B103</address>
        </department>
    </employee>

    <employee no="3310">
        <name>李四</name>
        <age>23</age>
        <salary>3000</salary>
        <department>
            <dname>工程部</dname>
            <address>xx大厦-B104</address>
        </department>
    </employee>
</hr>
```



### 标签书写规则 



- 合法的标签名

  - 标签名要有意义

  - 建议使用英文，小写字母，单词之间使用 “ - ” 分割

  - 建议多级标签之间不要存在重名的情况

    ```xml
    <abc>abc</abc> ×
    <考试$>数学期末</考试$>×
    <class><class>班级</class></class> ×
    <shop-cart><item>相册</item></shop-cart> √
    
    ```

- 合理使用属性

  - 标签属性用于描述标签不可或缺的信息
  - 对标签分组或者为标签设置ld时常用属性表示

- 处理特殊字符

  - 标签体中，出现"<"、">"特殊字符，会破坏文档结构。

  - 解决方案1. 使用实体引用

    table

  - 解决方法2. 使用 CDATA 标签

    ```xml
    <exam>
        <!--无效的XML:-->
    	<question>1+4<3是否正确? </question>
        <question>3+5>8是否正确? </question>
           
        <!--修改后的XML:-->
         <question>1+4&lt;3是否正确? </question>
         <question>3+5&gt;8是否正确?</question>
    </exam>
    ```

    

- 适当的注释与缩进

  ```xml
  <!-- 错误的写法 -->
  <employee><name>张三</name><age>31</age><height>178</height></employee>
  
  <!-- 正确的写法 -->
  
  <!--员工信息-->
  <employee>
  	<name>张三</name>
      <age>31</age>
  	<--身高cm-->
  	<height>178</height>
  </employee>
  
  ```

  

- 有序的子元素

  ```xml
  <shop-cart>
      <item sn="771938" category="电器">
          <name>X空调</name>
          <pricex 2000.00</price>
          <num>1</num>
  	</item>
      
  	<item sn="890321" category="食品">
      	<name>法式面包</name>
      	<price>10.00</price>
      	<num>5</num>
  	</item>
  </shop-cart>
  
  ```

  ​	

- 特殊字符CDATA标签

  - CDATA 指的是不应由 XML 解析器进行解析的文本数据
  - 从 “<![CDATA["开始， 到"]]”结束

  ```xml
  <lesson>
      <content>
      <![CDATA[
  本节我们来学习html中a标签的使用:<body>
  <a href="index.html">首页</a></body>
  ]]>
  	</content>
  </lesson>
  
  ```

  

