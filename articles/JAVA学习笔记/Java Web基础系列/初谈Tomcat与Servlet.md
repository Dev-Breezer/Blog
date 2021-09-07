# Tomcat 与 Servlet



### B/S 模式执行流程

![B/S模式执行流程](E:\Blog\images\Java\BS模式执行流程.png)





###  请求与流程



- 从浏览器发出送给服务器的数据包为 “请求（Request）”
- 从服务器返回给浏览器的结果称为 “响应（Response）”



![](E:\Blog\images\Java\Request-Reponse.png)



### J2EE 是什么



- J2EE (Java 2 Platform Enterprise Edition) 即：Java 2企业版

- 开发BS(Web)应用程序就是J2EE最核心的功能
- J2EE由13个功能模块组成
  - Servlet  Web服务器小程序  ⭐⭐⭐⭐⭐
  - JSP  服务器页面     ⭐⭐⭐⭐⭐
  - JDBC  数据库交互模块  ⭐⭐⭐⭐
  - XML  XML交互模块
  - EJB   企业级Java Bean
  - RMI 远程调用
  - JNDI 目录服务
  - JMS 消息服务
  - JTA 事务管理
  - JavaMail 发送/接收Email
  - JAF 安全框架
  - CORBA CORBA集成
  - JTS CORBA事务监控



### Apache Tomcat



- Tomcat是Apache软件基金会旗下一款免费的开放源代码的Web应用服务器程序



### J2EE 与 Tomcat 的关系



- J2EE 是一组技术规范与指南，具体实现由厂商决定
- Tomcat 是 J2EE Web (Servlet 与 JSP) 标准的实现者
- J2SE 是 J2EE运行的基石，运行 Tomcat 离不开J2SE



### Servlet



- Servlet （Servlet Applet） 服务器小程序，主要功能用于生成动态 Web 内容
- Servlet 是 J2EE 最重要的组成部分，也是我们学习的重点

![](E:\Blog\images\Java\Tomcat和Servlet.png)

