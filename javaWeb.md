# JavaWeb

JavaWeb主要了解三大组件，cookie&session机制，Ajax

（了解原理）文件上传，国际化，.......已经逐渐被框架替代

## HTML
简介：超文本标记语言

### 常用标签
1. 普通的：`<p></p>` `<h1></h1>` `<br>` ...... （忘记了去 W3school手册查）
2. 重要的：`<table></table>`表格（colspan，rowspan）、`<form action="提交的位置" method="GET/POST" enctype=""></form>`表单、
	enctype="" 表单提交的编码方式
	enctype="multipart/form-data" 文件上传

## CSS
简介：层叠样式表

### 作用：
B/S开发 ->  B端：结构（HTML）--表现（CSS）--行为（Javascript）
（忘记了去 W3school手册查）

## JS
简介：javascript：脚本语言（弱类型）

### 基本语法
1. 声明变量
2. 声明对象 
	```js
	var obj={
		lastName:"张三",
		age:18
	}
	obj 对象
	alert(pbj.lastName);
	obj.email="aaa";
	```

3. 声明方法
	```js
	声明：
	function hello(){  ... }
	var hello=function(){ .... };
	
	调用：
	hello(1,2);
	hello();
	```

事件：用户和浏览器的交互行为
```js
window.onload=function(){
	//文档加载完成事件：（页面里面的所有内容全部是显示成功）
}
$(function(){
	//文档加载完成（dom准备完成）
});
这两个的区别：$(funciton(){...});这个加载更快（只是属性和标签加载好），但是window.onload更保险
window.onload可以多次使用，两次使用window.onload，最后一次有用
$(funciton(){...});本质是讲 $ 方法调用多次
```

常用事件：
```html
<a href="hello" id="abc">你好</a>
var ab=document.getElementById("abc");
ab.onclick=function(){
	alert("aaaa");
	return false; //取消默认行为，页面就不跳转了
}
```

js内置对象
（忘记了去 W3school手册查）

## JQuery（要精通）
简介：js库（就相当于java里面的jar包）

重点：
1. 选择器
2. 文档操作（对dom增删改）
3. 属性操作

层级：
ancestor descendant：找后代
parent > child：找子元素。`$("a >#btn01")`：找到a标签下 id为 btn01的子元素
prev + next：找下一个兄弟。`$("#btn01 + .mini")`：找到id为btn01的下一个同级元素，而且这个元素的class是mini
prev ~ sibilings：找所有的同辈兄弟。`$("#deleteBtn ~ a")`：找到 id 为deleteBtn元素的所有 a标签的兄弟元素。`$("#deleteBtn ~ ")`：这个就是找 id 为deleteBtn元素的所有兄弟元素

### 选择器
`$("a:first")`：找到第一个a标签
`$(":first")`：找到文档中第一个标签 ->`<html>`
`$("a :first")`：（a后面有空格）找到a的第一个后代元素
`$("a > :first")`：找到a的第一个子元素
`$("#btn > a:eq(1)")`：找到btn下的第二个a标签
`$("a:empty")`：找到所有没有标签体的a标签

`:checked`：找到所有选中的（复选框，单选框等，不包括select里的option）
`:selected`：匹配所有选中的option

`$("div").find(".mini")`：找到所有div标签里class为mini的元素（找到后代和子元素所有）
`$("div").children(".mini")`：找到div里所有class为mini的子元素
`$("#div01").parent(".mini")`：找到id为div01的父元素，而且父元素的class必须是mini
`$("#div01").parents(".mini")`：找到所有class为mini的祖先元素

### 文档增删改
哪些方法能链式调用？
方法返回的是jQuery对象，就可以继续链式调用任何jQuery方法；返回的是他本身
`$("#p01").append("<a>hello</a>").append("<b></b>").click(function(){});` 给p01绑定事件
    

### 属性操作
attr：自定义属性的说去和设置推荐使用attr
prop：自定义属性的说去和设置是不能获取到的
【有的内容去看word】

### 事件
1. blur
2. change
3. click
4. submit

### 核心函数
核心用法：
1. 传入参数为【函数】时，`$(function(){})`相当于`window.onload=function(){}`
2. 传入参数为【HTML字符串】时，创建html元素（jquery对象）
    - `$(<a href="hello">haha</a>).prop("href",'hello01');`
    - `$(<a href="hello">haha</a>)[0].href="hello02";`
3. 选择器 `$("选择器")`  -> `$("#btn01")`
4. 传入参数为【DOM对象】时，$(this)

可以将dom对象转为jquery对象 ：为了相互调用各自的方法
```js
var btn01=document.getElementById("btn01"); //这个是dom对象
此时想添加内容，想用 btn01.append();这个是不行的，因为上面的是dom对象，不能直接调用jquery里的方法，但是我们可以写成$(btn01).append(); 此时前面的就是可以将dom对象转为jquery对象，就可以使用jquery方法
$(btn01).append()  这个就是dom转jquery
$(btn01)[0]  这个就是jquery转dom
```


## XML（要了解）

要求：会正确写出标签

1. 简介，语法
2. xml-dom4j 解析（了解）
3. xpatch（快速查询）


## Tomcat（要掌握）
### Tomcat目录结构
bin：可执行程序；tomcat在这里启动：startup.bat 启动命令（双击启动）；shutdown.bat（双击关闭）
conf：tomcat的配置文件目录
    1. server.xml：tomcat的配置集中地方：端口配置.....
    2. web.xml：tomcat所有web项目都需要遵循的一个xml
lib：tomcat运行期间需要用到的jar包，比如 el表达式解析jar包
logs：tomcat运行日志
temp：临时文件夹
webapps：集合tomcat中所有运行的项目；每一个项目都是一个文件夹形式
work：存放运行期间编译的一些东西，比如jsp页面

### 与eclipse整合
有一个注意点：
tomcat如果有什么问题，要在eclipse中进行修改：
	window --> server --> runtime  tomcat的整合信息



### Http（熟悉）

1. f12  要会看请求头和请求体
2. 发送请求的整个数据叫 请求报文；服务器传给浏览器的数据叫 响应报文

报文格式：
      报文头部
      空行
      报文主体

请求报文：
      请求首行
      请求头
      空行
      请求体

响应报文：
      响应首行
      响应头
      空行
      响应体

（之后还可以去查  http各种响应头，请求头的作用）



## Servlet（掌握思想）
### 简介
用来接受请求，处理请求，完成响应的一段小程序

### Servlet体系
Servlet是javaweb的三大组件之一（Servlet，Filter，Listener）
Servlet：接口（一开始用的是这个，麻烦）

HttpServlet：（现在用这个）
1. doGet()
2. doPost()

### Servlet的使用
1. 编写servlet
2. 在web.xml中进行配置
	```xml
	<servlet>
		<servlet-name>MyFirstServlet</servlet-name>
		<servlet-class>com.servlet.MyFirstServlet</servlet-class>
	</servlet>
	<servlet-mapping>
		<servlet-name>MyFirstServlet</servlet-name>
		<url-pattern>/hello</url-pattern>
	</servlet-mapping>
	```
### 重要知识点
> ServletConfig：

一个Servlet对应一个ServletConfig封装当前Servlet的配置信息

> ServletContext：四大域对象之一

四大域对象（PageContext，ServletRequest，HttpSession，ServletContext）
域对象：在域中保存一些数据，跨页面获取到保存的数据；多个资源之间共享数据。

ServletContext的作用：
1. 域对象
2. ServletContext获取当前项目信息；一个项目对应一个ServletContext；只是代表当前项目，不能获取别的项目
	`context.getRealPath("/pic/aa.jpg")`，也是只能获取到当前项目下的某个资源的路径

（剩下的内容，需要自己去查 j2eeAPI）

> HttpServletRequest 

代表请求

每一次发送请求，请求的详细信息会被tomcat自动封装成一个request对象，如果要获取当前请求的一些信息，使用request对象即可

作用：
1. 获取请求参数：`request.getParameter("hello")`
2. 作为域对象保存数据；同一次请求期间可以共享数据
3. 获取到`HttpSession`对象：`request.getSession();`
4. 转发。`request.getRequestDispatcher("/index.jsp").forward(request.response);`将当次的请求和响应交给另一个程序处理，在服务器内部进行

服务器上保存了所有页面上的图片和视频，还有动态程序.....

页面上的 img，link(css)都是向服务器发请求。`<script src="jquery.js">`也是给服务器发请求



> HttpServletResponse 

代表响应

作用：

1. 交给浏览器的数据（响应首行，响应头[对浏览器的一些命令]和响应体[浏览器收到要解析的数据]）

2. 重定向：浏览器收到重定向命令以后要发送新请求

   ```java
   request.sendRedirect("重定向的地址");
   response.sendRedirect(request.getContextPath()+'/index.jsp');
   request.getContextPath(); 获取到项目名，以 /开始不以 /结束
   ```

   

### 重要

> 乱码

**请求乱码**：浏览器发送给服务器的数据，服务器收到解析出来乱码

```jsp
GET、POST:页面上除了 表单method="post" 外剩下的都是get请求
<img src="/pics/1011.jpg" />
<a href="hello?username="张三">hello</a>
```

Tomcat服务器默认的编码和解码格式就是 ISO8859-1

1. GET请求乱码

   - 原因：

     1. 所有的请求参数是带在 url地址上的

     2. tomcat收到这个请求就会调用默认的编码格式（ ISO8859-1）将其解码完成，并封装成 request对象

        ```java
        String un=requestParamter("username");
        un=new String(un.getBytes("ISO8859-1"),"UTF-8"); //这个是原理
        ```

   - 解决：修改服务器配置文件`server.xml`，在8080端口配置处加上一句 `URIEncoding="utf-8"`

2. POST请求乱码

   - 原因：请求带来的数据都是在请求体中放着，tomcat不着急解析请求体；一旦调用`request.getParameter("p");`将整个请求体默认编码格式全部解析完成
   - 解决：在调用`request.getParameter()`之前，加上`request.setCharacterEncoding("utf-8")`：告诉tomcat请求体的数据使用utf-8

**响应乱码：**服务器发给浏览器的数据，浏览器收到解析乱码

出现的原因：直接写出去的数据，浏览器不知道数据的内容类型以及编码格式等；浏览器就会用默认格式打开（有的默认格式是utf-8，有的是gbk.....）

解决：给浏览器的数据一定要说清楚这是什么？

```java
response.setContentType("text/html;charset=utf-8");
charset：字符集
```



**标配**

Tomcat安装整合好后，给server.xml 8080端口配置处加上`URIEncoding="UTF-8"`：直接解决所有的GET乱码问题

解决POST乱码和响应乱码问题，使用Filter

```java
CharacterEncodingFilter{
    request.setCharacterEncoding("UTF-8");
    response.setContentType("text/html;charset=utf-8");
    chain.doFilter(request,response);
}
/*
	response.setContentType("text/html;charset=utf-8");这个一般不写，在使用response.getWriter().write("xxx");的时候要写
*/
```



> 路径

**相对路径**：相对于当前资源所在的路径为标准（推荐不使用）

​	不以 `/` 开始的路径

**(虚拟)绝对路径**

​	以 `/` 开始的路径（比如：file://c:/dd/ddxs.text 或者 `http://localhost:8080/aa.jsp`）

**区分哪些是服务器解析路径，哪些是浏览器解析路径？**
		`response.sendRedirect("/index.jsp");` 因为这个路径是要浏览器访问的，加上项目名

​	只要是`html标签`（详见html标签列表）里写的路径都是浏览器解析路径，除此之外都是服务器解析路径。`<jsp:forward></jsp:forward>` jsp自定义标签：目前见到的所有有前缀的标签都是服务器解析路径

1. 服务器解析路径：`request.getRequestDispatcher("/index.jsp");`就是当前项目下的jsp；项目名是自动加上的。
2. 浏览器解析路径：在前面拼上服务器地址才是最终要去的路径；页面要写以 `/` 开始的路径加上项目名。

**总的来说**，推荐使用绝对路径，加上项目名

```java
ServletContextListener{
    context.setAttribute("ctp",request.getContextPath());
}
```

```html
<a href="${ctp}/index.jsp">hello</a>
```



## JSP/JSTL/EL（东西好多，不懂）

### JSP

> 简介

.....

> 原理

.....

> 9大隐含对象

这里总结一下里面的4个域对象：pageContext,request,session,application

从小到大共享数据的范围：pageContext，request，session，application

1. pageContext：当前页面共享数据，在当前页面可以取出来
2. request：同一次请求共享的数据，同一次请求期间可以共享（这里也需要弄清楚转发和重定向）
   - 转发：可以一直转发下去
   - 重定向：一旦response了，响应就完成，当前请求就结束了
3. session：同一次会话期间数据可以共享（浏览器打开就开始会话，浏览器关闭就结束会话）
4. application：同一个web应用中共享数据，只要服务器不关都可以使用



> jsp标签

.....



### JSTL

Jsp Standard Tag Library（JSP标准标签库）

主要要用好两个标签：`c:forEach`、`c:if`

```jsp
<c:forEach items="要遍历的集合" var="每次遍历出的元素的变量名">
	${每次遍历出的元素的变量名}
</c:forEach>
```

```jsp
<c:if test="判断条件"></c:if>
```



### EL

简化取值操作

```java
<%
	String str="aaa";
%>
```

el只能取出11个对象中的值

**4个域对象**

> pageScope

.......

> requestScope（需要注意两点）

第一点：

`${requestscope.username}`从请求域中取出username值

​		`${requestScope.username} = request.getAttribute("username");`

第二点：

request和requestScope的关系：在request对象中能够保存数据的一小块区域叫requestScope

```java
//这里用伪代码理解一下
Request{
    Map<String,Object> requestScope=new HashMap<String,Object>();
    public HttpSession getSession(){};
    public String getParameter(String param){};
}
```

> sessionScope

session和sessionScope的关系同上面的request

.....

> application

......

**7个其他的**

param：获取请求参数的 `${param.username}=request.getParameter("username")`

paramValues：获取请求参数的  `${paramValues.username}=request.getParameters("username")`获取多选框多选下拉列表的所有选择内容

header：请求头

headerValues

cookie：获取cookie

initParam：获取web.xml中配置的初始化参数

```xml
<context-param>
    <param-name>username</param-name>
    <param-value>tomcat</param-value>
</context-param>
```



## Session & Cookie（熟练掌握）

### Session

1. 服务器端保存当前会话大量数据的一种技术
2. Session保存的数据是可以在同一个会话期间共享

> 使用

```java
session.setAttribute("username","zhangsan");
session.getAttribute("username");
```



### Cookie

浏览器端保存少量数据的一种技术

> 特点

1. 保存少量
2. 都是纯文本
3. 保存的当前网址的cookie，每次访问这个网站都会携带
4. 默认不支持中文

> 使用

1、服务器如何给浏览器发送保存cookie

```java
Cookie cookie=new Cookie("username","zhangsan");
response.addCookie(cookie);
```

响应头中命令浏览器保存一个Cookie

浏览器一旦保存cookie后，访问我们这个网站都会带上这个cookie。

2、cookie的有效时间

默认：会话期间有效（浏览器只要不关，cookie就会在；cookie存在于浏览器的进程中）

```java
setMaxAge(int expiry)：设置cookie的有效时间，单位为 秒
正数：表示多少秒以后超时（cookie自动销毁）
负数：表示cookie就是会话cookie，随浏览器关闭而失效
0：cookie立即失效
Cookie cookie=new Cookie("username","zhangsan");
cookie.setMaxAge(0);
response.addCookie(cookie);
```

修改或者删除cookie只能使用同名cookie覆盖

3、读取某个cookie（了解）

```java
Cookie[] cookies=request.getCookies();
if(cookies!=null){
    for(Cookie cookies1:cookies){
        String key=cookies1.getName();
        String value=cookies1.getValue();
        if(key.equals("username")){
            Sysem.out.println(value);
        }
    }
}
```



### 会话控制

为什么在别的地方给session中保存的数据，在另一个地方可以获取出来？

1. 我们和服务器进行交互期间，可能需要保存一些数据，服务器就为每个会话专门创建一个map；这个map用来保存数据，这个map我们就是叫session
2. 100个会话就会有100个map；每次创建map的时候，这个map有一个唯一标识（JESSSIONid;会话id）

利用服务器每次访问会带上它所有的cookie，服务器只需要创建一块能保存数据的map，给这个map一个唯一标识；创建好以后命令浏览器保存这个map的标识；以后浏览器访问就会带上这个map标识，服务器就按照标识找到这个map，取出这个map中的数据



注意点：

1. cookie失效：会话关闭，默认是cookie没了；通过cookie持久化技术继续找到之前的session
2. session失效：自动超时/手动失效



### 令牌机制

表单重复提交和验证码是一样的，这就涉及令牌机制

f5会将之前的请求再次发出去，表单重复提交。

​	第一次访问页面生成一个令牌，只要不刷新页面，f5重新发送上一次请求，令牌不会变化。servlet第一次收到令牌进行比对，比对完毕，更换或删除令牌；下一次直接去刷新上次的请求，由于带来的令牌还是上次的，而这个令牌已经失效了

令牌机制应用场景：

1. 防止表单重复提交
2. 验证码

生成令牌后，把令牌保存在两个地方：服务器和页面。在servlet里处理时，就是分别拿到服务器和页面的令牌，对比令牌是否一致，不一致就拒绝处理，一致就处理请求并且把令牌的值改成别的（重复提交时会拒绝处理请求）。这样就可以防止表单重复提交

（伪代码的word里）



## Filter（掌握）

### 过滤器

三大组件：Servlet、Filter、Listener

1. Servlet：处理请求
2. Filter：过滤拦截请求
3. Listener：监听器

三大组件基本都需要在 web.xml中进行注册，除了Listener中两个（活化钝化监听器，绑定解绑监听器）需要javaBean实现 不需要注册外，剩下的三大组件都需要注册



### 使用

过滤器使用步骤：

1. 实现Filter接口
2. 去web.xml进行配置



### Filter配置

```xml
<filter>
    <filter-name>MyFirstFilter</filter-name>
    <filter-class>com.filter.MyFirstFilter</filter-class>
</filter>
<filter-mapping>
	<filter-name>MyFirstFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```



> url-pattern的三种写法

1. 精确匹配：`/pics/hhh.jsp`或者`/hello.login` 这些都是直接拦截指定的路径
2. 路径匹配（模糊匹配）：`/pics/*`  拦截pics下所有请求
3. 后缀匹配（模糊匹配）：`*.jsp`  拦截所有以 `.jsp`结尾的请求

补充：`/pics/*.jsp`这种写法不能使用，因为不满足上面任何一种，不能两种混着用



### Filter原理

```java
doFilter(){
    //放行请求
    chain.doFilter(request,response);
}
```

图示看word文档



## Listener（掌握ServletContext）

### 监听器

有8个监听器：
ServletRequest（有2个）、HttpSession（4个）、ServletContext（有2个）

2个：生命周期监听器，属性变化监听器

4个（HttpSession）：生命周期监听器，属性变化监听器，活化钝化监听器（HttpSessionActivtionListener），绑定解绑监听器（HttpSessionBindingListener）

**需要掌握的监听器**

ServletContextListener：

1. 生命周期监听器，监听ServletContext的创建和销毁（监听服务器的启动，停止）；
2. 服务器启动为当前项目创建ServletContext对象，服务器停止销毁创建的ServletContext

ServletContext：

1. 一个web项目对应一个ServletContext，它代表当前web项目的信息
2. 还可以作为最大的域对象在整个项目运行期间共享数据



### 使用

1. 实现对应的监听器接口
2. 去web.xml中进行配置

注意：有两个Listener（HttpSessionActivtionListener，HttpSessionBindingListener）是javaBean需要实现的接口

JavaBean是什么？就是Person，Student.....这些实体类



## Ajax和JSON（熟练掌握）

### Js对象

js对象表示法：是一种轻量级（和xml相比很轻量）的数据交换格式

{key:value1,key:value2...};
value可以有很多种：
1. 基本的类型（字符串，数字，布尔值）
2. 数组 {lastName:"李四",book:["西游记",{},18]}
3. 对象

如果服务器返回给浏览器的数据是 js对象这种样子的，浏览器使用 js解析就会很方便

JSON：js对象进行传输（HTTP（只能传输文本））

```js
json的要求是和js对象一样的，只不过key必须是字符串
js对象在声明的时候key是否加双引号是可以选择的
var stu={
    lastName:"张三",//lastName的双引号可加可不加（"lastName":"XXX"）
    age:18
}
//JSON（js内置对象）：将js对象转为json（应该是js对象字符串表示法）字符串
var strJson=JSON.stringify(stu);
alert(strJson);
alert(typeof strJson);
```



### JSON

JavaScript Object Notation

json应该是利于传输的字符串

```json
var stu={
    lastName:"张三",
    age:18,
    car:{
        pp:"BW",
        price:"30000$"
    },
    infos:[{
        bookName:"XXX",
        price:98.99
    },18,true]
};
```



```js
var stu={
    lastName:"张三",
    age:18
}
var strJson=JSON.stringify(stu);
/*
	因为json现在是字符串，想获取里面的值（json所代表的js对象里面的属性值）是获取不到的
	现在就需要把字符串（这个字符串要满足js对象表示法（json）格式）转为js对象
*/
var stu2=JSON.parse(strJson);
alert(stu2.lastName);
```



> 需要掌握的两个方法

1、将js对象转为json字符串：var strJson=JSON.stringify(stu);

2、将json字符串转为js对象：var stu2=JSON.parse(strJson);



### Ajax

Asynchronous Javascript And XML（异步JavaScript和XML）

是一种无刷新页面于服务器的交互技术（页面不刷新就可以收到服务器响应的数据）

原来的交互：

1. 浏览器发送请求
2. 服务器收到请求，调用对应的servlet进行处理,servlet处理完成会有响应信息生成
3. 浏览器收到了服务器响应的数据，把之前的页面清除，展示新的数据（效果就是页面刷新）

现在的交互：（XMLHttpRequest对象）

1. XMLHttpRequest对象帮我们发送请求
2. 服务器收到请求，调用对应的servlet进行处理，servlet处理完成会有响应信息生成
3. XMLHttpRequest对象收到数据（浏览器就感受不到这个数据了；xhr对象收到这个数据）

XMLHttpRequest对象：所有现代浏览器均支持XMLHttpRequest对象

xhr原生编程很麻烦，所以我们可以使用jquery包装Ajax请求



传统交互方式往往需要页面整个刷新，造成很大的服务器负担。

Ajax就是只让服务器返回我们需要的部分数据即可；不用返回整个页面。xhr替代浏览器来接受响应，发送请求；利用dom增删改的方式来改变页面效果。

是异步无刷新页面技术

1. 异步：不会阻塞浏览器
2. 同步：会阻塞浏览器；因为需要等到服务器整个处理完请求，完成响应之后才能做其他事情

> 总结：什么是Ajax？

xhr对象向服务器发送请求，并收到响应数据，利用dom增删改的方式来改变页面效果。



### Jquery-Ajax

get和post的用法是一样的，只是一个发的是post请求，一个发的是get请求

`$.get()`

`$.post()`

`$.ajax()`

> 需要获取json字符串的属性值

servlet里的doPost方法

```java
protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		String lastName=request.getParameter("lastName");
		String age=request.getParameter("age");
		System.out.println("lastName+age="+lastName+"+"+age);
		
		Map<String,Object> map=new HashMap<>();
		map.put("lastName","BBB");
		map.put("age",18);
		//1. 转成json
		Gson gson=new Gson();
		String json=gson.toJson(map);
		//
		response.getWriter().write(json);
	}
```

index.jsp里的js

```js
第一种获取方法：
$("#btn02").click(function(){
		$.post("${ctp}/AjaxServlet","lastName=AABB&age=17",function(data){
			var obj=JSON.parse(data);
			alert(obj.lastName);
		});
	});
第二种获取方法：
$("#btn02").click(function(){
		$.post("${ctp}/AjaxServlet","lastName=AABB&age=17",function(data){
			//第二种：type最后一个参数直接指定是json，jquery自动转成json对象
			alert(data.lastName);
		},"json");
	});
```



默认ajax是异步的；数据的接收和下面方法的执行，不冲突

异步不用等待整个ajax请求完成，才执行下面的方法

```js
$("#btn02").click(function(){
		//发送ajax请求
		//所有请求的属性参数都是可以通过这个js对象定义
		var options={
				url:"${ctp}/AjaxServlet",//规定请求地址
				type:"GET",//请求方式
				data:{lastName:"lisi",age:18},//发送的数据
            	async:true,//调整异步（true）/同步（false）:默认是异步
				success:function(data){
					//alert("成功！"+(typeof data));
					var lastName=data.lastName;
					var age=data.age;
					$("div:eq(2)").append("姓名"+lastName+"<br>年龄"+age);
					$("div:eq(2)").css("background-color","#bbb");
				},
            	error:function(){
                    alert("error!!!");
                },
				dataType:"json"
		};
		$.ajax(options);
    	/*	设置异步：如果在servlet设置睡眠，默认是先执行下面操作，等睡眠时间到，再执行ajax请求
    	如果设置了同步：就是一定要等待ajax整个完成，才会执行后面的
    	
    	*/
    	alert("lalalalala....");
		return false;//禁用默认行为
	});
```

error也有多个参数

```js
error:function(a,b){
	alert("错误!!!"+b+"状态码："+a.status);
}
```



## 国际化、文件上传下载（了解）

原生得过程看word

国际化的两个例子：

1、根据浏览器请求头带来的区域信息国际化页面

Locale locale=request.getLocale();

2、点击超链接切换国际化

（1）超链接带上区域信息：Loacale就根据带上的区域信息来new

（2）推荐国际化取值，格式化日期......

```jsp
<fmt:message key="k">.....
```



文件上传下载

上传

1、上传准备

2、文件上传的请求体，多部件的形式

3、我们得导包处理：commons-fileupload/io......

下载

把文件流交给浏览器（一定要告诉浏览器，这个流不要打开，请下载）

response.setHeader("Content-Disposition","attachment;filename=tupian.jpg");