**JavaWeb**

----

web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
</web-app>
```

JSP头部编码

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
```



# 概念

## 概述

Web开发：

- web，网页
- 静态web
  - html，css
  - 提供的数据始终不会发生变化
- 动态web
  - 淘宝，不一样的人不一样的时间不一样的数据
  - 技术栈：Servlet/JSP,ASP.PHP

在Java中，动态web资源开发技术统称JavaWeb

## web应用程序

可以提供浏览器访问的程序；

统一的web资放在同一个文件夹下，web应用程序->Tomcat：服务器;

一个web应用多多部分组成(静态web，动态web)，html,css,js,jsp,servlet,java程序，jar包，配置文件properties;

web应用程序编写完毕，若想提供给外界访问：需要一个服务器来统一管理。

## 静态web

 <img src="https://i.loli.net/2021/05/25/AzaZ43IMrd1SewG.png" alt="image-20210518175547642" style="zoom:80%;float:left" />

 <img src="https://i.loli.net/2021/05/25/HBfTISZLK5XGcNg.png" alt="image-20210518175735365" style="zoom:80%;float:left" />



















## 动态web

  <img src="https://i.loli.net/2021/05/25/W1OFrtIa7YDb2BP.png" alt="image-20210518180101537" style="zoom:80%;float:left" />





















缺点：

- 假如服务器动态web资源出现了错误，我们需要重新编写我们的**后台程序**，重新发布；

优点：

- 动态更新，用户交互(数据持久化：注册，商品信息，用户信息...)

  

# Web服务器

## 3个技术

 <img src="https://i.loli.net/2021/05/25/cGqmnxzS9ClEa6J.png" alt="image-20210518180628653" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/25/kzrZHvB2M7s4bJg.png" alt="image-20210518180832445" style="zoom:80%;float:left" />



## 服务器

服务器是一种被动操作，用来处理用户的请求和返回响应信息。

Tomcat,IIS.....

 <img src="https://i.loli.net/2021/05/25/WBqpfScdaYAzbNU.png" alt="image-20210518181258425" style="zoom:80%;float:left"/>















## Tomcat

<img src="https://i.loli.net/2021/05/25/t1qeU25wRFsfNbj.png" alt="image-20210518182418762" style="zoom:80%;float:left" />

<img src="https://i.loli.net/2021/05/25/OxPGWk2vDMZsVgz.png" alt="image-20210518182554864" style="zoom:80%;float:left" />)











<img src="https://i.loli.net/2021/05/25/hIG9k1tKXD5eyWn.png" alt="image-20210518182816715" style="zoom:80%;float:left" />

可以配置启动的端口号；

可以配置主机域名；



> 修改主机域名

<img src="https://i.loli.net/2021/05/25/wsWf1yeKDBGxILX.png" alt="image-20210518183429364" style="zoom:80%;float:left" />

面试题：

<img src="https://i.loli.net/2021/05/25/hCaFgVWAcrmU6Sb.png" alt="image-20210518184103713" style="zoom:80%;float:left" />

## web网站

- 将写的网站放到服务器的指定文件夹webapps中

```java
-- webapps: Tomcat服务器的web目录
    --ROOT
    --mafu：网站的目录名
      --WEB-INF
         --classes:java程序
         --lib:web应用程序所依赖的jar包
         --web.xml:网站的配置文件
      --index.html默认的首页
      --static 资源文件
            --css
            --js
            --img
        

```

# HTTP

## 简述

超文本传输协议（Hypertext Transfer Protocol，HTTP）是一个简单的请求-响应协议，它通常运行在[TCP](https://baike.baidu.com/item/TCP/33012)之上。它指定了客户端可能发送给服务器什么样的消息以及得到什么样的响应。请求和响应消息的头以[ASCII](https://baike.baidu.com/item/ASCII/309296)形式给出；而消息内容则具有一个类似[MIME](https://baike.baidu.com/item/MIME/2900607)的格式。这个简单模型是早期[Web](https://baike.baidu.com/item/Web/150564)成功的有功之臣，因为它使开发和部署非常地直截了当。

- http1.0:HTTP/1.0  一个连接只能获得一个web资源，断开连接
- http2.0:HTTP/1.1  一个连接只能获得多个web资源

> HTTP请求



> HTTP响应



<img src="https://i.loli.net/2021/05/25/9e1k3IYombXSAaH.png" alt="image-20210518200514117" style="zoom:80%;float:left" />

# Maven

<img src="D:\Typora\md\picture\JavaWeb\image-20210518200740007.png" alt="image-20210518200740007" style="zoom:80%;float:left" />

Maven核心思想：**约定大于配置**。

1. 下载

<img src="https://i.loli.net/2021/05/25/ZAwP45Rtop1OKTc.png" alt="image-20210518201404094" style="zoom:80%;float:left" />

2. 环境变量

<img src="https://i.loli.net/2021/05/25/vg9bQZDrzMY1OCF.png" alt="image-20210518201956263" style="zoom:80%;float:left" />

3. 修改镜像
4. 本地仓库，远程仓库

> 在IDEA中使用Maven

<img src="https://i.loli.net/2021/05/25/MC5vHYipjIlq6m4.png" alt="image-20210518203225295" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/25/mnhiKy8WZEARzM2.png" alt="image-20210518203404461" style="zoom:80%;float:left" />



IDEA中设置Maven

<img src="https://i.loli.net/2021/05/25/AEKLkdhDbPSXH2T.png" alt="image-20210518203702073" style="zoom:80%;float:left" />

<img src="https://i.loli.net/2021/05/25/Vp4LkNrOJStYZhG.png" alt="image-20210518205316323" style="zoom:80%;float:left" />

Maven创建成功后注意看下IDEA默认设置。

<img src="https://i.loli.net/2021/05/25/IF3YZq4gPonCKXb.png" alt="image-20210518210442733" style="zoom:80%;float:left" />

上面是用Maven模板的项目。



现在创建普通Maven项目-----一个干净的Maven项目。

<img src="https://i.loli.net/2021/05/25/vjpV1gyaGuB2zWK.png" alt="image-20210518204916915" style="zoom:80%;float:left" />

注意Maven项目的资源过滤问题：

<img src="https://i.loli.net/2021/05/25/IbrRK8YXgOl1tfv.png" alt="image-20210518211403458" style="zoom:67%;float:left" />

设置默认：

<img src="https://i.loli.net/2021/05/25/8j7ay4givCdQDNM.png" alt="image-20210518212420868" style="zoom: 67%; float: left;" />

Maven默认web项目中的web.xml版本问题：

采用Tomcat默认4.0版本。

# Servlet

## 测试

学习路线：

<img src="https://i.loli.net/2021/05/25/5IBGkyKlLhoYxSb.png" alt="image-20210518215601024" style="zoom:67%;float:left" />

概述：

<img src="https://i.loli.net/2021/05/25/WUVqrgKbfPYpSMm.png" alt="image-20210518215738587" style="zoom:67%;float:left" />

> 源码分析

<img src="https://i.loli.net/2021/05/25/BHs3XzIElR7bgNJ.png" alt="image-20210518230345787" style="zoom:77%;float:left" />

测试：

```java
public class Test01 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        final PrintWriter writer = resp.getWriter();
        writer.println("servletTest01");
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

编写映射：

java程序通过浏览器访问，需要给浏览器提供访问的路径，而浏览器需要连接web服务器拿到资源，所以需要在web服务器中注册servlet。

```xml
         <servlet>
             <servlet-name>Test01</servlet-name>
             <servlet-class>com.mf.study01.Test01</servlet-class>
         </servlet>
         <servlet-mapping>
             <servlet-name>Test01</servlet-name>
             <url-pattern>/Test01</url-pattern>
         </servlet-mapping>
```

## 原理

<img src="https://i.loli.net/2021/05/25/q6cYuojP4teN1Fi.png" alt="image-20210519081548463" style="zoom:80%;float:left" />

## Mapping

### 测试

1. 一个servlet指定一个路径

```xml
         <servlet>
             <servlet-name>Test01</servlet-name>
             <servlet-class>com.mf.study01.Test01</servlet-class>
         </servlet>
         <servlet-mapping>
             <servlet-name>Test01</servlet-name>
             <url-pattern>/Test01</url-pattern>
         </servlet-mapping>
```

2. 一个servlet指定多个路径

```xml
         <servlet>
             <servlet-name>Test01</servlet-name>
             <servlet-class>com.mf.study01.Test01</servlet-class>
         </servlet>
         <servlet-mapping>
             <servlet-name>Test01</servlet-name>
             <url-pattern>/Test01</url-pattern>
         </servlet-mapping>
         <servlet-mapping>
                <servlet-name>Test01</servlet-name>
                <url-pattern>/Test02</url-pattern>
         </servlet-mapping>
         <servlet-mapping>
                <servlet-name>Test01</servlet-name>
                <url-pattern>/Test03</url-pattern>
         </servlet-mapping>
```

3. 一个servlet可以指定通用映射路径

```xml
         <servlet-mapping>
            <servlet-name>Test01</servlet-name>
            <url-pattern>/Test03/*</url-pattern>
         </servlet-mapping>
```

/*直接跳转到首页。

4. 前缀

<img src="https://i.loli.net/2021/05/25/ZRBI5nU2NesqrOC.png" alt="image-20210519093433991" style="zoom:80%;float:left" />



### 404处理

```java
public class error extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        resp.setContentType("text/html");
        resp.setCharacterEncoding("utf8");
        final PrintWriter writer = resp.getWriter();
        writer.println("<h2>页面走丢了！</h2>");


    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}

```

```xml
        <servlet>
            <servlet-name>error</servlet-name>
            <servlet-class>com.mf.study01.error</servlet-class>
        </servlet>
        <servlet-mapping>
            <servlet-name>error</servlet-name>
            <url-pattern>/*</url-pattern>
        </servlet-mapping>
```







### 遇到问题

部署war包成功，war exploded失败的问题

<img src="https://i.loli.net/2021/05/25/CrT3Mc4i5D1vaum.png" alt="image-20210519091108792" style="zoom:80%;float:left" />



重建webapp模块发现结构差异：

<img src="https://i.loli.net/2021/05/25/NDthZQPa7VGlcyJ.png" alt="image-20210519091031621" style="zoom:80%;float:left" />

问题：

<img src="https://i.loli.net/2021/05/25/oRgFKScdxVE9j67.png" alt="image-20210519092558628" style="zoom: 67%; float: left;" />

综上问题：后缀路写错了

<img src="https://i.loli.net/2021/05/25/ZRBI5nU2NesqrOC.png" alt="image-20210519093456190" style="zoom:80%;float:left" />



## ServletContext

web容器启动的时候，它会为每个web程序创建一个对应的ServletContext对象，代表了当前的web应用。

### 共享数据

之后会用session和request替换ServletContext。

<img src="https://i.loli.net/2021/05/25/lN4DxVpevgqir6L.png" alt="image-20210519102604480" style="zoom: 80%;float:left" />



Test01

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        ServletContext context= this.getServletContext();
        String username = "上官婉儿";
        context.setAttribute("username",username);
    }
```

Test02

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
       ServletContext context = this.getServletContext();
        String username =(String) context.getAttribute("username");

        resp.setContentType("text/html");
        resp.setCharacterEncoding("utf-8");
        resp.getWriter().println("<h2>"+username+"</h2>");
    }
```

<img src="https://i.loli.net/2021/05/26/f5W6LDFNPpTnR2m.png" alt="image-20210519104735369" style="zoom:67%;float:left" />

### 获得初始化参数

几乎不用。

web.xml

<img src="https://i.loli.net/2021/05/26/jeWw4pdXH1VKogs.png" alt="image-20210519105734183" style="zoom: 80%;float:left" />![image-20210519105846235](https://i.loli.net/2021/05/26/AL3JfUkq5vu9pgN.png)



<img src="https://i.loli.net/2021/05/26/AL3JfUkq5vu9pgN.png" alt="image-20210519105859655" style="zoom:80%;float:left" />



### 转发

用request替换。

转发的时候url路径不会改变：

```java
        context.getRequestDispatcher("/test03").forward(req,resp);//调用forward进行转发
```

<img src="https://i.loli.net/2021/05/26/Z7NTlpesMHqxGIz.png" alt="image-20210519111146671" style="zoom:67%;float:left" />

### 获取资源文件

也可以用类加载反射获取。

Properties

<img src="https://i.loli.net/2021/05/26/GQ1O5zw7Thfxmlg.png" alt="image-20210519112009732" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/05/26/jp3cBm2KPg6aOvF.png" alt="image-20210519112343095" style="zoom: 67%;float:left" />

相对web应用拿到资源。

<img src="https://i.loli.net/2021/05/26/fspWMwyG9AKRFzQ.png" alt="image-20210519112920853" style="zoom:80%;float:left" />

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        InputStream is = this.getServletContext().getResourceAsStream("/WEB-INF/classes/db.properties");
        Properties properties = new Properties();
        properties.load(is);
        resp.getWriter().println("username:"+properties.getProperty("username"));
        resp.getWriter().println("password:"+properties.getProperty("password"));

    }
```

## Response

HttpServletResponse

----

web服务器收到客户端的http请求，针对这个请求，分别创建一个代表请求的HttpServletRequest的对象和一个代表响应的HttpServletResponse的对象。

<img src="https://i.loli.net/2021/05/26/lxvkcne9RsGrmW8.png" alt="image-20210519113724044" style="zoom:80%;float:left" />

- 输出消息
- 下载文件



### 下载文件

<img src="https://i.loli.net/2021/05/26/fVIMUAnThu9KJN2.png" alt="image-20210519123947663" style="zoom:80%;float:left" />

测试：

<img src="https://i.loli.net/2021/05/26/NJPh2uKrfa6VL8M.png" alt="image-20210519161610423" style="zoom:67%;float:left" />

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //1.获取文件下载的路径
        String realPath = "D:\\IDEA\\MyProject\\KuangStudy\\JavaWeb\\Servlet03\\target\\classes\\成徐.jpeg";
        System.out.println("下载文件的路径" + realPath);
        //2.下载的文件名是什么?
        String fileName = realPath.substring(realPath.lastIndexOf("\\") + 1);
        //3.设置办法让浏览器能够支持(Content-Disposition)我们需要的东西
        //下载文件名处理乱码问题：URLEncoder.encode
        resp.setHeader("Content-Disposition","attachment;filename="+ URLEncoder.encode(fileName,"UTF-8"));
        //4.获取下载文件的输入流
        FileInputStream in = new FileInputStream(realPath);
        //5.创建缓冲区
        byte[] buffer = new byte[1024];
        int len=0;
        //6.获取OutputStream对象
        ServletOutputStream out = resp.getOutputStream();
        //7.将FileOutputStream流写入到buffer缓冲区,使用OutputStream将缓冲区中的数据输出到客户端
        while ((len=in.read(buffer))!=-1){
            out.write(buffer,0,len);
        }
        in.close();
        out.close();

    }
```





> 各种静态资源导出问题

```xml
    <resources>
      <resource>
        <directory>src/main/java</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>false</filtering>
      </resource>
      <resource>
        <directory>src/main/resources</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
          <include>**/*.jpeg</include>
        </includes>
        <filtering>false</filtering>
      </resource>
    </resources>

```

<img src="https://i.loli.net/2021/05/26/DFn3tvL9JB76OPZ.png" alt="image-20210519160603116" style="zoom:80%;float:left" />



### 验证码

- 前端实现
- 后端实现：需要用到Java的图片类，生成图片。



<img src="https://i.loli.net/2021/05/26/qSARn5xoH6sp7IC.png" alt="image-20210519165601483" style="zoom:67%;float:left" />



```java
    //生成随机数
    private String makeRandom(){
        Random random = new Random();
        String num= random.nextInt(99999999)+"";
        StringBuffer buffer = new StringBuffer();
        for (int i = 0; i <8- num.length(); i++) {
            buffer.append("0");
        }
        num=num+buffer.toString();
        return num;
    }

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
       //如何让浏览器1s刷新一次
        resp.setHeader("refresh","1");
       //在内存中创建图片
        BufferedImage image = new BufferedImage(300, 80, BufferedImage.TYPE_INT_RGB);
       //得到图片
        Graphics2D graphics =(Graphics2D) image.getGraphics();//一只2D的笔
        graphics.setBackground(Color.white);
        graphics.fillRect(0,0,300,80);
        //给图片写数据
        graphics.setColor(Color.yellow);
        graphics.setFont(new Font(null,Font.BOLD,60));
        graphics.drawString(makeRandom(),10,60);
        //告诉浏览器这个请求用图片方式打开
        resp.setContentType("image/jpeg");
        //网站存在缓存，不让浏览器缓存
        resp.setDateHeader("expires",-1);
        resp.setHeader("Cache-Control","no-cache");
        resp.setHeader("Pragma","no-cache");
        //把图片写给图片
        ImageIO.write(image,"jpeg",resp.getOutputStream());
    }
```



### 重定向

(重点)  地址会发生该改变，一个web资源B受到客户端A请求后通知客户端A去访问另外一个web资源C，这个过程叫重定向。

常见场景：登录页面...

```java
    void sendRedirect(String var1) throws IOException;
```

> 重定向问题：添加项目名

```java
resp.sendRedirect(req.getContextPath()+"/Image");
```



或

```java
/*          resp.setHeader("Location","/Servlet03_war/Image");
          resp.setStatus(HttpServletResponse.SC_FOUND);//302*/
           //需要添加项目名字
          resp.sendRedirect("/Servlet03_war/Image");
```

<img src="https://i.loli.net/2021/05/26/SQgfhOWBkbou3MA.png" alt="image-20210519171214705" style="zoom:67%;float:left" />



> 面试题：转发和重定向区别

相同：页面都会实现跳转  

不同：转发时url不改变  307，重定向url改变 302。

提交表单跳转路径问题：

```bash
-- 代表当前项目
${pageContext.request.contextPath}
```

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<body>
     <form action="${pageContext.request.contextPath}/Request" method="get">
         <label>用户名：</label>
         <input type="text" name="username">
         <br>
         <label>密码：</label>
         <input type="password" name="password">
         <br>
         <input type="submit" value="提交">
     </form>
</body>
</html>

```



## Request

HttpServletRequest

----

<img src="https://i.loli.net/2021/05/26/ryLV87Mxik2zwvG.png" alt="image-20210519174101336" style="zoom:80%;float:left" />

### 获取参数

<img src="https://i.loli.net/2021/05/26/MSmvU1bKEcaNu97.png" alt="image-20210519174440326" style="zoom:67%;float:left" />





### 转发

```java
public class Login extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.setCharacterEncoding("UTF-8");
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String[] hobby = req.getParameterValues("hobby");
        System.out.println("==========================");
        System.out.println(username);
        System.out.println(password);
        System.out.println(Arrays.toString(hobby));
        System.out.println("==========================");
        //通过请求转发

        req.getRequestDispatcher("/header.jsp").forward(req,resp);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}

```



<img src="https://i.loli.net/2021/05/26/wWgEpGqoQSN4kuz.png" alt="image-20210519184947450" style="zoom:80%;float:left" />



```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <title>登录</title>
    <style>
         h2{
             margin-top: 61px;
             color: #b9ee84;
             position: relative;
             left: 10%;
         }
         div{
             width: 400px;
             height: 110px;
             background: #ec9cad;
             opacity: 0.4;
             border-radius: 10px;
             text-align: center;
             position: relative;
             left: 10%;
         }
    </style>
<body>
   <h2>登录</h2>
   <div>
       <form action="${pageContext.request.contextPath}/login" method="post">
           <label>用户名：</label>
           <input type="text" name="username">
           <br>
           <label>密码：</label>
           <input type="password" name="password">
           <br>
           <label>技能：</label>
           <input type="checkbox" name="hobby" value="九阳神功">九阳神功
           <input type="checkbox" name="hobby" value="幽冥神掌">幽冥神掌
           <input type="checkbox" name="hobby" value="大挪移">大挪移
           <br>
           <input type="submit" value="提交">
       </form>
   </div>
</body>
</html>

```



# Cookie

**会话**：用户打开浏览器点开超链接访问web资源，然后关闭浏览器，这个过程称为会话。

**有状态会话**：

<img src="https://i.loli.net/2021/05/26/cYhQF2AMG6jR3Oq.png" alt="image-20210519190219731" style="zoom:80%;float:left" />

保存会话的两种技术：

cookie:客户端技术（响应，请求）。

seesion:服务器技术，保存用户会话信息。

常见场景：网站二次登陆记住密码

----

输出乱码问题：

也就是说Demo2中的response.setCharacterEncoding隐藏在JSP页面中了。然后根据转换后的Servlet可以看出response.setContentType(“text/html;charset=utf-8”);才能达到应有的效果,在使用http协议的情况中，该方法设置 Content-type实体报头，response.setContentType()的作用是使客户端浏览器，区分不同种类的数据，并根据不，同的MIME调用浏览器内不同的程序嵌入模块来处理相应的数据。

```java
 resp.setContentType("text/html;charset=utf-8");
```



```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //服务器，告诉你，你来的时间，把这个时间封装成一个信件，你下次带着来，就知道你来了
        //解决中文乱码
        req.setCharacterEncoding("UTF-8");

        //注意响应如果不走jsp的话还要加
        resp.setContentType("text/html;charset=utf-8");

        PrintWriter out = resp.getWriter();
        //服务器从客户端获取Cookie
        Cookie[] cookies = req.getCookies();
        //判断Cookie是否存在
        if(cookies!=null){
            out.println("欢迎回来！");
            out.print("你上一次访问的时间是：");
            for (int i = 0; i < cookies.length; i++) {
                Cookie cookie = cookies[i];
                if(cookie.getName().equals("lastLoginTime")){
                    long lastLoginTime = Long.parseLong(cookie.getValue());
                    out.println(new Date(lastLoginTime).toLocaleString());
                }

            }
        }else {
            out.println("欢迎注册!");
        }
        //服务端可客户端响应一个Cookie
        Cookie cookie = new Cookie("lastLoginTime", System.currentTimeMillis()+"");
        resp.addCookie(cookie);


    }
```

<img src="https://i.loli.net/2021/05/26/SwPjYLvI5a6HKu2.png" alt="image-20210519204506360" style="zoom:80%;float:left" />



 1621428588129

1621428588129

```java
        //cookie有效期为一天
        cookie.setMaxAge(24*60*60);
```

关闭浏览器重新登陆

<img src="https://i.loli.net/2021/05/26/BoQAx4YimsjS6eb.png" alt="image-20210519205219564" style="zoom:80%;float:left" />



总结：

1. 从请求中拿到cookie信息
2. 服务器形影cookie给客户端

```java
        Cookie[] cookies = req.getCookies();
        cookie.getName().equals("lastLoginTime")
        cookie.getValue()
        new Cookie("lastLoginTime", System.currentTimeMillis()+"");
        cookie.setMaxAge(24*60*60);
        resp.addCookie(cookie);
```

<img src="https://i.loli.net/2021/05/26/b3S41Gy8havsj7o.png" alt="image-20210519210037418" style="zoom:80%;float:left" />

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //创建一个cookie，名字和需要删除的cookie名字一样
        Cookie cookie = new Cookie("lastLoginTime", System.currentTimeMillis()+"");
        cookie.setMaxAge(0);
        resp.addCookie(cookie);
    }
```



> 传输中文乱码最快解决方法

```java
out.println(URLDecoder.decode(cookie.getValue(),"utf-8"));

Cookie cookie = new Cookie("name", URLEncoder.encode("韩信","utf-8"));
```



# Session

（重点）保存会话信息一般用Session不用Cookie，是用得最多的。

- 服务器会给每一个用户或浏览器创建一个session对象
- 一个session独占浏览器，只要浏览器没关闭，session就存在
- 用户登录之后，整个网站它都可以访问---》保存用户，购物车信息



> Cookie和Session区别

<img src="https://i.loli.net/2021/05/26/K5bo49OVlZmRMWd.png" alt="image-20210519215422550" style="zoom:80%;float:left" />



```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //解决乱码
        req.setCharacterEncoding("UTF-8");
        resp.setContentType("text/html;charset=utf-8");
        //得到session
        HttpSession session = req.getSession();
        //给session存东西
        session.setAttribute("name","刘邦");
        //获取session的id
        String id = session.getId();
        //判断是否新创建session
        PrintWriter writer = resp.getWriter();
        if(session.isNew()){
            writer.println("欢迎注册,ID为："+id);
        }else {
            writer.println("欢迎登录,ID为："+id);
        }
    }
```

<img src="https://i.loli.net/2021/05/26/zV67AWjPiUkf4IL.png" alt="image-20210519213355707" style="zoom:80%;float:left" />

session本质还是放在cookie中：

```java
        //session创建的时候做了什么事情
        Cookie cookie = new Cookie("JSESSIONID", id;
        resp.addCookie(cookie);
```



> 存对象

```java
session.setAttribute("name",new Person("刘稚",18,"女"));
writer.println(session.getAttribute("name"));
```



> 注销session

手动注销

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //得到session
        HttpSession session = req.getSession();
        session.removeAttribute("name");
        session.invalidate();

    }
```

web.xml设置超时时间

```xml
        <session-config>
<!--            15分钟后session注销-->
            <session-timeout>15</session-timeout>
        </session-config>
```



<img src="https://i.loli.net/2021/05/26/bCmEq4OS3X2gsjB.png" alt="image-20210519215734556" style="zoom:80%;float:left" />



# JSP

java服务器页面

<img src="D:\Typora\md\picture\JavaWeb\image-20210519220146163.png" alt="image-20210519220146163" style="zoom:80%;float:left" />

## 原理

<img src="https://i.loli.net/2021/05/26/Wb7pSQjxJcwaePF.png" alt="image-20210519220352259" style="zoom:80%;float:left" />

<img src="D:\Typora\md\picture\JavaWeb\image-20210519220826655.png" alt="image-20210519220826655" style="zoom:80%;float:left" />



表示自己的目录优点怪：

<img src="https://i.loli.net/2021/05/26/UHyIVQCNSE2gqX9.png" alt="image-20210519234721011" style="zoom:80%;float:left" />



**浏览器向服务器发送请求，不管访问什么资源，其实都是在访问Servlet**

<img src="https://i.loli.net/2021/05/26/pf95CNZAUeExG2i.png" alt="image-20210519232656160" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/26/i2vUYfNnuhgXrbE.png" alt="image-20210519233325785" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/26/HDyASMNpbEgaZuG.png" alt="image-20210519233510874" style="zoom:80%;float:left" />



> 原理流程图

<img src="https://i.loli.net/2021/05/26/udUYCOmVSj6Khe8.png" alt="image-20210519233910792" style="zoom:80%;float:left" />



在JSP页面中：

只要是JAVA代码就会原封不动的输出；

如果是HTML代码，就会被转换为这样的格式输出到前端：

```java
      out.write("<html>\r\n");
      out.write("<head>\r\n");
```

<img src="https://i.loli.net/2021/05/26/9zE2bHTL8G5hswN.png" alt="image-20210520120226052" style="zoom:80%;float:left" />



## JSTL

导入JSTL和标签库依赖

```xml
    <!-- https://mvnrepository.com/artifact/javax.servlet/jstl -->
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>jstl</artifactId>
      <version>1.2</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/taglibs/standard -->
    <dependency>
      <groupId>taglibs</groupId>
      <artifactId>standard</artifactId>
      <version>1.1.2</version>
    </dependency>
```



## 语法

```jsp
<%%>
<%=%>
<%!%>
<%----%>
```



JSP作为java技术的一种应用，了解知道即可。Java所有语法JSP都支持。

> JSP表达式:用来将程序输出到客户端

```jsp
<%=
  变量或者表达式
%>

例：
<%=
  new Date().toLocaleString()
%>
```

也可以直接用$取出元素值:EL表达式

```jsp
${new Date().toLocaleString()}
```





> JSP脚本片段

```jsp
<%
  java程序
%>

例：
<%
    int sum=0;
    for (int i = 0; i < 100; i++) {
        sum+=i;
    }
    out.println("<h2>sum="+sum+"</h2>");
%>
```

> 嵌入HTML元素

```jsp
<%--嵌入HTML元素--%>
<%
    int index=0;
    for (index = 0; index < 5; index++) {
        
    }
%>
<div class="div-1">
    <div class="div-2">
       <h3>现在是第： <%= index%> 进行笔试</h3>
    </div>
</div>
<%
    
%>
```

嵌套后：

```jsp
<style>
    .div-1{
        width: 500px;
        height: 304px;
        position: relative;
        top: 3%;
        left: 15%;
        background: #0affa5;
        opacity: 0.3;
    }
    .div-2 {
        width: 400px;
        height: 40px;
        text-align: center;
        position: relative;
        left: 10%;
        background: #ff4848;
        top: 5%;
    }
    h3{
        font-size: 18px;
        line-height: 40px;
        font-family: 华文宋体, serif;
    }
</style>
```



```jsp
<hr>
<%--嵌入HTML元素--%>
<div class="div-1">
<%
    int index=0;
    for (index = 0; index < 5; index++) {
%>
<div class="div-2">
    <h3>现在是第： <%= index%> 进行笔试</h3>
</div>
<%
    }
%>
    
</div>
```

<img src="https://i.loli.net/2021/05/26/lBWYXwUjJeIp8Ec.png" alt="image-20210520115541579" style="zoom:80%;float:left" />

以上代码都是在_jspService方法中的，所有变量都是方法内的局部变量。

> 全局变量

JSP声明：会被编译到JS生成的Java类中。其他的则会生成到_jspService方法中。

```jsp
<%!
    全局变量
%>
```

```jsp
<%!
   static {
       System.out.println("正在加载servlet");
   }
   private int globalVar=0;
   public void jspMafu(){
       System.out.println("进入了Mafu方法");
   }
%>
```

<img src="https://i.loli.net/2021/05/26/Jt7zQLxNuH2AEMK.png" alt="image-20210520121018794" style="zoom:80%;float:left" />



## 指令

```jsp
<%@page args....%>
```

> errorPage

```jsp
<%@ page errorPage="error/500.jsp" %>
```

```jsp
<img src="${pageContext.request.contextPath}/image/500.jpeg" alt="500错误">
```

方式二：

web.xml中修改

```xml
         <error-page>
             <error-code>500</error-code>
             <location>/error/500.jsp</location>
         </error-page>
```



> 公共文件包含

```jsp
<%@ include file="common/header.jsp"%>
```

```jsp
<body>
    <%@ include file="common/header.jsp"%>
    <h1>项目主体1</h1>
    <%@ include file="common/footer.jsp"%>
    <hr>
    <jsp:include page="/common/header.jsp"/>
    <h1>项目主2</h1>
    <jsp:include page="/common/footer.jsp"/>
</body>
```

一般使用第二种jsp标签方式包含公共页面。

区别：

第一种方式会将二者合二为一；

<img src="https://i.loli.net/2021/05/26/AzxHnFGPsZl41tm.png" alt="image-20210520161623617" style="zoom:80%;float:left" />



第二种是将两者通过引用拼接。

<img src="https://i.loli.net/2021/05/26/Br29tuhSlJGbNpD.png" alt="image-20210520161550423" style="zoom:80%;float:left" />

还有一个区别方式一的同名变量会发生冲突。

注：WEB-INF文件夹下不放资源，用户无法访问。



## 内置对象

9个

- PageContext
- Request
- Response
- Session
- Application [ServletContext]
- config  [ServletConfig]
- out
- page
- excetion



```jsp
<body>
<%--  内置对象--%>
<%
    pageContext.setAttribute("name1","刘邦1");//pageContext在当前页面有效
    request.setAttribute("name2","刘邦2");//只在一次请求中有效哦,请求转发携带
    session.setAttribute("name3","刘邦3");//一次会话会话中有效
    application.setAttribute("name4","刘邦4");//在服务器中有效
%>
<%--   脚本中代码原封不动放到java中 --%>
<%
    //通过pageContext来取值
    //从底层到高层(作用域)：
    String name1 = (String) pageContext.findAttribute("name1");
    String name2 = (String) pageContext.findAttribute("name2");
    String name3 = (String) pageContext.findAttribute("name3");
    String name4 = (String)  pageContext.findAttribute("name4");

%>

<%--使用el表达式输出--%>
<h2>取出的值为：</h2>
<h3>${name1}</h3>
<h3>${name2}</h3>
<h3>${name3}</h3>
<h3>${name4}</h3>

<%--
   ${name5}输出为空被过滤掉
   <%=name5%>输出null 不希望看到
--%>
</body>
```



<img src="https://i.loli.net/2021/05/26/kT6ASELCFeW2oMB.png" alt="image-20210521211322314" style="zoom:80%;float:left" />

观察作用域：

<img src="https://i.loli.net/2021/05/26/EtKhHPIJkmZDsAc.png" alt="image-20210521211402019" style="zoom:80%;float:left" />

结果：

<img src="https://i.loli.net/2021/05/26/U6J7i3VKXa8O2RY.png" alt="image-20210521211454261" style="zoom:80%;float：left" />



**从底层到高层(作用域)：pageContext-->request-->session-->application**

JVM:双亲委派机制;

<img src="https://i.loli.net/2021/05/26/PbxeiU5cjKNtpwA.png" alt="image-20210521211819147" style="zoom:80%;float:left" />

> 转发

```jsp
   <%
       pageContext.forward("/pageContext02.jsp");//页面中写法
       request.getRequestDispatcher("/pageContext02.jsp").forward(request,response);//后台写法
   %>
```

<img src="https://i.loli.net/2021/05/26/hAsOleQFmVE7n5t.png" alt="image-20210521212910382" style="zoom:80%;float:left" />



## JSP标签

都需要到包:jstl,standard

```xml
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>jstl</artifactId>
      <version>1.2</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/taglibs/standard -->
    <dependency>
      <groupId>taglibs</groupId>
      <artifactId>standard</artifactId>
      <version>1.1.2</version>
    </dependency>
```



3个JS标签

```jsp
<body>
    <h2>jspTag01页面</h2>
    <% request.setCharacterEncoding("utf8"); %>
    <% response.setContentType("text/html;charset=UTF-8");%>
<%--    <jsp:include page="pageContext02.jsp"/>--%>
    <jsp:forward page="jspTag02.jsp">
        <jsp:param name="value1" value="值1"/>
        <jsp:param name="value2" value="值2"/>
    </jsp:forward>
</body>
```





## JSTL标签

JSTL标签的使用就是为了弥补HTML标签的不足；JSTL功能标签和JAVA代码一样。

> 核心标签(掌握部分)

导入核心标签库

```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```



<img src="https://i.loli.net/2021/05/26/W5ytfwxD6P2RXem.png" alt="image-20210521215226556" style="zoom:80%;float:left" />

导包后标签出错可以检查Tomcat是否有包。

> c:if 

```jsp
<body>
   <h3>if测试</h3>
   <form action="coreIf.jsp" method="get">
<%--    获取表单中的数据：${param.参数名}--%>
       <input type="text" name="username" value="${param.username}">
       <input type="submit" value="提交">
   </form>
<%--判断如果提交的用户名是管理员则登录成功--%>
<%--  var是返回值--%>
<c:if test="${param.username=='admin'}" var="isAdmin">
    <c:out value="欢迎Admin登录！"/>
</c:if>
<c:out value="${isAdmin}"/>
</body>
```

> c:chose   c:when

```jsp
<body>
<%--set用来设置变量值--%>
    <c:set var="score" value="88"/>
    <c:choose>
        <c:when test="${score>=90}">哟秀！</c:when>
        <c:when test="${score>=80}">良好！</c:when>
        <c:when test="${score>=70}">不错！</c:when>
        <c:when test="${score>=60}">加油！</c:when>
    </c:choose>
</body>
```

> c:foreach

```jsp
<body>
     <%
         ArrayList<String>  people= new ArrayList<>();
         people.add("Mafu1");
         people.add("Mafu2");
         people.add("Mafu3");
         people.add("Mafu4");
         request.setAttribute("list",people);
     %>
     <c:forEach var="people" items="${list}">
         <c:out value="${people}"/>
         <br>
     </c:forEach>
<%--
var:每次遍历出来的变量
items:要遍历的集合
begin:开始
end：结束
step：步长
--%>
      <hr>
      <c:forEach begin="1" end="3" step="2" var="people" items="${list}">
          <c:out value="${people}"/>
          <br>
      </c:forEach>
</body>
```



> 格式化标签  SQL标签   XML  了解



## EL表达式

- 获取数据
- 执行运算
- 获取web开发的常用对象



# Bean

JavaBean实体类有特定的写法：

- 必须要有一个无参构造
- 属性必须私有化
- 必须有对应的get/set方法
- 一般用来和数据库的字段做映射 ORM(对象关系映射)
  - 表--》类
  - 字段--》属性
  - 行记录--》对象

```jsp
<body>
<%--
    以前要使用一个类是这样new对象的 new Sc();
    set方法相当于
--%>
<jsp:useBean id="sc" class="com.mf.pojo.Sc" scope="page"/>
<jsp:setProperty name="sc" property="cno" value="222"/>
<jsp:setProperty name="sc" property="sno" value="2"/>
<jsp:setProperty name="sc" property="grade" value="92"/>
<jsp:setProperty name="sc" property="newGrade" value="A"/>

 课程号：   <jsp:getProperty name="sc" property="cno"/>
 学号：   <jsp:getProperty name="sc" property="sno"/>
 成绩：   <jsp:getProperty name="sc" property="grade"/>
 等级：   <jsp:getProperty name="sc" property="newGrade"/>

</body>
```



- 过滤器
- 文件上传
- 邮件发送
- JDBC使用，CRUD，JDBC事务



# MVC

模型、视图、控制器。

> 早期架构

用户直接访问控制层，控制层直接操作数据库；

servlet-->CRUD-->数据库

弊端：程序臃肿不利维护

servlet代码：处理请求，响应、视图跳转，处理JDBC、业务逻辑代码；

<img src="https://i.loli.net/2021/05/26/TDbiUe4rSRHOC6u.png" alt="image-20210522094557895" style="zoom:80%;float:left" />

解决：没有啥是加一层解决不了的。

<img src="https://i.loli.net/2021/05/26/UEqa1tjFOy8S4Xm.png" alt="image-20210522094926349" style="zoom:80%;float:left" />



> MVC架构

<img src="https://i.loli.net/2021/05/26/jFIZUVxMsA6C1TX.png" alt="image-20210522095259924" style="zoom:80%;float:left" />

Model:

- Service:业务逻辑
- Dao：数据持久层CRUD

View：

- 展示数据
- 提供链接发起servlet请求(a,form,img...)

Controller：

- 接收用户请求：(req:请求参数，Session信息...)

- 交给业务层处理对应的代码

- 控制视图的跳转

  ```tex
  登录--》接收用户登陆请求--》处理用户请求获取参数--》交给业务层处理业务(判断，事务)--》Dao层查询事务正确--》数据库
  ```



# Filter

**重点**

过滤器，过滤网站数据：

- 处理中文代码（在每次调用servlet之前就将乱码处理好）
- 登录验证

<img src="https://i.loli.net/2021/05/26/gPLzne6yofXdaTU.png" alt="image-20210522100128259" style="zoom:80%;float:left" />

Filter和servlet一样，都是直接实现相对应接口即可：

<img src="https://i.loli.net/2021/05/26/qZzy4Dm1CMtHiTI.png" alt="image-20210522101002834" style="zoom:80%;float:left" />



随服务器一起启动：

<img src="https://i.loli.net/2021/05/26/CgoKuUmV4DZk1vM.png" alt="image-20210522103014661" style="zoom:80%;float:left" />



ShowServlet

```java
resp.getWriter().write("你最近怎么样了？");
```



CharacterEncodingFilter:实现Filter接口，重写方法即可。

```java
public class CharacterEncodingFilter implements Filter {
    //初始化
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        System.out.println("CharacterEncodingFilter正在初始化....");
    }
   /*
    Chain:链
    1.过滤器中的所有代码，在过滤特定请求的时候都会执行
    2，必须要让过滤器继续通行filterChain.doFilter
   * */
    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        servletRequest.setCharacterEncoding("utf-8");
        servletResponse.setContentType("text/html;charset=UTF-8");
        System.out.println("过滤器执行前....");
        filterChain.doFilter(servletRequest,servletResponse);//多个过滤器，让请求继续走，不写则停止请求程序
        System.out.println("过滤器执行后...");
    }
    //销毁
    @Override
    public void destroy() {
        System.out.println("CharacterEncodingFilter正在销毁.....");
    }
}
```



web.xml

```xml
        <servlet>
            <servlet-name>ShowServlet</servlet-name>
            <servlet-class>com.mf.servlet.ShowServlet</servlet-class>
        </servlet>
        <servlet-mapping>
            <servlet-name>ShowServlet</servlet-name>
            <url-pattern>/show</url-pattern>
        </servlet-mapping>
        <servlet-mapping>
            <servlet-name>ShowServlet</servlet-name>
            <url-pattern>/servlet/show</url-pattern>
        </servlet-mapping>

        <filter>
            <filter-name>CharacterEncodingFilter</filter-name>
            <filter-class>com.mf.filter.CharacterEncodingFilter</filter-class>
        </filter>
        <filter-mapping>
            <filter-name>CharacterEncodingFilter</filter-name>
<!--           过滤/servlet后的所有请求-->
            <url-pattern>/servlet/*</url-pattern>
        </filter-mapping>

```

## 权限拦截

用户登录进入主页，用户注销无法登录。

出错：重定向路径问题

<img src="https://i.loli.net/2021/05/26/VQC8HmPst2SdI5M.png" alt="image-20210522122148730" style="zoom:80%;float:left" />



首先设置session常量：

```java
public class Constant {
    public static String USER_SESSION="USER_SESSION";
}
```

login.jsp

```jsp
<body>
    <form action="${pageContext.request.contextPath}/servlet/login" method="get">
        <span>用户名：</span> <input type="text" name="username">
        <br>
        <span>密码：</span> <input type="password" name="password">
        <br>
        <input type="submit" value="登录">
    </form>
</body>
```



LoginServlet:session常量第一次设置

```java
public class LoginServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        System.out.println(username);
        System.out.println(password);
        if(username.equals("admin")&&password.equals("123456")){
            System.out.println("进入正确页面");
            req.getSession().setAttribute(Constant.USER_SESSION,req.getSession().getId());
            resp.sendRedirect(req.getContextPath()+"/sys/main.jsp");
        }else {
            System.out.println("进入错误页面");
            resp.sendRedirect(req.getContextPath()+"/error.jsp");
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

不在首页拦截main.jsp

```jsp
<body>
<%--  <%--%>
<%--      Object userSession = request.getSession().getAttribute(Constant.USER_SESSION);--%>
<%--      if(userSession==null) response.sendRedirect(request.getContextPath()+"/login.jsp");--%>
<%--  %>--%>
  <h2>主页</h2>
  <div>
      <a href="${pageContext.request.contextPath}/servlet/logout">注销</a>
  </div>
</body>
```

SysFilter过滤器

```java
public class SysFilter implements Filter {
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {

    }

    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {

        //因为要用到session一些参数所以需要强转一下
        HttpServletRequest req = (HttpServletRequest) servletRequest;
        HttpServletResponse resp = (HttpServletResponse) servletResponse;
        if (req.getSession().getAttribute(Constant.USER_SESSION)==null) {
            resp.sendRedirect(req.getContextPath()+"/error.jsp");
        }


        filterChain.doFilter(servletRequest,servletResponse);
    }

    @Override
    public void destroy() {

    }
}

```



注册过滤器：

```xml
        <filter>
            <filter-name>CharacterEncodingFilter</filter-name>
            <filter-class>com.mf.filter.CharacterEncodingFilter</filter-class>
        </filter>
        <filter-mapping>
            <filter-name>CharacterEncodingFilter</filter-name>
<!--           过滤/servlet后的所有请求-->
            <url-pattern>/servlet/*</url-pattern>
        </filter-mapping>

        <filter>
            <filter-name>SysFilter</filter-name>
            <filter-class>com.mf.filter.SysFilter</filter-class>
        </filter>
        <filter-mapping>
            <filter-name>SysFilter</filter-name>
            <url-pattern>/sys/*</url-pattern>
        </filter-mapping>

```



应用：权限管理

1. 用户登录后像session中放入用户的数据
2. 进入主页的时候要判断用户是否已经登录，要求：在过滤器中实现。

<img src="https://i.loli.net/2021/05/26/9GgvhW2TSNVmxFq.png" alt="image-20210522180232721" style="zoom:80%;float:left" />





# Listener

监听器。

实现监听器接口：有N种，，

OnlineCountListener

```java
//统计在线人数
public class OnlineCountListener implements HttpSessionListener{
    //创建session的监听
    //一旦创建一个session就会触发
    @Override
    public void sessionCreated(HttpSessionEvent httpSessionEvent) {
        ServletContext context = httpSessionEvent.getSession().getServletContext();
        System.out.println(httpSessionEvent.getSession().getId());
        Integer onlineCount = (Integer) context.getAttribute("OnlineCount");
        if (onlineCount==null){
            onlineCount= 1;
        }
        else{
            int count= onlineCount;
            onlineCount= count + 1;
        }
        System.out.println(onlineCount);
        context.setAttribute("onlineCount",onlineCount);
    }
    //销毁session的监听
    @Override
    public void sessionDestroyed(HttpSessionEvent httpSessionEvent) {
        ServletContext context = httpSessionEvent.getSession().getServletContext();
        httpSessionEvent.getSession().invalidate();
        Integer onlineCount = (Integer) context.getAttribute("OnlineCount");
        if (onlineCount==null) onlineCount=0;
        else onlineCount-=1;
        context.setAttribute("onlineCount",onlineCount);
    }

    /*
    session销毁：
    1.手动：过期时间
    2.重启服务器
    * */
}
```

```xml
<!--    注册监听器-->
        <listener>
            <listener-class>com.mf.Listener.OnlineCountListener</listener-class>
        </listener>
<!--    1分钟过期-->
        <session-config>
            <session-timeout>1</session-timeout>
        </session-config>
```

index.jsp

```jsp
  <body>
    <h2>
      当前在线人数：
      <span><%= this.getServletConfig().getServletContext().getAttribute("onlineCount")%></span>
    </h2>
  </body>
```

## 应用

关闭窗口

```java
public class TestPanel {
    public static void main(String[] args) {
        Frame frame = new Frame("监听器GUI");
        Panel panel = new Panel();
        frame.setLayout(null);
        frame.setBounds(300,300,600,400);
        frame.setBackground(Color.red);
        panel.setBounds(50,50,200,300);
        panel.setBackground(Color.gray);
        frame.add(panel);
        frame.setVisible(true);

       //关闭事件，加监听事件
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
```



# JDBC

<img src="https://i.loli.net/2021/05/26/zDCwTvNGEsZxt5K.png" alt="image-20210522181139904" style="zoom:80%;float:left" />



> 预编译



时间设置：

<img src="D:\Typora\md\picture\JavaWeb\image-20210522182034412.png" alt="image-20210522182034412" style="zoom:80%;float:left" />



> 事务

ACID保证数据安全。

<img src="https://i.loli.net/2021/05/26/crfuAzk21Y8mHsF.png" alt="image-20210522182300620" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/26/abJTXHd6AVR52Pj.png" alt="image-20210522182751086" style="zoom:80%;float:left" />



# 超市订单管理系统

SMBMS

登录页：

<img src="https://i.loli.net/2021/05/26/F3JpynK1PfMQomz.png" alt="image-20210522183255084" style="zoom:80%;float:left" />

首页：

<img src="https://i.loli.net/2021/05/26/JhOoMuQW4PFURgp.png" alt="image-20210522183335632" style="zoom:80%;float:left" />

模块分析：

<img src="https://i.loli.net/2021/05/26/BxKV5aiZlubAQTH.png" alt="image-20210522183541069" style="zoom:80%;float:left" />

数据库架构表:

<img src="https://i.loli.net/2021/05/26/W9QeThqI1Hxv6Ua.png" alt="image-20210522183936834" style="zoom:80%;float:left" />



> 项目搭建准备工作

1. 创建maven项目，测试。
2. 导包

```xml
mysql-connector-java
servlet-api
jsp-api
jstl
standard

lombok
junit
```

3. 创建项目包结构，创建实体类：ORM映射

<img src="https://i.loli.net/2021/05/26/qdORvzE3rh9V4ti.png" alt="image-20210522202927292" style="zoom:80%;float:left" />/

4. 基础公共类

   - 数据库配置文件采用dbcp

     <img src="https://i.loli.net/2021/05/26/EXC8aWlrVkDgLj3.png" alt="image-20210522202801230" style="zoom:80%;float:left" />

   - 过滤器

     <img src="https://i.loli.net/2021/05/26/g7iL8cG6QsVrlvX.png" alt="image-20210522210452744" style="zoom:80%;float:left" />

5.导入静态资源

<img src="https://i.loli.net/2021/05/26/vtxYAU3bHm5FfBa.png" alt="image-20210522210938016" style="zoom:80%;float:left" />



接下来是每个功能模块的具体实现。



## 登录

<img src="https://i.loli.net/2021/05/25/U1q5Dkn8lORrS9X.png" alt="image-20210522211354152" style="zoom:80%;float:left" />

1. 编写前端页面

2. 设置首页

   <img src="https://i.loli.net/2021/05/25/hFALWj9Ds8SqUz7.png" alt="image-20210522213728511" style="zoom:80%;float:left" />

3. 编写dao层

   <img src="https://i.loli.net/2021/05/25/J8P7mwryUiOtWhB.png" alt="image-20210522215449312" style="zoom:80%;float:left" />

4. 编写service层,测试

   <img src="https://i.loli.net/2021/05/25/zx5YLWG1KFqHCJp.png" alt="image-20210523181639368" style="zoom:80%;float:left" />

5. 编写servlet,测试

   <img src="https://i.loli.net/2021/05/25/B9MVtLdqlkWnFS2.png" alt="image-20210523183740587" style="zoom:80%;float:left" />



> 退出

移除session

```java
req.getSession().removeAttribute(Constant.USER_SESSION);
```



> 登录权限拦截

退出后无法直接通过url访问主页。

```java
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        HttpServletRequest req = (HttpServletRequest) servletRequest;
        HttpServletResponse resq=(HttpServletResponse) servletResponse;
        if(req.getSession().getAttribute(Constant.USER_SESSION)==null)
            resq.sendRedirect(req.getContextPath()+"/error.jsp");

        filterChain.doFilter(servletRequest,servletResponse);
    }
```



## 密码修改

项目从底层向上写。

<img src="https://i.loli.net/2021/05/25/HuoyAK4xCEzR3I8.png" alt="image-20210523202518184" style="zoom:80%;float:left" />

1. 导入前端jsp

2. 编写dao层

   ```java
       public int updatePwd(Connection conn, int id, int password) throws SQLException {
           String sql="update smbms_user set userPassword=? where id=?";
           if (conn==null) return -1;
           PreparedStatement st = conn.prepareStatement(sql);
           Object[] params={password,id};
           int i = UtilsJDBC_DBCP.executeUpdate(conn, sql, params);
           UtilsJDBC_DBCP.releaseConnection(null,st,null);
           return i;
       }
   ```

   

3. service层

   ```java
       @Override
       public boolean updatePwd(int id, int password) throws SQLException {
           Connection conn = UtilsJDBC_DBCP.getConnection();
           boolean flag=false;
           if(userDao.updatePwd(conn,id,password)>0) flag=true;
           UtilsJDBC_DBCP.releaseConnection(conn,null,null);
           return flag;
       }
   ```

4. servlet 提取方法实现复用

   ```java
   public class UserServlet extends HttpServlet {
       //实现servlet复用
       @Override
       protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           String method = req.getParameter("method");
           if(method!=null&&method.equals("savepwd")) updatePwd(req,resp);
       }
   
       @Override
       protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           doGet(req, resp);
       }
   
       public void updatePwd(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           System.out.println("UserServlet...start....");
           //从session拿id
           Object user = req.getSession().getAttribute(Constant.USER_SESSION);
           String newpassword = req.getParameter("newpassword");
           System.out.println("newpassword" + newpassword);
           if(user!=null&& !StringUtils.isNullOrEmpty(newpassword)){
               UserService userService = new UserServiceImpl();
               boolean b = false;
               try {
                   b = userService.updatePwd(((User) user).getId(), newpassword);
               } catch (SQLException e) {
                   e.printStackTrace();
               }
               if(b) {
                   System.out.println("修改成功");
                   req.setAttribute(Constant.MESSAGE, "修改成功!请重新登陆！");
                   //移除session
                   req.getSession().removeAttribute(Constant.USER_SESSION);
               }
               else req.setAttribute(Constant.MESSAGE,"修改失败!");
           }else {
               req.setAttribute(Constant.MESSAGE,"新密码无效!");
           }
           System.out.println("转发页面");
           req.getRequestDispatcher("pwdmodify.jsp").forward(req,resp);
       }
   }
   
   ```



> AJAX验证旧密码

导入json依赖

```xml
    <dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>fastjson</artifactId>
      <version>1.2.50</version>
    </dependency>
```



pwdmodify.js

```js
    oldpassword.on("blur", function () {
        $.ajax({
            type: "GET",
            url: path + "/jsp/user.do",
            data: {method: "pwdmodify", oldpassword: oldpassword.val()}, //ajax传递的参数
            dataType: "json",
            success: function (data) {
                if (data.result == "true") {//旧密码正确
                    validateTip(oldpassword.next(), {"color": "green"}, imgYes, true);
                } else if (data.result == "false") {//旧密码输入不正确
                    validateTip(oldpassword.next(), {"color": "red"}, imgNo + " 原密码输入不正确", false);
                } else if (data.result == "sessionerror") {//当前用户session过期，请重新登录
                    validateTip(oldpassword.next(), {"color": "red"}, imgNo + " 当前用户session过期，请重新登录", false);
                } else if (data.result == "error") {//旧密码输入为空
                    validateTip(oldpassword.next(), {"color": "red"}, imgNo + " 请输入旧密码", false);
                }
            },
            error: function (data) {
                //请求出错
                validateTip(oldpassword.next(), {"color": "red"}, imgNo + " 请求错误", false);
            }
        });


    }).on("focus", function () {
        validateTip(oldpassword.next(), {"color": "#666666"}, "* 请输入原密码", false);
    });
```







UserServlet

```java
    //验证旧密码,session中有用户密码
    public void pwdModify(HttpServletRequest req, HttpServletResponse resp) throws IOException {
        Object user = req.getSession().getAttribute(Constant.USER_SESSION);
        String oldpassword = req.getParameter("oldpassword");
        //万能的Map
        Map<String, String> resultMap = new HashMap<>();
        if(user==null){//session过期
           resultMap.put("result","sessionerror");
        }else if(StringUtils.isNullOrEmpty(oldpassword)){
            resultMap.put("result","error");
        }else {
            String userPassword = ((User) user).getUserPassword();
            if(oldpassword.equals(userPassword)){
                resultMap.put("result","true");
            }else {
                resultMap.put("result","false");
            }
        }
        resp.setContentType("application/json");
        PrintWriter writer = resp.getWriter();
        //JSONArray阿里巴巴的json工具类转换格式
        /*
           resultMap=["result","sessionerror","result","error"]
           json格式={k,v}
        * */
        writer.write(JSONArray.toJSONString(resultMap));
        //由于是流所以需要刷新和关闭
        writer.flush();
        writer.close();
    }
```

发起异步请求：没有刷新的情况下实现交互

<img src="https://i.loli.net/2021/05/25/MiOZHCaXq5RmrWD.png" alt="image-20210524094040867" style="zoom:80%;float:left" />



问题：转发

过滤器的问题：过滤页面和过滤请求不一样

<img src="https://i.loli.net/2021/05/25/ESbaoJVc9xL7FBU.png" alt="image-20210524101628482" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/25/QFbdjzpt4Bye8UY.png" alt="image-20210524105001842" style="zoom:80%;float:left" />



## 用户管理

采用两个Tomcat进行测试。



> 流程设计

<img src="https://i.loli.net/2021/05/25/yNP48XeiTWVbrsp.png" alt="image-20210524111224318" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/25/nmrOvcaLsHXfIQE.png" alt="image-20210524110947664" style="zoom:80%;float:left" />



1. 导入分页的工具类

2. 用户列表导入

   <img src="https://i.loli.net/2021/05/25/cbn1MYKCPo8af9x.png" alt="image-20210524112133377" style="zoom:67%;float:left" />

3. PageSupport工具类

   <img src="https://i.loli.net/2021/05/25/SMBIQfxFvrRy38t.png" alt="image-20210524111715621" style="zoom:80%;float:left" />



后端实现

---

### 用户总数

dao

```java
    //根据用户名或者角色，查询用户总数
    public int getUserCount(Connection conn,String userName,int userRole) throws SQLException;
```



```java
    //项目难点
    @Override
    public int getUserCount(Connection conn, String userName, int userRole) throws SQLException {
        StringBuffer sql=new StringBuffer();
        sql.append("select count(1) as count from smbms_user u,smbms_role r where u.userCode=r.id");
        if (conn==null) return -1;
        //list存放参数
        List<Object> lists = new ArrayList<Object>();
        if(!StringUtils.isNullOrEmpty(userName)){//拼接查询
           sql.append(" and u.userName like ?");
           lists.add("%"+userName+"%");//通配符
        }
        if (userRole>0){
           sql.append("and u.userCode =?");
           lists.add(userRole);
        }
        //如何把list转换成数组
        Object[] params = lists.toArray();
        System.out.println("UserServiceImpl:getUserCount-->"+sql.toString());//输出最后完整的sql
        ResultSet res = UtilsJDBC_DBCP.executeQuery(conn, sql.toString(), params);
        int count =0;
        if(res.next()){
            count = res.getInt("count");
        }
        UtilsJDBC_DBCP.releaseConnection(null,null,res);//conn在业务层关闭
        return count;
    }
```



service

```java
    //查询记录数
    public int getUserCount(String userName, int userRole) throws SQLException;
```

```java
    @Override
    public int getUserCount(String userName, int userRole) throws SQLException {
        Connection conn = UtilsJDBC_DBCP.getConnection();
        int count = userDao.getUserCount(conn, userName, userRole);
        UtilsJDBC_DBCP.releaseConnection(conn,null,null);
        return count;
    }
```

测试

```java
    @Test
    public void test() throws SQLException {
        UserServiceImpl userService = new UserServiceImpl();
//        User login = userService.login("admin", "1234567");
//        System.out.println(login);
        System.out.println(userService.getUserCount(null, 0));
    }
```



### 用户列表

```java
  //h获取用户列表
    List<User> getUserList(Connection conn, String userName, int userRole, int currentPageNo, int pageSize) throws Exception;
```

```java
    @Override
    public List<User> getUserList(Connection conn, String userName, int userRole, int currentPageNo, int pageSize) throws Exception {
        List<User> userList = new ArrayList<>();
        StringBuffer sql=new StringBuffer();
        sql.append("select u.*,r.roleName as userRoleName\n" +
                   "from smbms_user u,smbms_role r where\n" +
                   "u.userRole=r.id\n");
        if (conn==null) return null;
        //list存放参数
        List<Object> lists = new ArrayList<Object>();
        if(!StringUtils.isNullOrEmpty(userName)){//拼接查询
            sql.append("and u.userName like ?\n");
            lists.add("%"+userName+"%");//通配符
        }
        if (userRole>0){
            sql.append("and u.userRole =?\n");
            lists.add(userRole);
        }
        //在mysql数据库中，分页使用 limit startIndex，pageSize ; 总数
        sql.append("order by creationDate desc \n" +
                   "limit ?,?\n");
        currentPageNo=(currentPageNo-1)*pageSize;
        lists.add(currentPageNo);
        lists.add(pageSize);

        //如何把list转换成数组
        Object[] params = lists.toArray();
        System.out.println(Arrays.toString(params));
        System.out.println("UserServiceImpl:getUserList-->"+sql.toString());//输出最后完整的sql
        ResultSet res = UtilsJDBC_DBCP.executeQuery(conn, sql.toString(), params);
        while (res.next()){
            User user = new User();
            user.setId(res.getInt("id"));
            user.setUserCode(res.getString("userCode"));
            user.setUserName(res.getString("userName"));
            user.setGender(res.getInt("gender"));
            user.setBirthday(res.getDate("birthday"));
            user.setPhone(res.getString("phone"));
            user.setUserRole(res.getInt("userRole"));
            user.setUserRoleName(res.getString("userRoleName"));
            userList.add(user);
//            System.out.println("UserDaoImpl:getUserList-->"+user);
        }
        UtilsJDBC_DBCP.releaseConnection(null,null,res);//conn在业务层关闭

        return userList;
    }
```

```java
 //查询用户列表
    public List<User> getUserList(String queryUserName, int queryUserRole, int currentPageNo, int pageSize) throws Exception;
```

```java
    @Override
    public List<User> getUserList(String queryUserName, int queryUserRole, int currentPageNo, int pageSize) throws Exception {
        Connection conn = UtilsJDBC_DBCP.getConnection();
        List<User> userList = userDao.getUserList(conn, queryUserName, queryUserRole, currentPageNo, pageSize);
        UtilsJDBC_DBCP.releaseConnection(conn,null,null);
        return userList;
    }
```

```java
    @Test
    public void test() throws Exception {
        UserServiceImpl userService = new UserServiceImpl();
        List<User> userList = userService.getUserList(null, 0, 3, 3);
        for (User user : userList) {
            System.out.println(user);
        }
    }
```



### 角色列表

<img src="https://i.loli.net/2021/05/25/o3SJsgtwCc7eGn4.png" alt="image-20210524190950758" style="zoom:80%;float:left" />



至此，三条线后台代码完毕：

<img src="https://i.loli.net/2021/05/25/ZX5gi7cJW42CEFy.png" alt="image-20210524191245176" style="zoom:80%;float:left" />



接下来编写前端和控制请求：

<img src="https://i.loli.net/2021/05/25/uSARTpdF8rI64Xz.png" alt="image-20210524191328546" style="zoom:80%;float:left" />

### 用户显示servlet



<img src="https://i.loli.net/2021/05/25/3CrbBAFLQdMGk27.png" alt="image-20210524211607903" style="zoom:67%;float:left" />



```java
    //重点+难点
    public void query(HttpServletRequest req, HttpServletResponse resp) throws Exception {
        //查询用户列表
        //从前端获取数据
        String queryUserName = req.getParameter("queryname");
        String temp = req.getParameter("queryUserRole");
        String pageIndex = req.getParameter("pageIndex");
        int queryUserRole=0;

        //获取用户列表
        UserServiceImpl userService = new UserServiceImpl();
        List<User> userList=null;
        //第一次走请求，是第一页
        int pageSize=5;//页面大小固定，可以写到配置文件中
        int currentPageNo=1;

        if(queryUserName==null) queryUserName="";
        if(temp!=null&&!temp.equals("")) queryUserRole=Integer.parseInt(temp);
        if(pageIndex!=null) currentPageNo = Integer.parseInt(pageIndex);
        //获取用户总数:分页，上一页，下一页
        int totalCount = userService.getUserCount(queryUserName, queryUserRole);
        //总页数工具类
        PageSupport pageSupport = new PageSupport();
        pageSupport.setCurrentPageNo(currentPageNo);
        pageSupport.setPageSize(pageSize);
        pageSupport.setTotalPageCount(totalCount);
        int totalPageCount =-1;
        if(totalCount%pageSize==0 ) totalPageCount =totalCount/pageSize;
        else totalPageCount =totalCount/pageSize+1;
        //控制首页和尾页
        if(currentPageNo<1) currentPageNo=1;
        if(currentPageNo>totalPageCount) currentPageNo=totalPageCount;

        //获取用户列表展示
        userList = userService.getUserList(queryUserName, queryUserRole, currentPageNo, pageSize);
        req.setAttribute("userList",userList);
        RoleServiceImpl roleService = new RoleServiceImpl();
        List<Role> roleList = roleService.getRoleList();
        req.setAttribute("roleList",roleList);
        req.setAttribute("totalCount",totalCount);
        req.setAttribute("currentPageNo",currentPageNo);
        req.setAttribute("totalPageCount",totalPageCount);
        req.setAttribute("queryUserName",queryUserName);
        req.setAttribute("queryUserRole",queryUserRole);


        //返回前端
        req.getRequestDispatcher("userlist.jsp").forward(req,resp);
    }
```



### 架构分析

<img src="https://i.loli.net/2021/05/25/ZwNnfLCmQXgDrjT.png" alt="image-20210524213424301" style="zoom:80%;float:left" />



# 文件上传

> 导入依赖

```xml
    <!-- https://mvnrepository.com/artifact/commons-io/commons-io -->
    <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
      <version>2.6</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/commons-fileupload/commons-fileupload -->
    <dependency>
      <groupId>commons-fileupload</groupId>
      <artifactId>commons-fileupload</artifactId>
      <version>1.4</version>
    </dependency>
```



<img src="https://i.loli.net/2021/05/25/UkjL5vdX2ADVlhs.png" alt="image-20210525080356187" style="zoom:80%;float:left" />



> FileItem类

```jsp
<title>文件上传</title>
<body>
<%--  通过表单上传文件
      get：大小有限制 post无限制
--%>
     <form action="" enctype="multipart/form-data"  method="post">
         <p>上传用户：<input type="text" name="username"></p>
         <P><input type="file" name="file1"></P>
         <P><input type="file" name="file2"></P>
         <P><input type="submit" value="上传"> | <input type="reset" value="重置"></P>
     </form>
</body>
```

<img src="https://i.loli.net/2021/05/25/BHhLurUxP2bktKQ.png" alt="image-20210525082855083" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/05/25/6J2qKd1IXxyRHfZ.png" alt="image-20210525083025950" style="zoom:80%;float:left" />



原生态的文件上传流获取通常比较麻烦：处理上传的文件，一般需要通过流获取，我们可以使用request.getInputStream()。

建议使用Apache文件上传组件实现，common-fileupload,依赖commons-io组件。



<img src="https://i.loli.net/2021/05/25/7KIUXn9rTwGMQpy.png" alt="image-20210525092733012" style="zoom:80%;float:left" />

<img src="https://i.loli.net/2021/05/25/CWtcE3HZFKkG8Vs.png" alt="image-20210525092811267" style="zoom:80%;float:left" />





```java
public class UploadServlet extends HttpServlet {
    @SneakyThrows
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
       //判断上传的表单是普通表单还是带文件的表单
       if (!ServletFileUpload.isMultipartContent(req)) return;
       //创建保存路径，建议在web-inf目录下安全用户无法直接访问
        String upLoadRealPath = this.getServletContext().getRealPath("/WEB-INF/upload");
        File upLoadFile = new File(upLoadRealPath);
        if(!upLoadFile.exists()) upLoadFile.mkdir();
        //缓存，临时文件
        //加入文件超过预期大小我们将他放临时文件中过几天自动删除会提醒用户转永
        //创建保存路径，建议在web-inf目录下安全用户无法直接访问
        String tempRealPath = this.getServletContext().getRealPath("/WEB-INF/temp");
        File tempFile = new File(tempRealPath);
        if(!tempFile.exists()) tempFile.mkdir();

        //1.创建DiskFileItemFactory对象，处理文件上传路径或者掉限制：
        DiskFileItemFactory factory = getDiskFileItemFactory(tempFile);
        //2.获取servletFileUpload
        ServletFileUpload upload = getServletUpload(factory);
        //3.处理上传的文件
        String msg= upLoadParseRequest(upload,req,upLoadRealPath);
        //servlet请求转发消息
        req.setAttribute("msg",msg);
        req.getRequestDispatcher("info.jsp").forward(req,resp);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}

```

第一步：创建DiskFileItemFactory对象

```java
    public static DiskFileItemFactory getDiskFileItemFactory(File file){
        DiskFileItemFactory factory = new DiskFileItemFactory();
        //通过这个工厂设置缓冲区，当文件大于缓冲区的时候将他放到临时文件
        factory.setSizeThreshold(1024*1024);//1M
        factory.setRepository(file);
        return factory;
    }
```

第二步：获取servletFileUpload

```java
    public static ServletFileUpload getServletUpload(DiskFileItemFactory factory){
        ServletFileUpload upload = new ServletFileUpload(factory);
        //监听文件上传进度
        upload.setProgressListener(new ProgressListener() {
            @Override
            public void update(long l, long l1, int i) {
                System.out.println("总大小："+l1+" 已上传："+l);
            }
        });
        //处理乱码
        upload.setHeaderEncoding("UTF-8");
        //设置单个文件最大值
        upload.setFileSizeMax(1024*1024*10);
        //设置总共能够上传文件的大小
        upload.setSizeMax(1024*1024*10);
        return upload;
    }
```

第三步：上传文件

```java
    public static String  upLoadParseRequest(ServletFileUpload upload,HttpServletRequest req,String upLoadRealPath) throws FileUploadException, IOException {
        //将前端请求解析封装成一个FileItem对象,需要从servletUpload获取
        List<FileItem> fileItems = upload.parseRequest(req);
        String msg=null;
        for (FileItem fileItem : fileItems) {
            //判断上传的文件是普通的表单还是带文件的表单
            if (fileItem.isFormField()){
                String fieldName = fileItem.getFieldName();
                String value = fileItem.getString("UTF-8");
                System.out.println(fieldName + ": " + value);
            }else {
                //==============处理文件=======================
                String upLoadFieldName = fileItem.getName();
                System.out.println("upLoadFieldName=>"+upLoadFieldName);
                //文件名合法？
                if (upLoadFieldName==null||upLoadFieldName.trim().equals("")) continue;
                //获取文件名和后缀民
                String fileName = upLoadFieldName.substring(upLoadFieldName.lastIndexOf("/") + 1);
                String fileExtName = upLoadFieldName.substring(upLoadFieldName.lastIndexOf(".") + 1);
                /*网络传输中东西都需要序列化，POJO实体类要在多个电脑运行也需要继承序列化标记接口*/
                //UUID.randomUUID()生成唯一通用码
                String uuidPath = UUID.randomUUID().toString();

                //==============存放地址=======================
                String realPath = upLoadRealPath + "/" + uuidPath;
                //给每个文件创建一个文件夹
                File realFilePath = new File(realPath);
                if (!realFilePath.exists()) realFilePath.mkdir();

                //==============文件传输=======================
                InputStream in = fileItem.getInputStream();
                FileOutputStream fos = new FileOutputStream(realPath + "/" + fileName);
                byte[] buffer = new byte[1024 * 1024];
                int len=0;
                while ((len=in.read(buffer))>0){
                    fos.write(buffer,0,len);
                }
                fos.close();
                in.close();

                msg="上传成功";
                fileItem.delete();//清除临时文件
            }
        }
        return msg;
    }
```



出错点：

```java
String fieldName = fileItem.getFieldName();
区别
String upLoadFieldName = fileItem.getName();
```



上传后的文件应该在打包目录下。

```java
war模式：将WEB工程以包的形式上传到服务器 ；
war exploded模式：将WEB工程以当前文件夹的位置关系上传到服务器；//支持热部署
    
    
（1）war模式这种可以称之为是发布模式，看名字也知道，这是先打成war包，再发布；

（2）war exploded模式是直接把文件夹、jsp页面 、classes等等移到Tomcat 部署文件夹里面，进行加载部署。因此这种方式支持热部署，一般在开发的时候也是用这种方式。

（3）在平时开发的时候，使用热部署的话，应该对Tomcat进行相应的设置，这样的话修改的jsp界面什么的东西才可以及时的显示出来。

```





# 邮件发送



<img src="https://i.loli.net/2021/05/25/ZdGCLu47AUX2rSq.png" alt="image-20210525121201940" style="zoom:80%;float:left" />



收发结构图：

<img src="https://i.loli.net/2021/05/25/JzG4qLfUCvMtDNR.png" alt="image-20210525121710345" style="zoom:80%;float:left" />



发送邮件：SMTP协议；

接收邮件：POP3协议。

<img src="https://i.loli.net/2021/05/25/d5GjSqTZmxE1cAY.png" alt="image-20210525122124642" style="zoom:67%;float:left" />



## 简单邮件

> 使用Java发送邮件

<img src="https://i.loli.net/2021/05/25/E1GlIP25mqjJUX8.png" alt="image-20210525122317528" style="zoom:80%;float:left" />

包不要导错：

<img src="https://i.loli.net/2021/05/25/wDoYaSiPQnXmZ47.png" alt="image-20210525153154450" style="zoom:67%;float:left" />





<img src="https://i.loli.net/2021/05/25/5WfyVrb7sm4xLCi.png" alt="image-20210525122643329" style="zoom:80%;float:left" />



Java邮件处理程序主要有四个核心的类：

<img src="https://i.loli.net/2021/05/25/dvrUOLe5sIlSFVH.png" alt="image-20210525122732678" style="zoom:80%;float:left" />



使用JavaMail发送邮件5个步骤：

1. 创建session
2. 通过session得到transport对象
3. 使用邮箱用户名和授权码连上服务器
4. 创建邮件
5. 发送邮件



```java
//发送一封简单邮件
public class MailTest01 {
    public static void main(String[] args) throws Exception {
        Properties prop = new Properties();
        //设置邮件服务器
        prop.setProperty("mail.host","smtp.qq.com");
        //邮件发送协议
        prop.setProperty("mail.transport.protocol","smtp");
        //验证用户密码
        prop.setProperty("mail.smtp.auth","true");
        //若是qq邮箱还需下面几步设置ssl加密
        MailSSLSocketFactory sf = new MailSSLSocketFactory();
        sf.setTrustAllHosts(true);
        prop.put("mail.smtp.ssl.enable","true");
        prop.put("mail.smtp.ssl.socketFactory",sf);

        //使用JavaMail发送邮件5步骤
        //1.创建定义整个应用程序所需的环境信息的session对象
        //这段代码qq才有
        Session session = Session.getDefaultInstance(prop, new Authenticator() {
            @Override
            protected PasswordAuthentication getPasswordAuthentication() {
                //发件人邮件用户名、授权码
                return new PasswordAuthentication("3460942872@qq.com", "nrsifyrlsqsudbjb");
            }
        });
        //开启session的debug模式，可以查看程序发送Email的运行状态
        session.setDebug(true);
        //2.通过session得到transport对象
        Transport ts = session.getTransport();
        //3.使用邮箱的用户名和授权码连上邮件服务器
        ts.connect("smtp.qq.com","3460942872@qq.com","nrsifyrlsqsudbjb");
        //4.创建邮件
        //创建邮件对象
        MimeMessage message = new MimeMessage(session);
        //指明邮件发送人
        message.setFrom(new InternetAddress("3460942872@qq.com"));
        //指明邮件的收件人,自己给自己发
        message.setRecipient(Message.RecipientType.TO,new InternetAddress("1106486773@qq.com"));
        //邮件的标题
        message.setSubject("只包含文本的简单邮件");
        //邮件内容
        message.setContent("你好，邮件小程序","text/html;charset=UTF-8");
        //5.发送邮件
        ts.sendMessage(message,message.getAllRecipients());
        ts.close();

    }
}
```



<img src="https://i.loli.net/2021/05/25/Wf2cINEoZMj97bH.png" alt="image-20210525161145051" style="zoom:80%;float:left" />



## 附件邮件

<img src="https://i.loli.net/2021/05/25/ZHYRTIOpmnBfaQ3.png" alt="image-20210525161525516" style="zoom:80%;float:left" />

<img src="https://i.loli.net/2021/05/25/iaCfw1Zznxvgm3P.png" alt="image-20210525161842353" style="zoom:80%;float:left" />





> 带图片邮件

```java
//发送一封简单邮件
public class MailTest02 {
    public static void main(String[] args) throws Exception {
        Properties prop = new Properties();
        //设置邮件服务器
        prop.setProperty("mail.host","smtp.qq.com");
        //邮件发送协议
        prop.setProperty("mail.transport.protocol","smtp");
        //验证用户密码
        prop.setProperty("mail.smtp.auth","true");
        //若是qq邮箱还需下面几步设置ssl加密
        MailSSLSocketFactory sf = new MailSSLSocketFactory();
        sf.setTrustAllHosts(true);
        prop.put("mail.smtp.ssl.enable","true");
        prop.put("mail.smtp.ssl.socketFactory",sf);

        //使用JavaMail发送邮件5步骤
        //1.创建定义整个应用程序所需的环境信息的session对象
        //这段代码qq才有
        Session session = Session.getDefaultInstance(prop, new Authenticator() {
            @Override
            protected PasswordAuthentication getPasswordAuthentication() {
                //发件人邮件用户名、授权码
                return new PasswordAuthentication("3460942872@qq.com", "nrsifyrlsqsudbjb");
            }
        });
        //开启session的debug模式，可以查看程序发送Email的运行状态
        session.setDebug(true);
        //2.通过session得到transport对象
        Transport ts = session.getTransport();
        //3.使用邮箱的用户名和授权码连上邮件服务器
        ts.connect("smtp.qq.com","3460942872@qq.com","nrsifyrlsqsudbjb");
        //4.创建邮件
        //创建邮件对象
        MimeMessage message = new MimeMessage(session);
        //指明邮件发送人
        message.setFrom(new InternetAddress("3460942872@qq.com"));
        //指明邮件的收件人,自己给自己发
        message.setRecipient(Message.RecipientType.TO,new InternetAddress("1106486773@qq.com"));
        //邮件的标题
        message.setSubject("带图片的邮件");
        //==================================复杂邮件内容=======================
        //准备图片数据
        MimeBodyPart image = new MimeBodyPart();
        DataHandler dh = new DataHandler(new FileDataSource("D:\\IDEA\\MyProject\\KuangStudy\\JavaWeb\\Email\\target\\classes\\雨.png"));
        image.setDataHandler(dh);
        image.setContentID(URLEncoder.encode("雨.png","UTF-8"));
        //准备正文数据
        MimeBodyPart text = new MimeBodyPart();
        text.setContent("邮件带有<img src='cid:"+URLEncoder.encode("雨.png","UTF-8")+"'>的图片哦！","text/html;charset=UTF-8");
        //描述数据关系
        MimeMultipart mm = new MimeMultipart();
        mm.addBodyPart(text);
        mm.addBodyPart(image);
        mm.setSubType("related");
        //设置到消息中，保存修改
        message.setContent(mm);
        message.saveChanges();
        //==================================复杂邮件内容=======================
        //5.发送邮件
        ts.sendMessage(message,message.getAllRecipients());
        ts.close();

    }
}
```

<img src="https://i.loli.net/2021/05/25/Vq4pwHRUezZnajA.png" alt="image-20210525165519931" style="zoom:67%;float:left" />







> 带附件邮件

```java
//发送一封带附件邮件
public class MailTest03 {
    public static void main(String[] args) throws Exception {
        Properties prop = new Properties();
        //设置邮件服务器
        prop.setProperty("mail.host","smtp.qq.com");
        //邮件发送协议
        prop.setProperty("mail.transport.protocol","smtp");
        //验证用户密码
        prop.setProperty("mail.smtp.auth","true");
        //若是qq邮箱还需下面几步设置ssl加密
        MailSSLSocketFactory sf = new MailSSLSocketFactory();
        sf.setTrustAllHosts(true);
        prop.put("mail.smtp.ssl.enable","true");
        prop.put("mail.smtp.ssl.socketFactory",sf);

        //使用JavaMail发送邮件5步骤
        //1.创建定义整个应用程序所需的环境信息的session对象
        //这段代码qq才有
        Session session = Session.getDefaultInstance(prop, new Authenticator() {
            @Override
            protected PasswordAuthentication getPasswordAuthentication() {
                //发件人邮件用户名、授权码
                return new PasswordAuthentication("3460942872@qq.com", "nrsifyrlsqsudbjb");
            }
        });
        //开启session的debug模式，可以查看程序发送Email的运行状态
        session.setDebug(true);
        //2.通过session得到transport对象
        Transport ts = session.getTransport();
        //3.使用邮箱的用户名和授权码连上邮件服务器
        ts.connect("smtp.qq.com","3460942872@qq.com","nrsifyrlsqsudbjb");
        //4.创建邮件
        //创建邮件对象
        MimeMessage message = imageMail(session);
        //==================================复杂邮件内容=======================
        //5.发送邮件
        ts.sendMessage(message,message.getAllRecipients());
        ts.close();
    }
    public static MimeMessage imageMail(Session session) throws Exception {
        //消息的固定信息
        MimeMessage message = new MimeMessage(session);
        //指明邮件发送人
        message.setFrom(new InternetAddress("3460942872@qq.com"));
        //指明邮件的收件人
        message.setRecipient(Message.RecipientType.TO,new InternetAddress("1106486773@qq.com"));
        //邮件的标题
        message.setSubject("带附件的邮件");
        //==================================复杂邮件内容=======================
        //邮件内容：1.图片  2.附件  3.文本
        //准备图片数据
        MimeBodyPart image = new MimeBodyPart();
        DataHandler dh = new DataHandler(new FileDataSource("D:\\IDEA\\MyProject\\KuangStudy\\JavaWeb\\Email\\target\\classes\\雨.png"));
        image.setDataHandler(dh);
        image.setContentID(URLEncoder.encode("雨.png","UTF-8"));
        //准备正文数据
        MimeBodyPart text = new MimeBodyPart();
        text.setContent("邮件带有<img src='cid:"+URLEncoder.encode("雨.png","UTF-8")+"'>的图片哦！","text/html;charset=UTF-8");
        //准备附件,
        MimeBodyPart attachment = new MimeBodyPart();
        FileDataSource fileDataSource = new FileDataSource("D:\\IDEA\\MyProject\\KuangStudy\\JavaWeb\\Email\\src\\main\\resources\\ccf.pdf");
        attachment.setDataHandler(new DataHandler(fileDataSource));
        attachment.setFileName(MimeUtility.encodeText(fileDataSource.getName()));

        //描述数据关系
        MimeMultipart mm = new MimeMultipart();
        mm.addBodyPart(text);
        mm.addBodyPart(image);
        mm.setSubType("related");

        MimeBodyPart contentText = new MimeBodyPart();
        contentText.setContent(mm);

        MimeMultipart mm2 = new MimeMultipart();
        mm2.addBodyPart(attachment);
        mm2.addBodyPart(contentText);
        mm2.setSubType("mixed");

        //设置到消息中，保存修改
        message.setContent(mm2);
        message.saveChanges();
        return message;
    }
}

```



<img src="https://i.loli.net/2021/05/25/ipdVwJzWSjsTHZK.png" alt="image-20210525174044394" style="zoom:67%;float:left" />



中文乱码命名：

<img src="https://i.loli.net/2021/05/25/GNEipPC4Jn9szBS.png" alt="image-20210525174223158" style="zoom:67%;float:left" />





# 网站注册发送邮件

<img src="https://i.loli.net/2021/05/25/szDJr2TwOPHUGV8.png" alt="image-20210525174346880" style="zoom:80%;float:left" />



线程工具类

```java
//网站3秒原则：多线程实现用户体验，异步
public class SendMail extends Thread{
    private String from="3460942872@qq.com";
    private String username="大公司";
    private String password="nrsifyrlsqsudbjb";
    private String host="smtp.qq.com";
    private User user;

    public SendMail(User user) {
        this.user = user;
    }

    @SneakyThrows
    @Override
    public void run() {
        Properties prop = new Properties();
        //设置邮件服务器
        prop.setProperty("mail.host","smtp.qq.com");
        //邮件发送协议
        prop.setProperty("mail.transport.protocol","smtp");
        //验证用户密码
        prop.setProperty("mail.smtp.auth","true");
        //若是qq邮箱还需下面几步设置ssl加密
        MailSSLSocketFactory sf = new MailSSLSocketFactory();
        sf.setTrustAllHosts(true);
        prop.put("mail.smtp.ssl.enable","true");
        prop.put("mail.smtp.ssl.socketFactory",sf);

        //使用JavaMail发送邮件5步骤
        //1.创建定义整个应用程序所需的环境信息的session对象
        //这段代码qq才有
        Session session = Session.getDefaultInstance(prop, new Authenticator() {
            @Override
            protected PasswordAuthentication getPasswordAuthentication() {
                //发件人邮件用户名、授权码
                return new PasswordAuthentication("3460942872@qq.com", "nrsifyrlsqsudbjb");
            }
        });
        //开启session的debug模式，可以查看程序发送Email的运行状态
        session.setDebug(true);
        //2.通过session得到transport对象
        Transport ts = session.getTransport();
        //3.使用邮箱的用户名和授权码连上邮件服务器
        ts.connect(host,username,password);
        //4.创建邮件
        //创建邮件对象
        MimeMessage message = new MimeMessage(session);
        //指明邮件发送人
        message.setFrom(new InternetAddress(from));
        //指明邮件的收件人,自己给自己发
        message.setRecipient(Message.RecipientType.TO,new InternetAddress(user.getEmail()));
        //邮件的标题
        message.setSubject("欢迎注册！");
        String info="注册成功，您的用户名为："+user.getUsername()+"\n密码为为："+user.getPassword()+"\n祝您使用愉快";
        message.setContent(info,"text/html;charset=UTF-8");
        message.saveChanges();
        //5.发送邮件
        ts.sendMessage(message,message.getAllRecipients());
        ts.close();
    }
}
```



```java
public class RegisterServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //接收用户请求封装成对象
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String email = req.getParameter("email");
        User user = new User(username, password, email);
        //专门用线程发送邮件防止出现耗时
        SendMail send = new SendMail(user);
        send.start();
        req.setAttribute("message","注册成功，查看邮箱接收信息，若网络不稳定可能过会才收到！");
        req.getRequestDispatcher("info.jsp").forward(req,resp);
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

<img src="https://i.loli.net/2021/05/25/xUqazIVB5jgpNdK.png" alt="image-20210525202732150" style="zoom:50%;float:left" />

<img src="https://i.loli.net/2021/05/25/6BUk8EPxwQoWVuO.png" alt="image-20210525202705048" style="zoom:67%;float:left" />



# 后序学习

思想的学习：



<img src="https://i.loli.net/2021/05/25/5gVdG89XvPcRyxF.png" alt="image-20210525204357028" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/25/SAgxuypOTDwXLhj.png" alt="image-20210525204540250" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/25/YEnL7BvXeM9wlTt.png" alt="image-20210525204824138" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/25/DUFB42Czwe6aItT.png" alt="image-20210525205138118" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/05/25/mNZfrs8DEio2MYz.png" alt="image-20210525205215764" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/25/Yvr4bncOF26StR3.png" alt="image-20210525205405325" style="zoom:80%;float:left" />



补充：

<img src="https://i.loli.net/2021/05/25/oyJfpj97iwWK6zC.png" alt="image-20210525205513830" style="zoom:67%;float:left" />