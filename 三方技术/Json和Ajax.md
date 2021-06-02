JSON和AJAX

预备知识：

- springMVC

  - Controller
  - springmvc配置文件
  - web.xml

- JavaScript

  - 引入javaScript  <script>
  - 函数

- 选择器

  - 标签选择器
  - 类选择器
  - id选择器

- jQuery公式

  - $(选择器).时间(参数)
  - $(select).action(...)

  

----

**web1.0**:登录失败需要刷新页面才能重新登录，没有异步刷新，局部刷新功能。不点击提交按钮就不知道自己错了，还有手机号重复没有提示。

**web2.0:**最重要因素之一Ajax

---



<img src="https://i.loli.net/2021/05/26/lG81kwmbytFeO27.png" alt="image-20210525213339725" style="zoom:67%;float:left" />

# Json

## 概述

<img src="https://i.loli.net/2021/05/26/1ms8X25AWlHF93Z.png" alt="image-20210525213300470" style="zoom:80%;float:left" />

- 对象表示为键值对
- 数据由逗号分隔
- 花括号保存对象
- 方括号保存数组

JSON是JS对象的字符串表示法，本质是字符串。

```java
var obj={a:'hello',b:'word'};//js对象

var json='{"a":"hello","b":"world"}';//json字符串
```

## 转换

JSON字符串-->JS对象

```java
var obj=JSON.parse('{"a":"hello","b":"world"}')
```



JS对象-->JSON字符串

```java
var json=JSON.stringify({a:'hello',b:'word'});
```



前后端分离，数据交互变得异常重要，JSON在效率方面很好。

```html
<script>
    //编写一个对象
    let user={
        name:"吕布",
        age:2000,
        sex:"男"
    };//输出
    console.log(user);
    //js对象---》转换为json字符串
    let json=JSON.stringify(user);
    console.log(json);
    console.log(JSON.parse(json));
</script>
```



抓取百度服务器响应地址：

查看网页源代码：

```java
 sugHost : "https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su",
```

<img src="https://i.loli.net/2021/05/26/kPGE7jrFRqyKvHh.png" alt="image-20210525221303969" style="zoom:50%;float:left" />

## Controller返回Json

导入环境依赖：spring-webmvc

```xml
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.1</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.3.4</version>
        </dependency>
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>servlet-api</artifactId>
            <version>2.5</version>
        </dependency>
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>jsp-api</artifactId>
            <version>2.2</version>
        </dependency>
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.12</version>
        </dependency>
    </dependencies>
```

静态资源过滤问题：

```xml
 <build>
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
                </includes>
                <filtering>false</filtering>
            </resource>
        </resources>
    </build>
```



编写springmvc-servlet.xml配置文件：注意归类时候可能不被web.xml识别

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd
       http://www.springframework.org/schema/mvc
       https://www.springframework.org/schema/mvc/spring-mvc.xsd">

    <!--   自动扫描包交由Ioc容器管理-->
    <context:component-scan base-package="com.mf.controller"/>
    <!--    视图解析器-->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver" id="internalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/jsp/"/>
        <property name="suffix" value=".jsp"/>
    </bean>
    <!--  JSON乱码问题配置-->
    <mvc:annotation-driven>
        <mvc:message-converters register-defaults="true">
            <bean class="org.springframework.http.converter.StringHttpMessageConverter">
                <constructor-arg value="UTF-8"/>
            </bean>
            <bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
                <property name="objectMapper">
                    <bean class="org.springframework.http.converter.json.Jackson2ObjectMapperFactoryBean">
                        <property name="failOnEmptyBeans" value="false"/>
                    </bean>
                </property>
            </bean>
        </mvc:message-converters>
    </mvc:annotation-driven>

</beans>
```



编写web.xml配置文件

```xml
    <!--    dispatcherServlet-->
    <servlet>
        <servlet-name>springmvc</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:springmvc-servlet.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>springmvc</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
    <!--    Filter过滤器-->
    <filter>
        <filter-name>encodingFilter</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>encodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>

```



导入fackjson包

```xml
    <dependency>
      <groupId>com.fasterxml.jackson.core</groupId>
      <artifactId>jackson-databind</artifactId>
      <version>2.11.4</version>
    </dependency>
```



编写controller

```java
@Controller
public class UserController {

    @RequestMapping("/json1")
    //RequestMapping正常返回会走视图解析器，而json只需要返回json字符串而已
    //使用三方工具：Jackson，fastjson
    //@ResponseBody将服务器返回的对象转换为json对象返回
    @ResponseBody
    public String json1() throws JsonProcessingException {
        //需要Jackson的对象映射器，将对象转换成字符串
        ObjectMapper mapper = new ObjectMapper();
        //创建对象
        User user = new User("上官婉儿", 1, "女");
        System.out.println(user);
        //将对象转为字符串
        String json = mapper.writeValueAsString(user);
        System.out.println(json);
        return  json;//不会转到视图解析器
    }
    //如果有前端输出有乱码问题
    @RequestMapping(value = "/json2",produces = "application/json;charset=utf-8")
    @ResponseBody
    public String json2() throws JsonProcessingException {
        ObjectMapper mapper = new ObjectMapper();
        return mapper.writeValueAsString(new User("上官婉儿", 1, "女"));
    }
}

```



乱码问题统一配置文件解决

<img src="https://i.loli.net/2021/05/26/1Vo4fpsD7vA8tnh.png" alt="image-20210526093820192" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/26/Pa4wGr5OZ29mAXu.png" alt="image-20210526093038491" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/05/26/mbTwq7OsFLkzVxv.png" alt="image-20210526093107706" style="zoom:67%;float:left" />

输出list集合

```java
    @RequestMapping(value = "/json3")
    @ResponseBody
    public String json3() throws JsonProcessingException {
        List<User> list = new ArrayList<>();
        list.add(new User("上官婉儿1", 1, "女"));
        list.add(new User("上官婉儿2", 2, "女"));
        list.add(new User("上官婉儿3", 3, "女"));
        list.add(new User("上官婉儿4", 4, "女"));

        return new ObjectMapper().writeValueAsString(list);
    }
```



JSON格式化：

<img src="https://i.loli.net/2021/05/26/ibN6vtZzs24YVDH.png" alt="image-20210526095714168" style="zoom:67%;float:left" />



date输出格式:时间默认返回json字符串变成时间戳格式

```java
    @RequestMapping(value = "/time")
    @ResponseBody
    public String json4() throws JsonProcessingException {
        Date date = new Date();
        System.out.println(date);
        return new ObjectMapper().writeValueAsString(date);
    }
```

<img src="https://i.loli.net/2021/05/26/2dY5IEVCgPQzLN6.png" alt="image-20210526100841187" style="zoom:80%;float:left" />

前端输出时间戳：

<img src="https://i.loli.net/2021/05/26/7EIy51sLBdAHWqO.png" alt="image-20210526100926436" style="zoom:67%;float:left" />



解决：

```java
    @RequestMapping(value = "/time2")
    @ResponseBody
    public String json5() throws JsonProcessingException {
        ObjectMapper mapper = new ObjectMapper();
        //1.如何不返回时间戳,关闭
        mapper.configure(SerializationFeature.WRITE_DATE_KEYS_AS_TIMESTAMPS,false);
        //2.如何解决时间格式化问题
        SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH-mm-ss");
        //3.指定mapper时间格式
        mapper.setDateFormat(dateFormat);
        Date date = new Date();
        System.out.println(dateFormat.format(date));
        return mapper.writeValueAsString(date);
    }
```

<img src="https://i.loli.net/2021/05/26/I8XHOMmJuceY6ir.png" alt="image-20210526102256921" style="zoom:67%;float:left" />

> 重复代码封装成工具类

```java
public class JsonUtils {
    //重载
    public static String getJson(Object object) throws JsonProcessingException {
        return getJson(object,"yyyy-MM-dd HH-mm-ss");
    }
    public static String getJson(Object object,String format) throws JsonProcessingException {
        ObjectMapper mapper = new ObjectMapper();
        //1.如何不返回时间戳,关闭
        mapper.configure(SerializationFeature.WRITE_DATE_KEYS_AS_TIMESTAMPS,false);
        //2.如何解决时间格式化问题
        SimpleDateFormat dateFormat = new SimpleDateFormat(format);
        //3.指定mapper时间格式
        mapper.setDateFormat(dateFormat);

        return mapper.writeValueAsString(object);
    }
}

```

```java
    @RequestMapping(value = "/time3")
    @ResponseBody
    public String json6() throws JsonProcessingException {
        return JsonUtils.getJson(new Date());
    }

    @RequestMapping(value = "/json7")
    @ResponseBody
    public String json7() throws JsonProcessingException {
        List<User> list = new ArrayList<User>();
        list.add(new User("上官婉儿1", 1, "女"));
        list.add(new User("上官婉儿2", 2, "女"));
        list.add(new User("上官婉儿3", 3, "女"));
        list.add(new User("上官婉儿4", 4, "女"));

        return JsonUtils.getJson(list);
    }
```





## 小结

异步数据交互：

@ResponseBody注解将对象转换位json字符串直接返回不走视图解析器；

@RequestBody则用来接收前台json字符串转换java对象。



# Ajax

## 概述

<img src="https://i.loli.net/2021/05/26/Q7svWid5EmhYxtI.png" alt="image-20210526104155486" style="zoom:67%;float:left" />

使用Ajax创建动态性极强Web页面：当在搜索框输入关键字时候，JS将字符发送服务器返回搜索建议列表，增强B/S体验性。

用途：

- 注册时，输入用户名自动监测用户是否存在；
- 登录时，提示用户名和密码错误；
- 删除数据行，行id发送到后台在数据库删除后在页面dom也删除数据行。

## iframe

前端伪造ajax。

```html
<head>
    <meta charset="UTF-8">
    <title>iframe</title>
    <style>
        .div1{
            width: 300px;
            height: 200px;
            margin: 20px auto;
            background: url("../resources/1.jpg") 0 0 no-repeat;
            opacity: 0.7;
        }
        iframe{
            width: 100%;
            height: 500px;
        }
        h3{
            text-align: center;
        }
        p{
            margin-top: 10%;
            margin-left: 30%;
        }
    </style>
</head>
<body>
<script>
    //窗口加载的时候就会加载这个函数
     window.onload=function time(){
         let date=new Date();
         document.getElementById(`currentTime`).innerText=date.getTime();
     }
     function loadPage(){
        let pageUrl=document.getElementById(`url`).value;
        console.log(pageUrl);
        document.getElementById(`iframePosition`).src=pageUrl;
     }
</script>

<div class="div1">

    <p>输入要加载的地址：<span id="currentTime"></span></p>
    <p><label for="url"></label><input type="text" id="url"></p>
    <p><input type="button" value="加载" onclick="loadPage()"></p>

</div>
<div class="div2">
    <h3>加载页面的位置：</h3>
    <iframe id="iframePosition">

    </iframe>
</div>
</body>
```



<img src="https://i.loli.net/2021/05/26/SOsg9N4AFYIWdPX.png" alt="image-20210526113444886" style="zoom:80%;float:left" />



## jQuery



纯JS实现Ajax:本质使用XMLHttpServletRequest实现，XHR对象。

XHR对象：向服务器发送请求和接收响应提供接口，以异步方式获取数据。

我们直接使用jQuery封装的Ajax：方便调用！

```js
jQuery.get(...)
jQuery.post(....)
jQuery.getJSON(...)
所有参数：
url:待加载的url地址
data:待发送的Key/value参数
success:载入成功调回函数
dataType:返回内容格式xml,json,script,text,html
```



```js
jQuery.ajax(..)
所有参数：
url:请求地址
type:请求方式
headers:请求头
data:要发送数据
contentType:即将发送信息到服务器的内容编码类型默认("application/..;charset=utf-8")
async:是否异步
timeout:设置请求超时时间毫秒
beforeSend:发送请求前执行的函数
complete:完成后执行的回调函数
success:成功后执行的回调函数
error:失败后执行的回调函数
accepts:通过请求头告诉服务器当前客户接受的数据类型
dataType:将服务器返回的内容转换成普通文本格式
```



Springmvc中访问静态资源需要加上：

```xml
    <mvc:default-servlet-handler/>
```



导入库jQuery或者在线cdn：

```html
<script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
<script src="${pageContext.request.contextPath}/statics/js/jquery-3.1.1.min.js"></script>
```



```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Ajax</title>
    <style>
        .div1{
            margin: 100px 100px;
            background: url("statics/image/1.jpg") 0 0 no-repeat;
            opacity: 0.7;
            text-align: center;
        }
        .div2{
            width: 200px;
            height: 100px;
            margin: 20px auto;
            background: #39e888;
            opacity: 0.6;
        }
    </style>
    <script src="${pageContext.request.contextPath}/statics/js/jquery-3.6.0.js"></script>
</head>
<body>

    <script>
        function a1(){
            //将文本框值发给服务器并接收服务器返回的数据
            //success:function (data)回调函数data封装了服务器返回数据和状态
            $.ajax({
              url: "${pageContext.request.contextPath}/ajax/a1",
              data: {"name":$("txtName").val()},
              success:function (data){
                  console.log(data);
              }
            });

        }
    </script>

    <div class="div1">
        <div class="div2">
            <p>
                <span>用户名：</span>
                <label>
                    <%-- 失去焦点产生时间--%>
                    <input type="text" name="txtName" onblur="a1()">
                </label>
            </p>
            <p>
                <input type="button" value="提交">
            </p>
        </div>
    </div>
</body>
</html>
```



```java
@Controller
@RequestMapping("/ajax")
public class AjaxController {
    //第一种方式：服务器返回一个字符串，直接使用response
    @RequestMapping("/a1")
    public void ajax01(String name, HttpServletResponse resp) throws IOException {
       if("admin".equals(name)) resp.getWriter().write("true");
       else resp.getWriter().write("false");
    }

    @RequestMapping("/a2")
    @ResponseBody
    public List<User> ajax02(){
        List<User> list = new ArrayList<User>();
        list.add(new User("上官婉儿1", 1, "女"));
        list.add(new User("上官婉儿2", 2, "女"));
        list.add(new User("上官婉儿3", 3, "女"));
        list.add(new User("上官婉儿4", 4, "女"));
        return list;
    }
}
```

<img src="https://i.loli.net/2021/05/26/Msr1qzhV2GEdWPZ.png" alt="image-20210526162612150" style="zoom:80%;float:left" />

问题：需要用标签选择器才能正确传值，，建议今后都用标签取值。

<img src="https://i.loli.net/2021/05/26/AKgquk2NVjImvr9.png" alt="image-20210526165713274" style="zoom:80%;float:left" />

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Ajax02</title>
    <script src="${pageContext.request.contextPath}/statics/js/jquery-3.6.0.js"></script>
    <style>
        div{
            width: 400px;
            height: 300px;
            margin: 20px auto;
            background: #39e888;
            opacity: 0.6;
            text-align: center;
        }
        table{
            margin-top: 25px;
            margin-left: 10%;
            width: 270px;
        }
        table,tr,td,th{
            border: 1px solid red;
            padding: 2px;
        }
    </style>
</head>
<body>
<script>
<%--  一进来就执行此函数--%>
    $(function (){
        $("#btn").click(function (){
            $.post({
                url: "${pageContext.request.contextPath}/ajax/a2",
                success: function (data){
                  console.log(data);
                  let html="";
                  for (let i=0;i<data.length;i++){
                      html+="<tr>"+
                               "<td>"+data[i].name+"</td>"+
                               "<td>"+data[i].age+"</td>"+
                               "<td>"+data[i].sex+"</td>"+
                            "</tr>"
                  }
                  $("#content").html(html);
                }
            })
        })
    })
</script>

<div>
    <input type="button" id="btn" value="加载数据">
    <table>
        <tr>
            <td>姓名</td>
            <td>年龄</td>
            <td>性别</td>
        </tr>
        <tbody id="content">

        </tbody>
    </table>
</div>
</body>
</html>

```

<img src="https://i.loli.net/2021/05/26/TDw1KXGoHeOLaVi.png" alt="image-20210526171604115" style="zoom:67%;float:left" />



```java
    @RequestMapping("/a3")
    @ResponseBody
    public String ajax03(String name, String pwd) {
          String msg="";
          if (name!=null){
              if ("admin".equals(name)) msg="ok";
              else msg="error";
          }
        if (pwd!=null){
            if ("123".equals(pwd)) msg="ok";
            else msg="error";
        }
        return msg;
    }
```



```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Ajax</title>
    <style>
        .div1{
            margin: 100px 100px;
            background: url("statics/image/1.jpg") 0 0 no-repeat;
            opacity: 0.7;
        }
        .div2{
            width: 400px;
            height: 150px;
            margin: 20px auto;
            background: #39e888;
            opacity: 0.6;
        }
    </style>
    <script src="${pageContext.request.contextPath}/statics/js/jquery-3.6.0.js"></script>
</head>
<body>

<script>
    function a1(){
        //将文本框值发给服务器并接收服务器返回的数据
        //success:function (data)回调函数data封装了服务器返回数据和状态
        $.post({
            url: "${pageContext.request.contextPath}/ajax/a3",
            data: {"name":$("#txtName").val()},
            success:function (data){
                console.log("name:"+data.toString());
                if (data.toString()==="ok") $("#nameInfo").css("color","green");
                else $("#nameInfo").css("color","red");
                $("#nameInfo").html(data)
            }
        });
    }
    function a2(){
        $.post({
            url: "${pageContext.request.contextPath}/ajax/a3",
            data: {"pwd":$("#txtWord").val()},
            success:function (data){
                console.log("pwd:"+data.toString());
                if (data.toString()=="ok") $("#pwdInfo").css("color","yellow");
                else $("#pwdInfo").css("color","red");
                $("#pwdInfo").html(data)
            }
        });
    }
</script>

<div class="div1">
    <div class="div2">
        <p>
            <span>用户名：</span>
            <input type="text" name="username" id="txtName" onblur="a1()">
            <span id="nameInfo"></span>

        </p>
        <p>
            <span>密码：</span>
            <input type="text" name="password" id="txtWord" onblur="a2()">
            <span id="pwdInfo"></span>
        </p>
        <p>
            <input type="button" value="提交">
        </p>
    </div>
</div>
</body>
</html>

```

<img src="https://i.loli.net/2021/05/26/J7VTRtKu6CdqQlI.png" alt="image-20210526175744593" style="zoom:67%;float:left" />

> 总结

<img src="https://i.loli.net/2021/05/26/fjlos8HugdTUrm1.png" alt="image-20210526180001000" style="zoom:67%;float:left" />



































