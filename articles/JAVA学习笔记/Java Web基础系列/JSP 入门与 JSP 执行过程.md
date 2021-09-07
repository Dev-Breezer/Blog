# JSP 入门



### Servlet 开发的痛点

- 静态的 HTML 与动态的 Java 代码混在一起，难以维护
- Servlet 利用 out.println() 语句输出，开发效率低下
- Eclipse很难在开发过程中发现错误，调试困难



### JSP 介绍



- JSP 全称是（Java Server Pages）, Java 服务器页面
- JSP 是 J2EE 的功能模块，由 Web 服务器执行
- JSP 的作用就是降低动态网页开发难度



### JSP 的特点



- JSP 使用简单，短时间学习便可上手使用
- JSP 可将 Java 代码与 HTML 分离，降低开发难度
- JSP 的本质就是 Servlet



### JSP 的运行要求

- 可正常运行的 Tomcat
- 所有 JSP 页面扩展名必须是 .jsp
- JSP 页面应放在Web应用程序目录下



```jsp
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	<table>
		<tr>
			<th>year</th>
			<th>salary</th>
		</tr>
		
		<% 
			for(int i=0; i<=50; i++){
				out.println("<tr>");
				out.println("<td>" + i + "</td>");
				int sal = 0;
				if(i <=5){
					sal = 1500 + i * 150;
				}else if(i > 5 && i <= 10){
					sal = 1500 + 150 * 5 + 300 *(i - 5);
				}else if(i > 10){
					sal = 1500 + 150 * 5 + 300 * 5 + 375 * (i - 5);
				}
				out.println("<td>" + sal + "</td>");
				out.println("</tr>");
			}	
		%>
		
	</table>
</body>
</html>
```





### JSP 的执行过程与转译过程





![](E:\Blog\images\Java\JSP执行过程.png)

