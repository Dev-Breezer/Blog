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

  

### XML 语义约束

+ XML文档结构正常，但不可能是有效的

  + 例如，员工当但XML重绝不允许出现 “植物品种 ”标签。XML语义约束就是用于规定XML文档中允许出现哪些元素。

+ XML 语义约束由两种定义方式：DTD与XML Schema

  + DTD（Document Type Definition，文档类型定义）是一种简单易明的语义约束方式。
  + DTD文件扩展名为.dtd

  ```dtd
  <!ELEMENT hr(employee+)>
  <!ELEMENT employee (name,age,salary,department)><!ATTLIST employee no CDATA"">
  <!ELEMENT name (#PCDATA)>
  ```

+ DTD 定义节点

  + 利用DTD中的 <!ELEMENT> 标签，我们可以定义XML文档中允许出现的节点及数量，以hr.xml为例。

    ```dtd
    <!--定义hr节点只允许出现1个employee子节点-->
    <!ELEMENT hr(employee)>
    
    <!--employee 节点下必须包含以下四个节点，且按顺序出现-->
    <!ELEMENT employee(name, age ,salary,department)>
    
    <!--定于name标签体  只能是文本，#PCDATA代表文本元素-->
    <!ELEMENT name(#PCDATA)>
    ```

+ DTD 定义节点数量

  + 如某个子节点需要多次重复出现，则需要在子节点后增加相应的描述符

    ```dtd
    <!--hr节点最少出现1个employee子节点-->
    <!ELEMENT hr(employee+)>
    
    <!--hr节点下可出现0..n个employee字节点-->
    <!ELEMENT hr(employee*)>
    
    <!--hr节点下最多出现1个employee字节点-->
    <!ELEMENT hr(employee?)>
    ```

+ XML 引用 DTD 文件

  + 在 XML 中使用 <!DOCTYPE> 标签来引用 DTD 文件

    ```xml
    <!--
    书写格式：
    <!DOCTYPE 根节点 SYSTEM "dtd文件路径">
    -->
    
    <!--示例-->
    <!DOCTYPE hr SYSTEM "hr.dtd">



### 案例：



```dtd
<?xml version="1.0" encoding="utf-8" ?>
<!ELEMENT hr (employee+)>
<!ELEMENT employee (name, age, salary, department)>
<!ATTLIST employee no CDATA "">
<!ELEMENT name (#PCDATA)>
<!ELEMENT age (#PCDATA)>
<!ELEMENT salary (#PCDATA)>
<!ELEMENT department (dname, address)>
<!ELEMENT dname (#PCDATA)>
<!ELEMENT address (#PCDATA)>
```



```xml
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE hr SYSTEM "hr.dtd">
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



### XML Schema



+ XML Schema 比 DTD 更为复杂，提供了更多功能
+ XML Schema 提供了数据类型、格式限定、数据范围等特性
+ XML Schema 是 W3C 标准



```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- 人力资源管理系统-->
<hr xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="hr.xsd">
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



```schema
<?xml version="1.0" encoding="UTF-8" ?>
<schema xmlns="http://www.w3.org/2001/XMLSchema">
    <element name="hr">
        <!--   complexType 标签含义时复杂节点，包含子节点时必须使用这个标签     -->
        <complexType>
            <sequence>
                <element name="employee">
                    <complexType>
                        <sequence>
                            <element name="name" type="string"></element>
                            <element name="age" type="integer"></element>
                            <element name="salary" type="integer"></element>
                            <element name="department">
                                <complexType>
                                    <sequence>
                                        <element name="dname" type="string"></element>
                                        <element name="address" type="string"></element>
                                    </sequence>
                                </complexType>
                            </element>
                        </sequence>
                        <attribute name="no" type="string" use="required"></attribute>
                    </complexType>
                </element>
            </sequence>
        </complexType>
    </element>
</schema>
```



### DOM 文档对象模型



+ DOM(Document Object Model)定义了访问和操作XML文档的标准方法，DOM把XML文档作为树结构来查看，能够通过DOM树来读写所有元素。



### DOM4j



+ Dom4j是一个易用的、开源的库，用于解析XML。它应用于Java平台，具有性能优异、功能强大和极其易使用的特点
+ Dom4j将XML视为Document对象
+ XML标签被Dom4j定义为Element对象



### XPath 路径表达式

+ XPath 路径表达式是 XML 文档中查找数据的语言
+ 掌握 XPath 可以极大的提高在提取数据时的开发效率
+ 学习 XPath 本质就是掌握各种形式表达式的使用技巧



+ 最常用的基本的表达式

  | 表达式   | 描述                                                     |
  | -------- | -------------------------------------------------------- |
  | nodename | 选取此节点的所有子节点                                   |
  | /        | 从根节点选取                                             |
  | //       | 从匹配选择的当前节点选择文档中的节点，而不考虑它的位置。 |
  | .        | 选取当前节点                                             |
  | ..       | 选取当前节点的父节点                                     |
  | @        | 选取属性                                                 |



- Xpath 基本表达式使用案例

  | 路径表达式      | 结果                                                         |
  | --------------- | ------------------------------------------------------------ |
  | bookstore       | 选取 bookstore 元素的所有子节点                              |
  | /bookstore      | 选取根元素 bookstore<br />注释：假如路径起始于正斜杠（/），则此路径始终代表到某个元素的绝对路径 |
  | bookstore/book  | 选取属于 bookstore 的子元素的所有 book 元素                  |
  | //book          | 选取所有 book 子元素，而不管它在文档中的位置                 |
  | bookstore//book | 选择属于 bookstore 元素的后代的所有 book 元素，而不管它们位于 bookstore 之下的什么位置 |
  | //@lang         | 选取名为 lang 的所有属性                                     |



+ Xpath 谓语表达式


  | 路径表达式                         | 结果                                                         |
  | ---------------------------------- | ------------------------------------------------------------ |
  | /bookstore/book[1]                 | 选取属于 bookstore 子元素的第一个 book 元素                  |
  | /bookstore/book[last()]            | 选取属于 bookstore 子元素的最后一个 book 元素                |
  | /bookstore/book[last()-1]          | 选取属于 bookstore 子元素的倒数第二个 book 元素              |
  | /bookstore/book[position()<3]      | 选取最前面的两个属性 bookstore 元素的子元素的 book 元素      |
  | //title[@lang]                     | 选取所有拥有名为 lang 属性的 title 元素                      |
  | //title[@lang='eng']               | 选取所有 title 元素，且这些元素拥有值为 eng 的 lang 属性     |
  | /bookstore/book[price>35.00]       | 选取 bookstore 元素中的 book 元素的所有 title 元素，且其中的值大于35.00 |
  | /bookstore/book[price>35.00]/title | 选取 bookstore 元素中的 book 元素的所有 title 元素，且其中的值须大于35.00 |
  

  