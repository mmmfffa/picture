[[我的工作台 - Gitee.com](https://gitee.com/ma-fu/dashboard/projects)]:



# 开篇 #

ssm: mybatis+Spring+SpringMVC      **MVC三层架构**

MVC：模型(dao,service)   视图(jsp)   控制器(servlet)

MVVM:M V VM    viewModle  双向绑定

servlet:转发，重定向



JavaSE: 认真学习，老师带，入门快；

JavaWeb：认真学习，老师带，入门快；

SSM框架：研究官方文档，锻炼自学能力，锻炼项目能力。



后续学习……

SpringMVC+Vue+SpringBoot+SpringCloud+Linux



**框架整合**    SSM=JavaWeb做项目；



Spring：**IOC和AOP**

SpringMVC：**SpringMVC的执行流程！**   **SSM框架整合**

# SpringMVC简介 #

## 什么MVC ##

**MVC主要作用是降低了视图与业务逻辑之间的双向耦合。**

最典型的MVC：JSP+servlet+javabean

**MVC框架要做那些事情**

- 将url映射到java类或java类的的方法
- 封装用户提交的数据
- 处理请求--调用相关的业务处理--封装响应数据
- 将响应的数据进行渲染.jsp/html等表示层数据

常见的服务器MVC框架：Structs,Spring MVC,ASP.NET MVC,ZendFramework,JSF;

常见的前端MVC框架：Vue,angularjs,react,backbone;

由MVC演化的另外一些模式：MVP,MVVM……

## 什么是SpringMVC ##

### 概述 ###

Spring MVC是Spring Framework的一部分，是基于Java实现MVC的轻量级Web框架。

**Spring的web框架围绕DispatcherServlet[调度Servlet]设计**

### 中心控制器 ###

SpringMVC以请求为驱动 , 围绕一个中心Servlet分派请求及提供其他功能，DispatcherServlet是一个实际的Servlet (它继承自HttpServlet 基类)。

### SpringMVC执行原理 ###

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7KwPOPWq00pMJiaK86lF6BjIbmPOkY8TxF6qvGAGXxC7dArYcr8uJlWoVC4aF4bfxgCGCD8sHg8mgw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

# 回顾servlet #

## pom.xml依赖 ##

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
    </dependencies>

```

## 新建一个Moudle,添加web app的支持 ##

## 编写Servlet类，处理用户请求 ##

```java
package com.kuang.servlet;

//实现Servlet接口
public class HelloServlet extends HttpServlet {
   @Override
   protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
       //取得参数
       String method = req.getParameter("method");
       if (method.equals("add")){
           req.getSession().setAttribute("msg","执行了add方法");
      }
       if (method.equals("delete")){
           req.getSession().setAttribute("msg","执行了delete方法");
      }
       //业务逻辑
       //视图跳转
       req.getRequestDispatcher("/WEB-INF/jsp/hello.jsp").forward(req,resp);
  }

   @Override
   protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
       doGet(req,resp);
  }
}
```

## 编写JSP ##

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
   <title>Kuangshen</title>
</head>
<body>
${msg}
</body>
</html>
```

## 在web.xml中注册Servlet ##

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
        version="4.0">
   <servlet>
       <servlet-name>HelloServlet</servlet-name>
       <servlet-class>com.kuang.servlet.HelloServlet</servlet-class>
   </servlet>
   <servlet-mapping>
       <servlet-name>HelloServlet</servlet-name>
       <url-pattern>/user</url-pattern>
   </servlet-mapping>

</web-app>

```

## 配置Tomcat，并启动测试 ##

## 热部署 ##

- 项目运行时build   (设置setting)
- 项目运行时make (regitry)
- 预编译 build project
- tomcat热部署设置

# 第一个SpringMVC程序 #

## 配置版 ##

### 新建mvc项目 ###

- 新建Moudle，添加web支持

- 确定导入SpringMVC依赖

- 配置web.xml，注册DispatcherServlet

  ```xml
   <!--1.注册servlet-->
     <servlet>
         <servlet-name>SpringMVC</servlet-name>
         <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
         <!--通过初始化参数指定SpringMVC配置文件的位置，进行关联-->
         <init-param>
             <param-name>contextConfigLocation</param-name>
             <param-value>classpath:springmvc-servlet.xml</param-value>
         </init-param>
         <!-- 启动顺序，数字越小，启动越早 -->
         <load-on-startup>1</load-on-startup>
     </servlet>
  
     <!--所有请求都会被springmvc拦截 -->
     <servlet-mapping>
         <servlet-name>SpringMVC</servlet-name>
         <url-pattern>/</url-pattern>
     </servlet-mapping>
  ```

  

- 编写SpringMVC的配置文件!名称： [servletname]-servlet.xml

- 添加映射处理器,添加处理器适配器

  ```xml
   <bean class="org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping"/>
        <bean class="org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter"/>
        <!--视图解析器:DispatcherServlet给他的ModelAndView-->
        <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver" id="InternalResourceViewResolver">
              <!--前缀-->
              <property name="prefix" value="/WEB-INF/jsp/"/>
              <!--后缀-->
              <property name="suffix" value=".jsp"/>
        </bean>
  ```

  

- 添加视图解析器

- 编写我们要操作的业务Controller,要么实现Controller接口，要么增加注解

；需要返回一个ModelAndView，装数据，封视图

- 将自己的类交给SpringIOC容器，注册bean
- 写要跳转的jsp页面，显示ModelAndView存放的数据已经我们的正常页面；
- 配置Tomcat启动测试

实际开发中不会这么干

可能遇到的问题：访问出现404

排查步骤：

- 查看控制台输出，看是否缺少jar包

- 查看IDEA的项目发布中添加lib依赖！

  ![img](file:///C:\Users\Administrator\AppData\Roaming\Tencent\Users\3460942872\QQ\WinTemp\RichOle\_641B_]8`O{8B4A5P@U`707.png)

- 重现build项目，启动Tomcat！

### web5.0版本没有智能提示 ###

将web.xml5.0换为web.xml4.0

![img](file:///C:\Users\Administrator\Documents\Tencent Files\3460942872\Image\C2C\OH_[1G~R@~HH%NQPC]RB0FT.jpg)

## 注解版本 ##

### 步骤 ###

- 新建Moudle ,添加web支持

- 由于Maven可能存在静态资源过滤问题，将配置完善

- pom.xml引入相关依赖，主要有Spring框架核心库，SpringMVC ,servlet,JSTL,一般在在父工程中已经引入。

- 配置web.xml

- 添加SpringMVC配置文件

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:context="http://www.springframework.org/schema/context"
         xmlns:mvc="http://www.springframework.org/schema/mvc"
         xsi:schemaLocation="http://www.springframework.org/schema/beans
         http://www.springframework.org/schema/beans/spring-beans.xsd
         http://www.springframework.org/schema/context
         https://www.springframework.org/schema/context/spring-context.xsd
         http://www.springframework.org/schema/mvc
         https://www.springframework.org/schema/mvc/spring-mvc.xsd">
  
      <!-- 自动扫描包，让指定包下的注解生效,由IOC容器统一管理 -->
      <context:component-scan base-package="com.mf.controller"/>
      <!-- 让Spring MVC不处理静态资源 -->
      <mvc:default-servlet-handler />
      <!--
      支持mvc注解驱动
          在spring中一般采用@RequestMapping注解来完成映射关系
          要想使@RequestMapping注解生效
          必须向上下文中注册DefaultAnnotationHandlerMapping
          和一个AnnotationMethodHandlerAdapter实例
          这两个实例分别在类级别和方法级别处理。
          而annotation-driven配置帮助我们自动完成上述两个实例的注入。
       -->
      <mvc:annotation-driven />
  
      <!-- 视图解析器 -->
      <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver"
            id="internalResourceViewResolver">
          <!-- 前缀 -->
          <property name="prefix" value="/WEB-INF/jsp/" />
          <!-- 后缀 -->
          <property name="suffix" value=".jsp" />
      </bean>
  
  </beans>
  ```

  

- 创建Controller

- 创建视图层

- 配置Tomcat运行

### Maven可能存在资源过滤问题 ###

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

# 控制器Controller和RestFul风格 #

## 控制器Controller ##

通常通过接口定义或注解定义两种方法实现。

解析请求转换成模型。

SpringMVC中一个控制器类可包含多个方法，SpringMVC中Controller的配置方式有很多种。

### 实现Controller接口 ###

1.编写一个Controler类

```java
//定义控制器
//注意点：不要导错包，实现Controller接口，重写方法；
public class ControllerTest1 implements Controller {

   public ModelAndView handleRequest(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse) throws Exception {
       //返回一个模型视图对象
       ModelAndView mv = new ModelAndView();
       mv.addObject("msg","Test1Controller");
       mv.setViewName("test");
       return mv;
  }
}
```

2.去Spring配置文件中注册请求的Bean,name对应请求路径，class对应处理请求的类

```xml
<bean name="/t1" class="com.kuang.controller.ControllerTest1"/>
```

3.编写test.jsp

4.Tomcat运行

说明：实现Controller定义控制器是比较老的方法。

一个控制器中只有一个方法，如果要多个方法需要定义多个Controller。

## 使用注解@Controller ##

- @Controller注解类型用于声明Spring类的实例是一个控制器

- 组件扫描

  ```xml
  <!-- 自动扫描指定的包，下面所有注解类交给IOC容器管理 -->
  <context:component-scan base-package="com.kuang.controller"/>
  ```

- 编写Controller类，使用注解实现

  ```java
  //@Controller注解的类会自动添加到Spring上下文中
  @Controller
  public class ControllerTest2{
  
     //映射访问路径
     @RequestMapping("/t2")
     public String index(Model model){
         //Spring MVC会自动实例化一个Model对象用于向视图中传值
         model.addAttribute("msg", "ControllerTest2");
         //返回视图位置
         return "test";
    }
  
  }
  ```

- Tomcat测试

## 四个注解 ##


```java
  @Component 组件
  @Service   service
  @Controller  controller
  @Repository   dao
```

  

  我们的两个请求都可以指向一个视图，但是页面结果的结果是不一样的，从这里可以看出视图是被复用的，而控制器与视图之间是弱偶合关系。

## @RequestMapping ##

用于映射url到控制器类或一个特定的处理程序方法。可用于类或方法上。用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。

RestFul风格

### 简介 ###

RestFul风格就是一个资源定位以及资源操作的风格。不是标准也不是协议，只是一种风格。基于这个风格的设计的软件更加简洁，更有层次，更加易于实现缓存等机制。

资源：互联网的所有事物称之为资源。

- 传统范式操作资源
- 使用RESTful操作资源

### 学习测试 ###

1.编写RestFulController类

2.SpringMVC上使用@PathVariable注解，让方法参数的值对应绑定到一个URI模板变量上。

3.测试

tip：

1.改动java代码：Redeloy

![img](file:///C:\Users\Administrator\Documents\Tencent Files\3460942872\Image\C2C\V2BTTRMT93(CLMI@)30EU7L.png)

2.改动配置文件，重新启动tomcat

3.改动前端，刷新一下

### 常用请求注解

- @GETMapping(path:)
- @POSTMaping(path:)



# 重定向和转发

springmvc结果跳转方式：

1. modelAndview

   页面：{视图解析器前缀}+viewName+{视图解析器后缀}

2. 原生ServletAPI

   通过HttpServletResponse进行输出，重定向，转发。

   sendRedirect();

   getRequestDispatcher().fowward();

3. springmvc实现转发和重定向，无需视图解析器

   springmvc默认是转发；

   加redirect后就是重定向。有视图重定向。



#    数据处理

   ## 处理提交数据

   ![image-20210411215642884](https://i.loli.net/2021/05/20/zlZ67VHR9wXWytL.png)



访问web目录下的index.jsp路径问题：**req.getContextPath()+"/index.jsp"**

![image-20210412203044223](https://i.loli.net/2021/05/20/4UaOZeThQM5psLE.png)



## 乱码处理

请求方式的问题

添加springmvc的过滤器

```xml
<filter>
   <filter-name>encoding</filter-name>
   <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
   <init-param>
       <param-name>encoding</param-name>
       <param-value>utf-8</param-value>
   </init-param>
</filter>
<filter-mapping>
   <filter-name>encoding</filter-name>
   <url-pattern>/*</url-pattern>
</filter-mapping>
```

<url-pattern>/*</url-pattern>

注意这里是/*,处理包括jsp的页面，否则过滤器对前端的处理无法生效。





# 整合SSM

## pom依赖

junit,数据库驱动，数据库连接池c3p0，servletJSp(servletapi,jspapi,jstl)，mybatis(mybatis和mybatis-spring),spring(springmvc和springjdbc),静态资源过滤；

```xml
<dependencies>
   <!--Junit-->
   <dependency>
       <groupId>junit</groupId>
       <artifactId>junit</artifactId>
       <version>4.12</version>
   </dependency>
   <!--数据库驱动-->
   <dependency>
       <groupId>mysql</groupId>
       <artifactId>mysql-connector-java</artifactId>
       <version>5.1.47</version>
   </dependency>
   <!-- 数据库连接池 -->
   <dependency>
       <groupId>com.mchange</groupId>
       <artifactId>c3p0</artifactId>
       <version>0.9.5.2</version>
   </dependency>

   <!--Servlet - JSP -->
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

   <!--Mybatis-->
   <dependency>
       <groupId>org.mybatis</groupId>
       <artifactId>mybatis</artifactId>
       <version>3.5.2</version>
   </dependency>
   <dependency>
       <groupId>org.mybatis</groupId>
       <artifactId>mybatis-spring</artifactId>
       <version>2.0.2</version>
   </dependency>

   <!--Spring-->
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-webmvc</artifactId>
       <version>5.1.9.RELEASE</version>
   </dependency>
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-jdbc</artifactId>
       <version>5.1.9.RELEASE</version>
   </dependency>
</dependencies>


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

## 基本结构和配置装置

```
com.mf.pojo
com.mf.dao
com.mf.service
com.mf.controller
```

mybatis-config.xml:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
       PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
       "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>

</configuration>
```

applcationContext.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">

</beans>
```

mybatis层：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
       PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
       "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
   
   <typeAliases>
       <package name="com.kuang.pojo"/>
   </typeAliases>
   <mappers>
       <mapper resource="com/kuang/dao/BookMapper.xml"/>
   </mappers>

</configuration>
```

**编写pojo实体类！**

**编写dao的Mapper接口！**

**编写接口对应的Mapper.xml！**

编写service层的接口和实现类

底层操作完毕！！！

## spring层整合mybatis

配置spring整合mybatis,数据源使用c3p0连接池；

spring整合mybatis配置文件：spring-dao.xml

1.整合mybatis，关联数据库文件，数据库连接池c3p0

2.配置sqlsessionFactory对象

3.配置mybatis全局配置文件：mybatis-config..xml

4.配置扫描Dao接口的包，动态实现Dao接口注入到Spring容器中



```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xmlns:context="http://www.springframework.org/schema/context"
      xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       https://www.springframework.org/schema/context/spring-context.xsd">

   <!-- 配置整合mybatis -->
   <!-- 1.关联数据库文件 -->
   <context:property-placeholder location="classpath:database.properties"/>

   <!-- 2.数据库连接池 -->
   <!--数据库连接池
       dbcp 半自动化操作 不能自动连接
       c3p0 自动化操作（自动的加载配置文件 并且设置到对象里面）
   -->
   <bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource">
       <!-- 配置连接池属性 -->
       <property name="driverClass" value="${jdbc.driver}"/>
       <property name="jdbcUrl" value="${jdbc.url}"/>
       <property name="user" value="${jdbc.username}"/>
       <property name="password" value="${jdbc.password}"/>

       <!-- c3p0连接池的私有属性 -->
       <property name="maxPoolSize" value="30"/>
       <property name="minPoolSize" value="10"/>
       <!-- 关闭连接后不自动commit -->
       <property name="autoCommitOnClose" value="false"/>
       <!-- 获取连接超时时间 -->
       <property name="checkoutTimeout" value="10000"/>
       <!-- 当获取连接失败重试次数 -->
       <property name="acquireRetryAttempts" value="2"/>
   </bean>

   <!-- 3.配置SqlSessionFactory对象 -->
   <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
       <!-- 注入数据库连接池 -->
       <property name="dataSource" ref="dataSource"/>
       <!-- 配置MyBaties全局配置文件:mybatis-config.xml -->
       <property name="configLocation" value="classpath:mybatis-config.xml"/>
   </bean>

   <!-- 4.配置扫描Dao接口包，动态实现Dao接口注入到spring容器中 -->
   <!--解释 ：https://www.cnblogs.com/jpfss/p/7799806.html-->
   <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
       <!-- 注入sqlSessionFactory -->
       <property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"/>
       <!-- 给出需要扫描Dao接口包 -->
       <property name="basePackage" value="com.kuang.dao"/>
   </bean>

</beans>
```

## spring层整合service层

spring-service.xml

1.扫描service相关的bean

2.service接口注入到IOC容器中

3.配置事务管理器，注入数据库连接池

tip：spring层搞定，可以看到，spring就是一个大杂烩，一个容器！！

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xmlns:context="http://www.springframework.org/schema/context"
      xsi:schemaLocation="http://www.springframework.org/schema/beans
   http://www.springframework.org/schema/beans/spring-beans.xsd
   http://www.springframework.org/schema/context
   http://www.springframework.org/schema/context/spring-context.xsd">

   <!-- 扫描service相关的bean -->
   <context:component-scan base-package="com.kuang.service" />

   <!--BookServiceImpl注入到IOC容器中-->
   <bean id="BookServiceImpl" class="com.kuang.service.BookServiceImpl">
       <property name="bookMapper" ref="bookMapper"/>
   </bean>

   <!-- 配置事务管理器 -->
   <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
       <!-- 注入数据库连接池 -->
       <property name="dataSource" ref="dataSource" />
   </bean>

</beans>
```

## springmvc层

web.xml:

1.调度器dispatcherservlet

2.encodingFilter过滤器

3.seesion过期时间

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
        version="4.0">

   <!--DispatcherServlet-->
   <servlet>
       <servlet-name>DispatcherServlet</servlet-name>
       <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
       <init-param>
           <param-name>contextConfigLocation</param-name>
           <!--一定要注意:我们这里加载的是总的配置文件，之前被这里坑了！-->  
           <param-value>classpath:applicationContext.xml</param-value>
       </init-param>
       <load-on-startup>1</load-on-startup>
   </servlet>
   <servlet-mapping>
       <servlet-name>DispatcherServlet</servlet-name>
       <url-pattern>/</url-pattern>
   </servlet-mapping>

   <!--encodingFilter-->
   <filter>
       <filter-name>encodingFilter</filter-name>
       <filter-class>
          org.springframework.web.filter.CharacterEncodingFilter
       </filter-class>
       <init-param>
           <param-name>encoding</param-name>
           <param-value>utf-8</param-value>
       </init-param>
   </filter>
   <filter-mapping>
       <filter-name>encodingFilter</filter-name>
       <url-pattern>/*</url-pattern>
   </filter-mapping>
   
   <!--Session过期时间-->
   <session-config>
       <session-timeout>15</session-timeout>
   </session-config>
   
</web-app>
```

spring-mvc.xml:

1.配置springmvc，开启注解驱动，静态资源默认servlet配置，配置jsp显示viewResolver视图解析器，扫描web相关的bean

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

   <!-- 配置SpringMVC -->
   <!-- 1.开启SpringMVC注解驱动 -->
   <mvc:annotation-driven />
   <!-- 2.静态资源默认servlet配置-->
   <mvc:default-servlet-handler/>

   <!-- 3.配置jsp 显示ViewResolver视图解析器 -->
   <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
       <property name="viewClass" value="org.springframework.web.servlet.view.JstlView" />
       <property name="prefix" value="/WEB-INF/jsp/" />
       <property name="suffix" value=".jsp" />
   </bean>

   <!-- 4.扫描web相关的bean -->
   <context:component-scan base-package="com.kuang.controller" />

</beans>
```

spring的配置整合文件：applicationContext.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">

   <import resource="spring-dao.xml"/>
   <import resource="spring-service.xml"/>
   <import resource="spring-mvc.xml"/>
   
</beans>
```

配置文件暂时结束！！！

## Controller和视图层编写

1、BookController 类编写 ， 方法一：查询全部书籍

2、编写首页 **index.jsp**

3、书籍列表页面 **allbook.jsp**

4、BookController 类编写 ， 方法二：添加书籍

5、添加书籍页面：**addBook.jsp**

6、BookController 类编写 ， 方法三：修改书籍

7、修改书籍页面  **updateBook.jsp**

8、BookController 类编写 ， 方法四：删除书籍

![image-20210412144933545](https://i.loli.net/2021/05/20/7eV3PmtCBUdawhc.png)

![image-20210412145013859](https://i.loli.net/2021/05/20/5RqDBipvHfc47Gh.png)

## 小结

这是第一个SSM整合案例，必须烂熟于心！

SSM框架重要程度不言而喻，学到此就可以进行基本网站的单独开发了，但是这只是增删改查的基本操作(90%的程序员就是在做CRUD增删改查)，这算是真正步入后台开发的门，也是能找一个后台开发工作的底线！



**springmvc进阶：**

- Ajax和Json

- 文件上传和下载

- 拦截器



## BootStarp

cnd和矢量图标

```jsp
<!-- 新 Bootstrap 核心 CSS 文件 -->
<link href="https://cdn.staticfile.org/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
  
<!-- jQuery文件。务必在bootstrap.min.js 之前引入 -->
<script src="https://cdn.staticfile.org/jquery/2.1.1/jquery.min.js"></script>
  
<!-- 最新的 Bootstrap 核心 JavaScript 文件 -->
<script src="https://cdn.staticfile.org/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
矢量图标
<link 
      rel="stylesheet" 
      href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@5.14.0/css/all.min.css"
>
```



# JSON



前后端分离时代；

后端部署后端，提供接口；



​      json      说白对后端就是一个字符串

 

前端独立部署，负责渲染后端数据；





## 什么是JSON

javaScript object notaion，js对象标记；

是一种轻量级的数据交换格式使用广泛；

完全独立于编程语言的**文本格式**存储和表示数据；



{}保存对象，[]保存数组；

JSON键值对JavaScript对象；



JSON和JavaScript对象的关系：

JSON是JavaScript对象的字符创表示法，它使用文本表示一个JS对象的信息，本质是一个字符串。

```java
var obj = {a: 'Hello', b: 'World'}; //这是一个对象，注意键名也是可以使用引号包裹的
var json = '{"a": "Hello", "b": "World"}'; //这是一个 JSON 字符串，本质是一个字符串
```



JSON和JavaScript对象互转:

JSON字符串->JavaScript对象：JSON.parse();

JavaScript对象->JSON字符串:   JSON.stringify();



## Jackson使用

COntroller返回json数据；

较好的json解析工具：Jackson，阿里巴巴的fastjson；



导包：jackson-databind；

配置springmvc：

web.xml：

```
1.注册servlet
    通过初始化参数指定SpringMVC配置文件的位置，进行关联；
    启动顺序，数字越小，启动越早；
    所有请求都会被springmvc拦截
2.配置过滤器。
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
        version="4.0">

   <!--1.注册servlet-->
   <servlet>
       <servlet-name>SpringMVC</servlet-name>
       <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
       <!--通过初始化参数指定SpringMVC配置文件的位置，进行关联-->
       <init-param>
           <param-name>contextConfigLocation</param-name>
           <param-value>classpath:springmvc-servlet.xml</param-value>
       </init-param>
       <!-- 启动顺序，数字越小，启动越早 -->
       <load-on-startup>1</load-on-startup>
   </servlet>

   <!--所有请求都会被springmvc拦截 -->
   <servlet-mapping>
       <servlet-name>SpringMVC</servlet-name>
       <url-pattern>/</url-pattern>
   </servlet-mapping>

   <filter>
       <filter-name>encoding</filter-name>
       <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
       <init-param>
           <param-name>encoding</param-name>
           <param-value>utf-8</param-value>
       </init-param>
   </filter>
   <filter-mapping>
       <filter-name>encoding</filter-name>
       <url-pattern>/</url-pattern>
   </filter-mapping>

</web-app>
```

springmvc-servlet.xml：

```
1.自动扫描指定的包，下面所有注解类交给IOC容器管理
2. 视图解析器
```

```xml
?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xmlns:context="http://www.springframework.org/schema/context"
      xmlns:mvc="http://www.springframework.org/schema/mvc"
      xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       https://www.springframework.org/schema/context/spring-context.xsd
       http://www.springframework.org/schema/mvc
       https://www.springframework.org/schema/mvc/spring-mvc.xsd">

   <!-- 自动扫描指定的包，下面所有注解类交给IOC容器管理 -->
   <context:component-scan base-package="com.kuang.controller"/>

   <!-- 视图解析器 -->
   <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver"
         id="internalResourceViewResolver">
       <!-- 前缀 -->
       <property name="prefix" value="/WEB-INF/jsp/" />
       <!-- 后缀 -->
       <property name="suffix" value=".jsp" />
   </bean>

</beans>
```



@ResponseBody ;     

ObjectMapper:jackson的对象映射器，用来解析数据；



请求出现乱码：

```
produces = "application/json;charset=utf-8"
```

## 代码优化

### 乱码统一解决

配置springmvc:   StringHttpMessageConverter消息转换配置！

```xml
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
```

### 返回json字符串统一解决

前后端分离开发中一般使用@RestCOntroller为类的所有方法都返回json字符串。

### 测试

1.list集合输出

2.输出时间对象：取消默认timestamps形式，自定义：

```java
 //不使用时间戳的方式
   mapper.configure(SerializationFeature.WRITE_DATES_AS_TIMESTAMPS, false);
   //自定义日期格式对象
   SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
   //指定日期格式
   mapper.setDateFormat(sdf);
```

3.将时间输出格式抽取为工具类

## FastJson使用

实现json对象与JavaBean对象的转换；

实现JavaBean对象与json字符串的转换；

实现json对象与json字符串的转换。

**JSONObject   JSONArray**  **JSON**代表前两者的转化。



# Ajax

## 什么是Ajax

- Ajax=Asynchronous JavaScript and XML      异步的JavaScript和XML

- Ajax是一种无须重新加载整页面的情况下能够更新部分网页的技术
- 它不是一种新的编程语言，而是一种应用于创建更好更快以及交互性更强的web应用程序
- 单词自动搜索，和百度搜索框一样
- 使用ajax技术的网页通过在后台服务器进行少量的数据交换就可以实现异步局部更新
- 创建直接，高可用，更丰富，更动态的web用户界面

## 伪造Ajax

JS原生XML HttpRequest！Ajax的核心是XHR。

XHR为向服务器发送请求和解析服务器响应提供了接口。



通常用jQuery，方便简单，是一个库，js的大量函数(方法)。

jQuery不是生产者而是大自然搬运工，对XHR进行了封装，方便调用。

导入库jQuery或者在线cdn：

```jsp
<script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
<script src="${pageContext.request.contextPath}/statics/js/jquery-3.1.1.min.js"></script>
```





实现点击，获得焦点事件，文本框内容变化也会发起一个事件。



使用前端的一个iframe标签来伪造一个ajax的样子：

```html
<!DOCTYPE html>
<html>
<head lang="en">
   <meta charset="UTF-8">
   <title>kuangshen</title>
</head>
<body>

<script type="text/javascript">
   window.onload = function(){
       var myDate = new Date();
       document.getElementById('currentTime').innerText = myDate.getTime();
  };

   function LoadPage(){
       var targetUrl =  document.getElementById('url').value;
       console.log(targetUrl);
       document.getElementById("iframePosition").src = targetUrl;
  }

</script>

<div>
   <p>请输入要加载的地址：<span id="currentTime"></span></p>
   <p>
       <input id="url" type="text" value="https://www.baidu.com/"/>
       <input type="button" value="提交" onclick="LoadPage()">
   </p>
</div>

<div>
   <h3>加载页面位置：</h3>
   <iframe id="iframePosition" style="width: 100%;height: 500px;"></iframe>
</div>

</body>
</html>
```



**利用Ajax可以做：**

- 注册时输入用户名自动检测用户是否已经存在
- 登录时提示用户名密码错误
- 删除数据行时，将ID发送到后台，后台在数据库中删除，数据库删除成功，在页面dom中数据行也删除。





## Ajax前后端交互原理

![image-20210416193934537](https://i.loli.net/2021/05/20/rFDtIqZiWsf1HNd.png)



HTML+css:略懂+JS(熟练)

JS：

- 闭包 () ()
- Dom
  - tag,id,name
  - create,remove
- Bom
  - windows
  - document.(title,getelemtbyid)



ul:无序列表

li：列表



编写web.xml和spring配置文件：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xmlns:context="http://www.springframework.org/schema/context"
      xmlns:mvc="http://www.springframework.org/schema/mvc"
      xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       https://www.springframework.org/schema/context/spring-context.xsd
       http://www.springframework.org/schema/mvc
       https://www.springframework.org/schema/mvc/spring-mvc.xsd">

   <!-- 自动扫描指定的包，下面所有注解类交给IOC容器管理 -->
   <context:component-scan base-package="com.kuang.controller"/>
   <mvc:default-servlet-handler />
   <mvc:annotation-driven />

   <!-- 视图解析器 -->
   <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver"
         id="internalResourceViewResolver">
       <!-- 前缀 -->
       <property name="prefix" value="/WEB-INF/jsp/" />
       <!-- 后缀 -->
       <property name="suffix" value=".jsp" />
   </bean>

</beans>
```

使用最原始的HttpServletResponse编写AjaxController:

```java
@Controller
public class AjaxController {

   @RequestMapping("/a1")
   public void ajax1(String name , HttpServletResponse response) throws IOException {
       if ("admin".equals(name)){
           response.getWriter().print("true");
      }else{
           response.getWriter().print("false");
      }
  }

}
```

index.jsp:

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
 <head>
   <title>$Title$</title>
  <%--<script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>--%>
   <script src="${pageContext.request.contextPath}/statics/js/jquery-3.1.1.min.js"></script>
   <script>
       function a1(){
           $.post({
               url:"${pageContext.request.contextPath}/a1",
               data:{'name':$("#txtName").val()},
               success:function (data,status) {
                   alert(data);
                   alert(status);
              }
          });
      }
   </script>
 </head>
 <body>

<%--onblur：失去焦点触发事件--%>
用户名:<input type="text" id="txtName" onblur="a1()"/>

 </body>
</html>
```





**SpringMVC实现：**

后端

```java
@RequestMapping("/a2")
public List<User> ajax2(){
   List<User> list = new ArrayList<User>();
   list.add(new User("秦疆1号",3,"男"));
   list.add(new User("秦疆2号",3,"男"));
   list.add(new User("秦疆3号",3,"男"));
   return list; //由于@RestController注解，将list转成json格式返回
}
```

前端

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
   <title>Title</title>
</head>
<body>
<input type="button" id="btn" value="获取数据"/>
<table width="80%" align="center">
   <tr>
       <td>姓名</td>
       <td>年龄</td>
       <td>性别</td>
   </tr>
   <tbody id="content">
   </tbody>
</table>

<script src="${pageContext.request.contextPath}/statics/js/jquery-3.1.1.min.js"></script>
<script>

   $(function () {
       $("#btn").click(function () {
           $.post("${pageContext.request.contextPath}/a2",function (data) {
               console.log(data)
               var html="";
               for (var i = 0; i <data.length ; i++) {
                   html+= "<tr>" +
                       "<td>" + data[i].name + "</td>" +
                       "<td>" + data[i].age + "</td>" +
                       "<td>" + data[i].sex + "</td>" +
                       "</tr>"
              }
               $("#content").html(html);
          });
      })
  })
</script>
</body>
</html>
```





**利用Ajax实现注册检测**

controller

```java
@RequestMapping("/a3")
public String ajax3(String name,String pwd){
   String msg = "";
   //模拟数据库中存在数据
   if (name!=null){
       if ("admin".equals(name)){
           msg = "OK";
      }else {
           msg = "用户名输入错误";
      }
  }
   if (pwd!=null){
       if ("123456".equals(pwd)){
           msg = "OK";
      }else {
           msg = "密码输入有误";
      }
  }
   return msg; //由于@RestController注解，将msg转成json格式返回
}
```

login.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
   <title>ajax</title>
   <script src="${pageContext.request.contextPath}/statics/js/jquery-3.1.1.min.js"></script>
   <script>

       function a1(){
           $.post({
               url:"${pageContext.request.contextPath}/a3",
               data:{'name':$("#name").val()},
               success:function (data) {
                   if (data.toString()=='OK'){
                       $("#userInfo").css("color","green");
                  }else {
                       $("#userInfo").css("color","red");
                  }
                   $("#userInfo").html(data);
              }
          });
      }
       function a2(){
           $.post({
               url:"${pageContext.request.contextPath}/a3",
               data:{'pwd':$("#pwd").val()},
               success:function (data) {
                   if (data.toString()=='OK'){
                       $("#pwdInfo").css("color","green");
                  }else {
                       $("#pwdInfo").css("color","red");
                  }
                   $("#pwdInfo").html(data);
              }
          });
      }

   </script>
</head>
<body>
<p>
  用户名:<input type="text" id="name" onblur="a1()"/>
   <span id="userInfo"></span>
</p>
<p>
  密码:<input type="text" id="pwd" onblur="a2()"/>
   <s
      pan id="pwdInfo"></span>
</p>
</body>
</html>
```

注意json输出乱码问题：





# 拦截器

拦截器和过滤器的区别拦截器是AOP思想的具体应用。

拦截器只会拦截访问的控制器方法，对jsp/html/css/image/js不处理所以效率会高一些。

## 自定义拦截器

必须先实现HandlerInterceptor接口:

```java
public class MyInterceptor implements HandlerInterceptor {

   //在请求处理的方法之前执行
   //如果返回true执行下一个拦截器
   //如果返回false就不执行下一个拦截器
   public boolean preHandle(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object o) throws Exception {
       System.out.println("------------处理前------------");
       return true;
  }

   //在请求处理方法执行之后执行
   public void postHandle(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object o, ModelAndView modelAndView) throws Exception {
       System.out.println("------------处理后------------");
  }

   //在dispatcherServlet处理后执行,做清理工作.
   public void afterCompletion(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object o, Exception e) throws Exception {
       System.out.println("------------清理------------");
  }
}
```

springmvc配置文件中配置拦截器：

```xml
<!--关于拦截器的配置-->
<mvc:interceptors>
   <mvc:interceptor>
       <!--/** 包括路径及其子路径-->
       <!--/admin/* 拦截的是/admin/add等等这种 , /admin/add/user不会被拦截-->
       <!--/admin/** 拦截的是/admin/下的所有-->
       <mvc:mapping path="/**"/>
       <!--bean配置的就是拦截器-->
       <bean class="com.kuang.interceptor.MyInterceptor"/>
   </mvc:interceptor>
</mvc:interceptors>
```

编写controller接收请求：

编写index.jsp:

```jsp
<a href="${pageContext.request.contextPath}/interceptor">拦截器测试</a>
```



## 验证用户是否登录

```java
@SuppressWarnings("ALL")
public class loginInterceptor implements HandlerInterceptor{
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
         //判断什么情况情况下没有登录，放行登录什么时候
        HttpSession session = request.getSession();
//        本来就在登录页面也放行
        if(request.getRequestURI().contains("goLogin")){
            return true;
        }
//        第一次登录
        if(request.getRequestURI().contains("login")){
            return true;
        }
//       第一次登录也是没有session的
        if(session.getAttribute("userLoginInfo")!=null){
            return  true;
        }
//        其他情况下转发
        request.getRequestDispatcher("/WEB-INF/jsp/login.jsp").forward(request,response);
        return false;
    }
}

```





# 文件上传和下载

## 文件上传

两种方式

文件流

```java
//    @RequestParam("file")将name=file控件得到的文件封装成CommonsMultipartFile对象
//    批量上传CommonsMultipartFile则为数组即可
    @RequestMapping("/upload")
    public String fileUpload(@RequestParam("file")CommonsMultipartFile file, HttpServletRequest request) throws IOException {
        //获取文件名
        String originalFilename = file.getOriginalFilename();
//        文件名为空返回首页
        assert originalFilename != null;
        if(originalFilename.equals("")){
            return "redirect:/index.jsp";
        }
        System.out.println("上传文件名=>"+originalFilename);
//        上传文件路径保存设置
        String realPath = request.getServletContext().getRealPath("/upload");
//        如果路径不存在则创建一个
        File file1 = new File(realPath);
        if(!file1.exists()){
            file1.mkdir();
        }
        System.out.println("上传文件保存地址=>"+file1);
//       文件输入流
        InputStream inputStream = file.getInputStream();
//       文件输出流
        FileOutputStream fileOutputStream = new FileOutputStream(new File(file1, originalFilename));
//       读取写出
        int len=0;
        byte[] bytes = new byte[1024];
        while ((len=inputStream.read(bytes))!=-1){
            fileOutputStream.write(bytes,0,len);
            fileOutputStream.flush();
        }

        inputStream.close();
        fileOutputStream.close();

        return "redirect:/index.jsp";
    }
```

transto方法

```java
    /*
     * 采用file.Transto 来保存上传的文件
     */
    @RequestMapping("/upload2")
    public String  fileUpload2(@RequestParam("file") CommonsMultipartFile file, HttpServletRequest request) throws IOException {

        //上传路径保存设置
        String path = request.getServletContext().getRealPath("/upload");
        File realPath = new File(path);
        if (!realPath.exists()){
            realPath.mkdir();
        }
        //上传文件地址
        System.out.println("上传文件保存地址："+realPath);

        //通过CommonsMultipartFile的方法直接写文件（注意这个时候）
        file.transferTo(new File(realPath +"/"+ file.getOriginalFilename()));

        return "redirect:/index.jsp";
    }
```



## 文件下载

步骤：

- 设置response响应头
- 读取文件
- 写出文件
- 执行操作
- 关闭流（先开后关）

```java
@RequestMapping(value="/download")
public String downloads(HttpServletResponse response ,HttpServletRequest request) throws Exception{
   //要下载的图片地址
   String  path = request.getServletContext().getRealPath("/upload");
   String  fileName = "基础语法.jpg";

   //1、设置response 响应头
   response.reset(); //设置页面不缓存,清空buffer
   response.setCharacterEncoding("UTF-8"); //字符编码
   response.setContentType("multipart/form-data"); //二进制传输数据
   //设置响应头
   response.setHeader("Content-Disposition",
           "attachment;fileName="+URLEncoder.encode(fileName, "UTF-8"));

   File file = new File(path,fileName);
   //2、 读取文件--输入流
   InputStream input=new FileInputStream(file);
   //3、 写出文件--输出流
   OutputStream out = response.getOutputStream();

   byte[] buff =new byte[1024];
   int index=0;
   //4、执行 写出操作
   while((index= input.read(buff))!= -1){
       out.write(buff, 0, index);
       out.flush();
  }
   out.close();
   input.close();
   return null;
}
```





# 回顾SSM

## mybatis

- 认识mybatis：持久化
- **第一个mybatis程序**
- CRUD
- 配置
- **ResultMap结果集映射**：一对多，多对一
- Log4j
- 分页
- 注解开发
- 动态SQL
- 缓存

## spring

- IOC理论推导
- spring概述
- IOC-Beans.xml
- **DI-Ser/c p**
- **代理模式(静态，动态)**
- AOP
- 注解开发spring
- **JavaConfig**
- **整合Mybatis**（事务）
- 声明式事务





## springmvc

- **spring执行流程**
- 回顾mvc
- helloSpringMVC
- 执行原理
- 结果跳转方式
- 数据如何处理
- 乱码问题
- Controller
- **RestFul**
- **整合SSM项目**
- JSON
- Ajax
- 拦截器
- 文件上传和下载





前端四要素：

- 逻辑

  - 判断
  - 循环

- 事件

  - 浏览器事件：window document

  - Dom事件：增，删，改节点元素内容

    对应框架：

    jQury  Vue React

- 视图

  - html

  - css    （难点）

    对应框架：

      BootStrap   layui

- 通信
  - xhr
  - ajax（jQuery封装）
  - axios（Vue）

前端化工程：SSM+BootStrap+Vue



Java全栈工程师：

- 后台开发：主打
- 前端：html、css、js、jQuery、ps
- 运维：项目发布、服务器如何运行一个项目？（springboot简单） Linux









