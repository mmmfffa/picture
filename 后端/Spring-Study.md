[[我的工作台 - Gitee.com](https://gitee.com/ma-fu/dashboard/projects)]:

# 常用依赖 #

## pom.xml


```xml
    <dependencies>
        <!-- https://mvnrepository.com/artifact/org.springframework/spring-webmvc -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.3.3</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/junit/junit -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.1</version>
            <scope>test</scope>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.aspectj/aspectjweaver -->
        <dependency>
           <groupId>org.aspectj</groupId>
           <artifactId>aspectjweaver</artifactId>
           <version>1.9.4</version>
        </dependency>

    </dependencies>
```



## beans.xml注解支持 ##

```text
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="
       http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        https://www.springframework.org/schema/context/spring-context.xsd
        http://www.springframework.org/schema/aop
        https://www.springframework.org/schema/aop/spring-aop.xsd
       ">
<!--开启注解的支持-->
       <context:annotation-config/>

</beans>
```

## spring-dao.xml ##

```xml

dataSource和sqlSession的Spring方式注入


        <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
                <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=false&amp;useUnicode=true&amp;
                                            characterEncoding=UTF-    8&amp;allowPublicKeyRetrieval=true"/>
                <property name="username" value="root"/>
                <property name="password" value="8613919"/>
        </bean>
        <!--    sqlSessionFactory-->
        <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
                <property name="dataSource" ref="dataSource" />
<!--            绑定mybatis配置文件-->
                <property name="configLocation" value="classpath:mybatis-config.xml"/>
                <property name="mapperLocations" value="classpath*:com/mf/dao/**/*.xml"/>
        </bean>
<!--        SqlSessionTemplate就是我们使用的sqlSession-->
        <bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
<!--             只能使用构造器注入sqlSessionFactory,因为他没有set方法-->
                <constructor-arg index="0" ref="sqlSessionFactory"/>
        </bean>

```



# 目录 #



## Spring ##

### 简介 ###

spring理念：使现有技术更加实用，本身就是一个大杂烩，整合现有的框架技术。

一句话概括：spring是一个轻量级的控制反转Ioc和面向切面AOP的容器(框架)。

### 优点 ###

- 轻量级，非入侵；
- 控制反转，面向切面；
- 支持事务处理，对象框架整合。

### 拓展 ###

## IOC理论推导 ##

spring7层分层架构：

**核心容器：**通过beanfactory使用控制反转定义创建、配置、管理bean的方式。

spring上下文：配置文件，提供一些企业服务。

**springAOP：**将声明性事务切入应用程序。

**springDAO：**面向 JDBC 的异常，降低了需要编写的异常代码数量（例如打开和关闭连接）。

Spring ORM：若干个 ORM 框架。

Spring Web 模块：为基于 Web 的应用程序提供了上下文

**Spring MVC 框架**：MVC 框架是一个全功能的构建 Web 应用程序的 MVC 实现。



1.ApplicationContext.xml读取配置文件

2.POJO根据元数据创建和组装Bean

3.程序使用时再从Ioc容器中取出需要的对象

**Ioc实现方式有两种：xml配置和注解**

采用xml配置，bean的定义信息和实现分离；

注解把二者合二为一，定义信息直接以注解形式在实现类中，从而达到零配置。



### IOC的本质 ###

**控制反转的本质是一种设计思想，DI(依赖注入)是实现IOC的一种方式。**

- UserDao接口
- UserDaoImpl实现类
- UserService业务接口
- UserServiceImpl业务实现

## HelloSpring ##

1.创建实体，创建接口和实现类

2.注册beans.xml,交由spring创建和管理

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">

   <!--bean就是java对象 , 由Spring创建和管理-->
   <bean id="hello" class="com.kuang.pojo.Hello">
       <property name="name" value="Spring"/>
   </bean>
    
   <bean id="MysqlImpl" class="com.kuang.dao.impl.UserDaoMySqlImpl"/>
   <bean id="OracleImpl" class="com.kuang.dao.impl.UserDaoOracleImpl"/>

   <bean id="ServiceImpl" class="com.kuang.service.impl.UserServiceImpl">
       <!--注意: 这里的name并不是属性 , 而是set方法后面的那部分 , 首字母小写-->
       <!--引用另外一个bean , 不是用value 而是用 ref-->
       <property name="userDao" ref="OracleImpl"/>
   </bean>

</beans>
```

3.要用直接ApplicationContext 从beans.xml拿到(再也不用**new** 对象了)





## IOC创建对象的方式 ##

1.通过无参构造方法来创建。

2.通过有参构造方法(还是用Set方法)来创建。



beans.xml参数设置3种方式：

1.根据index参数下标。

2.根据参数名字。**推荐使用**

3.根据参数类型。不建议使用

```xml
<constructor-arg index="0" value="kuangshen2"/>

<property name="name" value="马富说"/>

<constructor-arg type="java.lang.String" value="kuangshen2"/>
```

配置文件加载的时候，其中管理的对象已经创建和初始化了。



传统对象由程序本身控制创建。

spring由IOC容器创建对象并设置属性，程序本身不创建对象而是被动接受对象，利用set方法进行注入，这个过程就叫做控制反转。

## Spring配置 ##

### 别名alias ###

### Bean配置 ###

id是bean的标识符，要唯一；

没有配置id，name就是默认标识符；

有id又有name,name就是别名；

两个都没有，applicationContext.getBean(.class)获取对象。

```xml
<bean id="hello" name="hello2 h2,h3;h4" class="com.kuang.pojo.Hello">
   <property name="name" value="Spring"/>
</bean>
```

### import ###

## 依赖注入 ##

依赖IOC容器创建对象，注入对象属性值。

### 构造器注入 ###

### Set方式注入【重点】 ###

### 拓展方式注入 ###

1.常量注入

2.bean注入 **ref**

3.数组注入 **array**

4.list注入 **list**

5.Map注入 **map  entry**

6.set注入 **set**

7.null注入  **<null/>**

8.properties注入 **props  prop**



p标签注入(set方式注入)

c标签注入(有参构造方式注入)

### bean的作用域 ###

单例   singleton

原生型   score=prototype 

request创建自己的bean

session共享bean

## Bean自动装配 ##

spring装配bean方式有三种：

1.java中显示配置

2.xml中显示配置

3.隐式bean发现机制和**自动装配**(组件扫描component scanning，自动装配autowiring)



什么叫自动装配：spring自动发现应用上下文所创建的bean，spring自动满足bean之间的依赖。

自动装配有3种方式：

byname

bytype

**注解**(推荐使用)

### xml以前的bean装配方式 ###

### ByName自动装配，ByType自动装配 ###

```xml
   <!--原来的方式-->
   <bean id="dog" class="com.kuang.pojo.Dog"/>
   <bean id="cat" class="com.kuang.pojo.Cat"/>

   <bean id="user" class="com.kuang.pojo.User">
       <property name="cat" ref="cat"/>
       <property name="dog" ref="dog"/>
       <property name="str" value="qinjiang"/>
   </bean>

   <!--byname自动装配-->
    <bean id="user" class="com.kuang.pojo.User" autowire="byName">
       <property name="str" value="qinjiang"/>
    </bean>

    <!--bytype自动装配,类型要唯一-->
    <bean id="dog" class="com.kuang.pojo.Dog"/>
    <bean id="cat" class="com.kuang.pojo.Cat"/>
    <!--类型不唯一报错-->
    <bean id="cat2" class="com.kuang.pojo.Cat"/>

    <bean id="user" class="com.kuang.pojo.User" autowire="byType">
       <property name="str" value="qinjiang"/>
    </bean>
```

### 使用注解实现自动装配(推荐使用) ###

导使用注解就需要导入spring-aop的包

开启注解支持

```xml
<context:annotation-config/>
```

@Autowired是按类型自动装配的，**不支持id匹配**

```java
//如果允许对象为null，设置required = false,默认为true
@Autowired(required = false)
private Cat cat;
@Autowired
private Dog dog;
private String str;
```

```xml
<context:annotation-config/>

<bean id="dog" class="com.kuang.pojo.Dog"/>
<bean id="cat" class="com.kuang.pojo.Cat"/>
<bean id="user" class="com.kuang.pojo.User"/>
```

@Autowired加上 **@Qualifier**可以根据byname自动装配，就可以支持id匹配了

```java
@Autowired
@Qualifier(value = "cat2")
private Cat cat;
@Autowired
@Qualifier(value = "dog2")
private Dog dog;
```

@Resource 

 如有指定的name属性，先按该属性进行byName方式查找装配;

其次再进行默认的byName方式进行装配；

其次再按byType的方式自动装配。

```java
@Resource
private Cat cat;
@Resource
private Dog og;
```

## 基于注解开发spring

导入注解支持包aop  和  context约束

扫描包 和 添加注解驱动

```xml
<context:component-scan base-package="com.kuang.pojo"/>
<context:annotation-config/>  
```

包下的类增加注解@Component，属性注入  @Value(如果提供了set方法，在set方法上添加@value("值")

```java
@Component("user")
// 相当于配置文件中 <bean id="user" class="当前注解的类"/>
public class User {
   @Value("秦疆")
   // 相当于配置文件中 <property name="name" value="秦疆"/>
   public String name;
}
```



不同层的衍生注解：本质都是@component

- @controller :web层
- @service：service层
- @repository:dao层



bean的自动装配上节已讲。



小结：

xml与注解比较：

- xml适用任何场景，结构清晰，维护方便

- 注解不是自己提供的类适用不了，开发方便

  

**推荐使用xml和注解整合开发：**xml管理bean，注解完成属性注入



## 基于Java类开发spring ##

编写实体类

创建config配置包，编写配置类

```java
@Configuration  //代表这是一个配置类
public class MyConfig {

   @Bean //通过方法注册一个bean，这里的返回值就Bean的类型，方法名就是bean的id！
   public Dog dog(){
       return new Dog();
  }

}
```

```java
@Test
public void test2(){
   ApplicationContext applicationContext =
           new AnnotationConfigApplicationContext(MyConfig.class);
   Dog dog = (Dog) applicationContext.getBean("dog");
   System.out.println(dog.name);
}
```


@Import(MyConfig2.class)  //导入合并其他配置类，类似于配置文件中的 inculde 标签


## 代理模式 ##

**静态代理**

1.抽象角色

2.具体角色

3.代理角色

4客户

缺点：增加具体角色要增加代理类，工作量变大，改动功能需要改动代码量大，违反开闭原则。

**动态代理**

动态代理分两类：基于接口(JDK动态代理)和基于类(cglib) 。

现在比较多使用javasist生成动态代理。

### 基于JDK动态代理

#### 两个核心类

**InvocationHandler**：调用处理程序

**Proxy**  :实现了接口InvocationHandler

`Proxy`提供了创建动态代理类和实例的静态方法，它也是由这些方法创建的所有动态代理类的超类。

两个重要方法：

**getProxy()**   :   newProxyInstance(loader,interfaces,h);

loader-类加载器来定义代理类

interfaces-代理类实现接口列表

h-调度方法调用的调用处理函数

**invoke()  :**   处理代理实例上的方法调用并返回结果

```java
//生成代理类
public Object getProxy(){
   return Proxy.newProxyInstance(this.getClass().getClassLoader(),
                                 rent.getClass().getInterfaces(),this);
}
```

```java
public class ProxyInvocationHandler implements InvocationHandler {
   private Rent rent;

   public void setRent(Rent rent) {
       this.rent = rent;
  }

   //生成代理类，重点是第二个参数，获取要代理的抽象角色！之前都是一个角色，现在可以代理一类角色
   public Object getProxy(){
       return Proxy.newProxyInstance(this.getClass().getClassLoader(),
               rent.getClass().getInterfaces(),this);
  }

   // proxy : 代理类 
   //method : 代理类的调用处理程序的方法对象.
   // 处理代理实例上的方法调用并返回结果
   @Override
   public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
       seeHouse();
       //核心：本质利用反射实现！
       Object result = method.invoke(rent, args);
       fare();
       return result;
  }

   //看房
   public void seeHouse(){
       System.out.println("带房客看房");
  }
   //收中介费
   public void fare(){
       System.out.println("收中介费");
  }

}
```

```java
       //代理实例的调用处理程序
       ProxyInvocationHandler pih = new ProxyInvocationHandler();
       pih.setRent(host); //将真实角色放置进去！
       Rent proxy = (Rent)pih.getProxy(); //动态生成对应的代理类！
```

动态代理代理某一类业务 

**一个动态代理可以代理多个类，代理的是接口！**



#### 动态代理固定模板

```java
public class ProxyInvocationHandler implements InvocationHandler {
   private Object target;

   public void setTarget(Object target) {
       this.target = target;
  }

   //生成代理类
   public Object getProxy(){
       return Proxy.newProxyInstance(this.getClass().getClassLoader(),
               target.getClass().getInterfaces(),this);
  }

   // proxy : 代理类
   // method : 代理类的调用处理程序的方法对象.
   public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
       log(method.getName());
       Object result = method.invoke(target, args);
       return result;
  }

   public void log(String methodName){
       System.out.println("执行了"+methodName+"方法");
  }

}
```

```java
        //真实角色
        UserServiceImpl userService = new UserServiceImpl();
        //代理角色，不存在
        ProxyInvocationHandler pih = new ProxyInvocationHandler();
        //设置要代理的对象
        pih.setTarget(userService);
        UserService proxy =(UserService) pih.getProxy();
        proxy.add();
        proxy.delete();
```



## AOP ##

**纵向开发：**

dao

|

service

|

servlet

|

前端

**横向开发：**

log->userservice

面向切面编程:  不改变原来的代码的情况下，实现了对原有功能的增强。

springaop：提供声明式事务，允许用户自定义切面。



通知（Advice）：切面必须要完成的工作。即，它是类中的一个方法。

切入点（PointCut）：切面通知 执行的 “地点”的定义。

#### 五种类型的Advice

1.前置通知

2.后置通知

3.环绕通知

4.异常抛出通知

5.引介通知

#### AOP三种实现方式

导入aop织入包

##### SpringAPI实现

编写业务接口

编写业务实现类

编写增强类(5种通知类型)      implements MethodBeforeAdvice     implements AfterReturningAdvice

```java
public class Log implements MethodBeforeAdvice {

   //method : 要执行的目标对象的方法
   //objects : 被调用的方法的参数
   //Object : 目标对象
   @Override
   public void before(Method method, Object[] objects, Object o) throws Throwable {
       System.out.println( o.getClass().getName() + "的" + method.getName() + "方法被执行了");
  }
}
```

```java
public class AfterLog implements AfterReturningAdvice {
   //returnValue 返回值
   //method被调用的方法
   //args 被调用的方法的对象的参数
   //target 被调用的目标对象
   @Override
   public void afterReturning(Object returnValue, Method method, Object[] args, Object target) throws Throwable {
       System.out.println("执行了" + target.getClass().getName()
       +"的"+method.getName()+"方法,"
       +"返回值："+returnValue);
  }
}
```

注册到spring中

```xml
<!--注册bean-->
   <bean id="userService" class="com.kuang.service.UserServiceImpl"/>
   <bean id="log" class="com.kuang.log.Log"/>
   <bean id="afterLog" class="com.kuang.log.AfterLog"/>

   <!--aop的配置-->
   <aop:config>
       <!--切入点 expression:表达式匹配要执行的方法-->
       <aop:pointcut id="pointcut" expression="execution(* com.kuang.service.UserServiceImpl.*(..))"/>
       <!--执行环绕; advice-ref执行方法 . pointcut-ref切入点-->
       <aop:advisor advice-ref="log" pointcut-ref="pointcut"/>
       <aop:advisor advice-ref="afterLog" pointcut-ref="pointcut"/>
   </aop:config>
```

公共业务(实现了复用)和领域业务结合；

领域业务更纯粹 , 程序猿专注领域业务 , 其本质还是动态代理。



##### 自定义类实现

自定义切入类

```java
public class DiyPointcut {

   public void before(){
       System.out.println("---------方法执行前---------");
  }
   public void after(){
       System.out.println("---------方法执行后---------");
  }
   
}
```

注册到spring中

```xml
<bean id="diy" class="com.kuang.config.DiyPointcut"/>

<!--aop的配置-->
<aop:config>
   <!--第二种方式：使用AOP的标签实现-->
   <aop:aspect ref="diy">
       <aop:pointcut id="diyPonitcut" expression="execution(* com.kuang.service.UserServiceImpl.*(..))"/>
       <aop:before pointcut-ref="diyPonitcut" method="before"/>
       <aop:after pointcut-ref="diyPonitcut" method="after"/>
   </aop:aspect>
</aop:config>
```



##### 使用注解实现(推荐使用)

编写注解实现的增强类

```java
@Aspect
public class AnnotationPointcut {
   @Before("execution(* com.kuang.service.UserServiceImpl.*(..))")
   public void before(){
       System.out.println("---------方法执行前---------");
  }

   @After("execution(* com.kuang.service.UserServiceImpl.*(..))")
   public void after(){
       System.out.println("---------方法执行后---------");
  }

   @Around("execution(* com.kuang.service.UserServiceImpl.*(..))")
   public void around(ProceedingJoinPoint jp) throws Throwable {
       System.out.println("环绕前");
       System.out.println("签名:"+jp.getSignature());
       //执行目标方法proceed
       Object proceed = jp.proceed();
       System.out.println("环绕后");
       System.out.println(proceed);
  }
}
```

注册到spring中

```xml
<!--第三种方式:注解实现-->
<bean id="annotationPointcut" class="com.kuang.config.AnnotationPointcut"/>
<aop:aspectj-autoproxy/>
```

**<aop:aspectj-autoproxy />**

声明自动为spring容器中那些配置@aspectJ切面的bean创建代理，织入切面。

当然，spring 在内部依旧采用AnnotationAwareAspectJAutoProxyCreator进行自动代理的创建工作，但具体实现的细节已经被<aop:aspectj-autoproxy />隐藏起来了

<aop:aspectj-autoproxy />有一个proxy-target-class属性，默认为false，表示使用jdk动态代理织入增强，当配为<aop:aspectj-autoproxy  poxy-target-class="true"/>时，表示使用CGLib动态代理技术织入增强。不过即使proxy-target-class设置为false，如果目标类没有声明接口，则spring将自动使用CGLib动态代理。

## 整合Mybatis ##

1.导入相关依赖：

```xml

   <dependencies>
        <!--mybatis相关-->
        <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis -->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.5.6</version>
        </dependency>
       
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.49</version>
        </dependency>
       
        <!--spring相关-->
        <!-- https://mvnrepository.com/artifact/org.springframework/spring-webmvc -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.3.3</version>
        </dependency>
        
        <!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
        <!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>5.2.0.RELEASE</version>
        </dependency>
       
        <!--        aspectJaop织入器-->
        <dependency>
            <groupId>org.aspectj</groupId>
            <artifactId>aspectjweaver</artifactId>
            <version>1.9.6</version>
        </dependency>
       
        <!--        mybatis-spring整合包【重点】-->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-spring</artifactId>
            <version>2.0.6</version>
        </dependency>
       
        <!-- https://mvnrepository.com/artifact/org.projectlombok/lombok -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.12</version>
            <scope>provided</scope>
        </dependency>
       
        <!-- https://mvnrepository.com/artifact/junit/junit -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.1</version>
            <scope>test</scope>
        </dependency>
       
       <!--    配置maven静态资源过滤问题-->
        <build>
            <resources>
                <resource>
                    <directory>src/main/java</directory>
                    <includes>
                        <include>**/*.properties</include>
                        <include>**/*.xml</include>
                    </includes>
                    <filtering>true</filtering>
                </resource>
            </resources>
        </build>

    </dependencies>
```

2.编写配置文件

编写pojo实体类

applicationContext.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/aop
        https://www.springframework.org/schema/aop/spring-aop.xsd">
       <import resource="spring-dao.xml"/>

       <bean id="userMapper" class="com.mf.dao.UserMapperImpl">
              <property name="sqlSessionTemplate" ref="sqlSession"/>
       </bean>

       <bean id="userMapper2" class="com.mf.dao.UserMapperImpl2">
              <property name="sqlSessionFactory" ref="sqlSessionFactory"/>
       </bean>

</beans>
```

mybatis.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
<!-- 给mybatis留点面子，设置和别名留给它来做-->
    <typeAliases>
        <package name="com.mf.pojo"/>
    </typeAliases>
</configuration>
```

spring-dao.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/aop
        https://www.springframework.org/schema/aop/spring-aop.xsd">

<!--    DataSource:使用Spring的数据源替换mybatis的配置 c3p0 dbcp druid
        我们这里使用Spring提供的JDBC
-->
        <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
                <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=false&amp;useUnicode=true&amp;
                                            characterEncoding=UTF-8&amp;allowPublicKeyRetrieval=true"/>
                <property name="username" value="root"/>
                <property name="password" value="8613919"/>
        </bean>
        <!--    sqlSessionFactory-->
        <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
                <property name="dataSource" ref="dataSource" />
<!--            绑定mybatis配置文件-->
                <property name="configLocation" value="classpath:mybatis-config.xml"/>
                <property name="mapperLocations" value="classpath*:com/mf/dao/**/*.xml"/>
        </bean>
<!--        SqlSessionTemplate就是我们使用的sqlSession-->
        <bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
<!--             只能使用构造器注入sqlSessionFactory,因为他没有set方法-->
                <constructor-arg index="0" ref="sqlSessionFactory"/>
        </bean>

</beans>
```

编写dao接口类

编写mapper映射文件

编写service

```java
public class UserDaoImpl implements UserDao {

 private SqlSession sqlSession;

 public void setSqlSession(SqlSession sqlSession) {
   this.sqlSession = sqlSession;
}

 public User getUser(String userId) {
   return sqlSession.getMapper...;
}
}
```

注入sqlsessiontemplate

```xml
<bean id="userDao" class="org.mybatis.spring.sample.dao.UserDaoImpl">
 <property name="sqlSession" ref="sqlSession" />
</bean>
```

3.代码实现



整合方式一：

1.引入spring配置文件beans.xml

2.配置数据源替换mybytatis数据源

```xml
<!--配置数据源：数据源有非常多，可以使用第三方的，也可使使用Spring的-->
<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
   <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
   <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=true&amp;useUnicode=true&amp;characterEncoding=utf8"/>
   <property name="username" value="root"/>
   <property name="password" value="123456"/>
</bean>
```

3.配置SqlSessionFactory关联MyBatis

```xml
<!--配置SqlSessionFactory-->
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
   <property name="dataSource" ref="dataSource"/>
   <!--关联Mybatis-->
   <property name="configLocation" value="classpath:mybatis-config.xml"/>
   <property name="mapperLocations" value="classpath:com/kuang/dao/*.xml"/>
</bean>
```

4.注册sqlsessionTemplate，关联sqlsessionFactory

```xml
<!--注册sqlSessionTemplate , 关联sqlSessionFactory-->
<bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
   <!--利用构造器注入-->
   <constructor-arg index="0" ref="sqlSessionFactory"/>
</bean>
```

5.增加dao接口的实现类，私有化sqlsessionTemplate

```java
public class UserDaoImpl implements UserMapper {

   //sqlSession不用我们自己创建了，Spring来管理
   private SqlSessionTemplate sqlSession;

   public void setSqlSession(SqlSessionTemplate sqlSession) {
       this.sqlSession = sqlSession;
  }

   public List<User> selectUser() {
       UserMapper mapper = sqlSession.getMapper(UserMapper.class);
       return mapper.selectUser();
  }
   
}
```

6.注册bean的实现。

```xml
<bean id="userDao" class="com.kuang.dao.UserDaoImpl">
   <property name="sqlSession" ref="sqlSession"/>
</bean>
```



整合方式二：

dao继承Support类 , 直接利用 getSqlSession() 获得 , 然后直接注入SqlSessionFactory 。

比起方式1 , 不需要管理SqlSessionTemplate , 而且对事务的支持更加友好 。

```java
public class UserDaoImpl extends SqlSessionDaoSupport implements UserMapper {
   public List<User> selectUser() {
       UserMapper mapper = getSqlSession().getMapper(UserMapper.class);
       return mapper.selectUser();
  }
}
```

```xml
<bean id="userDao" class="com.kuang.dao.UserDaoImpl">
   <property name="sqlSessionFactory" ref="sqlSessionFactory" />
</bean>
```

整合到spring以后可以完全不要mybatis的配置文件



## 声明式事务 ##

### ACID

1.原子性

2.一致性

3.隔离性

4.持久性

### 事务管理

编程式事务管理：直接嵌套业务方法

声明式事务管理：aop前面编程，比前者要好。



spring事务管理

**导入约束:tx**

配置声明性事务

配置事务通知

配置AOP

```xml
<!--   配置声明式事务-->
       <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
              <property name="dataSource" ref="dataSource"/>
       </bean>
<!--       结合AOP实现事务的织入-->
<!--       配置事务通知：-->
       <tx:advice id="txAdvice" transaction-manager="transactionManager">
<!--              给那些方法配置事务-->
<!--              配置事务传播的特性  propagation传播-->
              <tx:attributes>
                     <tx:method name="add" propagation="REQUIRED"/>
                     <tx:method name="delete" propagation="REQUIRED"/>
                     <tx:method name="update" propagation="REQUIRED"/>
                     <tx:method name="select" read-only="true"/>
                     <tx:method name="*" propagation="REQUIRED"/>
              </tx:attributes>
       </tx:advice>
<!--       配置事务的切入-->
       <aop:config>
              <aop:pointcut id="txPointCut" expression="execution(* com.mf.dao.*.*(..))"/>
              <aop:advisor advice-ref="txAdvice" pointcut-ref="txPointCut"/>
       </aop:config>
```