# JSP 的基本语法



- JSP 语法十分简单，按功能可分为以下四种
  - JSP 代码块
    - JSP 代码块用于在 JSP 中嵌入 Java 代码
    - JSP 代码块语法：<% Java 代码块%>
    - 例如：<% System.out.println("Hello World"); %>
  - JSP 声明构造块
    - JSP 声明构造块用于声明变量或方法
    - JSP 声明构造块语法：<% !声明语句 %>
    - 例如：<%! public int add(int a, int b){return a+b;}%>
  - JSP 输出指令
    - JSP 输出指令用于在 JSP 页面中显示 Java 代码执行结果
    - JSP 输出指令语法：<%= Java 代码 %>
    - 例如：<% = "\<b>" +name + "\</b>%>
  - JSP 处理指令
    - JSP 处理指令用于提供 JSP 执行过程中的辅助信息
    - JSP 处理指令语法：<%@ JSP 指令%>
    - 例如：<%@  page import="java.until.*" %>



### JSP 常用处理指令



- <% @page %> 定义当前 JSP 页面全局设置
- <% @page include %> 将其他 JSP 页面与当前 JSP 页面合并
- <% @taglib%> 引入 JSP 标签库



### JSP 中注释的区别



- <%-- 注释--%> JSP 注释，被注释语句不做任何处理
- //、/**/ 用于注释 <%%> java 代码，被注释代码不执行
- \<!-- html --> HTML 注释，被注释语句不会被浏览器解释



### JSP 综合训练



```jsp
<%@page import="java.util.*"  contentType="text/html;charset=utf-8"%>
<%!
// 定义一个方法

boolean isPrime(int num){
	boolean flag = true;
	for(int j = 2; j < num; j++){
		if(num % j ==0){
			flag = false;
			break;
		}
	}
	return flag;
}
%>

<%
	List<Integer> primes = new ArrayList<Integer>();
	for(int i = 2; i <= 1000; i++){
		boolean flag = isPrime(i);
		if(flag == true){

			primes.add(i);
		}
	}
%>

<% 
	for(int p: primes){
		//out.println( "<h1>"+ p +"是质数</h1>");
		
%>
	<h1 style="color:red; "><%=p %>是质数</h1>
	
<%
	}

%>


```



### JSP 代码复用



```jsp
<%@page contentType="text/html; charset=utf-8"%>
要闻|推荐|财经|娱乐
```



```jsp
<%@page contentType="text/html; charset=utf-8"%>
<hr/>
Conpyright 1999-2018
```



```jsp
<%@page contentType="text/html; charset=utf-8"%>
<%@include file="include/header.jsp"%>
<%
	out.println("<h1>新闻标题</h1>");
	out.println("<p>新闻正文</p>");

%>
<%@include file="include/footer.jsp"%>
```

