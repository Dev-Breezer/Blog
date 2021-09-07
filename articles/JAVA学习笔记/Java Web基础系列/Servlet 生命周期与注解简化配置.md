### Servlet 生命周期

+ 装载 - web.xml
+ 创建 - 构造函数
+ 初始化 - init()
+ 提供服务 - service()
+ 销毁 - destroy()



```java
package com.demo.servlet;

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class FirstServlet extends HttpServlet{

	public FirstServlet() {
		System.out.println("正在创建FirstServlet对象");
		
	}
	
	
	@Override
	public void init(ServletConfig config) throws ServletException {
		System.out.println("正在初始化 FirstServlet 对象");
	}



	@Override
	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// 接收请求发来的参数
		String name = request.getParameter("name");
		String html = "<h1 style='color:red'>hi," + name +"!<h1></hr>";
		System.out.println("返回给浏览器的响应数据为：" + html);
		PrintWriter out = response.getWriter();
		out.println(html); // 将html发送回浏览器
	}


	@Override
	public void destroy() {
	System.out.println("正在销毁Servlet对象");
	}
}

```





### 注解简化配置



- Servlet 3.x 之后引入了 “注解Annotation” 特性
- 注解用于简化Web应用程序的配置过程
- Servlet核心注解：@WebServlet



```java
package com.demo.servlet;

import java.io.IOException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/anno")
public class AnnotationServlet extends HttpServlet{

	@Override
	protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		// TODO Auto-generated method stub
		resp.getWriter().println("I'm annotation servlet!");
	}
	
}

```



### 启动时加载 Servlet



- web.xml 使用 <load-on-startup> 设置启动加载
- <load-on-startup>0~999</load-on-startup>
- 启动时加载在工作中常用于系统的预处理



```java
package com.job.servlet;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;

/*
 * 假设开发xx系统,系统启动时要自动完成初始化数据库，完成数据导入，统计分析
 */

public class CreateServlet extends HttpServlet{

//	创建数据库
	
	@Override
	public void init() throws ServletException {
		System.out.println("正在创建数据库！");
	}
	
}
```



```java
package com.job.servlet;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;

public class ImportServlet extends HttpServlet {
//	导入数据
	@Override
	public void init() throws ServletException {
		System.out.println("正在导入数据！");
	}
	
}
```



```java
package com.job.servlet;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;

// 另一种设置启动时加载方法
@WebServlet(urlPatterns="/unused",loadOnStartup=2)
public class AnalysisServlet extends HttpServlet {
//	导入数据
	@Override
	public void init() throws ServletException {
		System.out.println("正在分析结果！");
	}
	
}
```



```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" id="WebApp_ID" version="3.1">
  <display-name>job.servlets</display-name>
  <welcome-file-list>
    <welcome-file>index.html</welcome-file>
    <welcome-file>index.htm</welcome-file>
    <welcome-file>index.jsp</welcome-file>
    <welcome-file>default.html</welcome-file>
    <welcome-file>default.htm</welcome-file>
    <welcome-file>default.jsp</welcome-file>
  </welcome-file-list>
  <servlet>
  <servlet-name>create</servlet-name>
  <servlet-class>com.job.servlet.CreateServlet</servlet-class>
  <load-on-startup>0</load-on-startup>
  </servlet>
  
  <servlet>
  <servlet-name>import</servlet-name>
  <servlet-class>com.job.servlet.ImportServlet</servlet-class>
  <load-on-startup>1</load-on-startup>
  </servlet>
  <!--  
  <servlet>
  <servlet-name>analysis</servlet-name>
  <servlet-class>com.job.servlet.AnalysisServlet</servlet-class>
  <load-on-startup>2</load-on-startup>
  </servlet>
-->
</web-app>
```

