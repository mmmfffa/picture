# 开篇

SpringBoot官方doc：

```tex
https://docs.spring.io/spring-boot/docs/
```



```html
<html lang="en" xmlns:th="http://www.thymeleaf.org">
```







## 前情回顾

- JavaSe:OOP
- MySql:持久化
- Html5+CSS3+JavaScript+jQuey+框架：视图层
- JavaWeb:原始独立开发MVC三层架构网站
- SSM框架：简化开发流程，但是配置也开始较为复杂
  - 项目打war包：Tomcat中运行
- Spring在简化：SpringBoot--->进入微服务架构时代！
  - 项目打jar包，内嵌Tomcat
- 服务越来越多：SpringCloud



微服务阶段：**SpringBoot**

---

> 学习路线

<img src="https://i.loli.net/2021/05/28/xg3E9ebcSjsIu5z.png" alt="思维导图1" style="zoom:67%;float:left" />



## SpringBoot介绍

**Spring**是一个开源框架，或者通俗的讲就是一个**容器**。

> Spring是如何简化Java开发的

Spring采用4中关键策略：

1. 基于POJO的轻量级和最小侵入性编程；
2. 通过IOC，依赖注入DI和面向接口实现松耦合；
3. 基于切面AOP和惯例进行声明式编程；
4. 通过切面和模板减少代码样式。



> 什么是SpringBoot？

SpringBoot基于Spring4.0设计，Spring应用的整个搭建和开发过程。另外SpringBoot通过集成大量的框架使得依赖包的版本冲突，以及引用的不稳定性等问题得到了很好的解决。 

SpringBoot所具备的特征有：

1. 可以创建独立的Spring应用程序，并且基于其Maven或Gradle插件，可以创建可执行的JARs和WARs；
2. 内嵌Tomcat或Jetty等Servlet容器；
3. 提供自动配置的“starter”项目对象模型（POMS）以简化maven置；
4. 绝对没有代码生成，不需要XML配置。 



SpringBoot框架中还有两个非常重要的策略：**开箱即用和约定优于配置**。

> 什么是开箱即用？

是指在开发过程中，通过在MAVEN项目的pom文件中添加相关依赖包，然后使用对应注解来代替繁琐的XML配置文件以管理对象的生命周期。这个特点使得开发人员摆脱了复杂的配置工作以及依赖的管理工作，更加专注于业务逻辑。



> 什么是约定大于配置？

是一种由SpringBoot本身来配置目标结构，由开发者在结构中添加信息的软件设计范式。这一特点虽降低了部分灵活性，增加了BUG定位的复杂性，但减少了开发人员需要做出决定的数量，同时减少了大量的XML配置，并且可以将代码编译、测试和打包等工作自动化。



>前端常使用模板引擎

主要有FreeMarker和Thymeleaf



<img src="https://i.loli.net/2021/05/28/9ApFJmk7OZhtgXi.png" alt="image-20210526190546082" style="zoom:67%;float:left" />



程序=数据结构+算法---程序员

？？？

程序=面向对象+框架---码农



## 微服务介绍

MVC三层架构   MVVM前端架构  微服务架构；

业务：service:UserService:===>模块；

Springmvc，controller===>提供接口；

微服务是一种架构风格，它要求我们在开发一个应用的时候，这个应用2必须构建成一系列小服务的组合；通过http，rpc的方式互通。



> 单体应用架构

应用中的所有应用服务都封装在一个应用中。无论是ERP，CRM或是其他系统，都把数据库访问和web访问等等功能放到一个war内。

优点：

- 易于开发和调试，方便部署；
- 需要拓展时只需要将war复制多份，然后放到多个服务器上，再做个负载均衡就可以了。

缺点：

- 哪怕修改一个很小的地方，都需要停掉整个微服务，重新打包，重新部署这个war包；
- 特别是对于大型应用，我们不可能将所有内人放在一个应用里，所以如何维护和分工；



> 微服务架构

所谓微服务架构，就是把每个功能独立出来，把独立出来的功能元素动态组合，需要的功能才拿去组合，需要多一些时可以整合多个功能元素。所以微服务架构是对功能元素的复制，而没有对整个应用进行复制。

优点：

- 节省调用资源
- 每个功能元素的服务都是一个可替换额，可独立升级的软件代码；

<img src="https://i.loli.net/2021/05/28/K3YwahSrFUZVjoz.png" alt="image-20210527162211835" style="zoom:50%;float:left" />

自由组装。



[微服务架构（Microservices） | 黯羽轻扬 (ayqy.net)](http://www.ayqy.net/blog/微服务架构（microservices）/)

<img src="https://i.loli.net/2021/05/28/jA7QtGN1oezMuwP.png" alt="image-20210527162726331" style="zoom: 67%;float:left" />



# 第一个SpringBoot

- jdk1.8
- maven3.6
- springboot
- idea

创建：

- 官方提供了快速生成的网站

  <img src="https://i.loli.net/2021/05/28/wi1sHrO6LP7FYWD.png" alt="image-20210527164208223" style="zoom:50%;float:left" />

- idea继承了了这个网站



项目结构:

需要在HellowordApplication**同级目录**下建包

<img src="https://i.loli.net/2021/05/28/39S7YIyC8ELO1Hd.png" alt="image-20210527165327537" style="zoom: 80%;float:left" />



测试：@RestController<=>@RequestMapping+@RequestBody；

接口自动装配了，写了就能直接运行。

<img src="https://i.loli.net/2021/05/28/8D64yhAimGZSFdt.png" alt="image-20210527165507550" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/28/7tfCl4XxqD9dOK3.png" alt="image-20210527165901633" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/28/8T42kScK7mQebsd.png" alt="image-20210527170012011" style="zoom:80%;float:left" />

springboot所有依赖都是使用Spring-boot开头：

<img src="https://i.loli.net/2021/05/28/XHSAVUO2EwfP7zb.png" alt="image-20210527170150176" style="zoom:80%;float:left" />

这里的web依赖用于实现http接口，依赖中包含了Springmvc，官网描述：

使用springmvc构建web包括restful的应用程序的入门者，使用Tomcat作为默认嵌入式容器。



packget打包成jar包，不依赖其他东西直接可执行：

<img src="https://i.loli.net/2021/05/28/Sjh2oGKyTNR5gYA.png" alt="image-20210527170838662" style="zoom:67%;float:left" />



> 使用idea创建第一个SpringBoot程序

<img src="https://i.loli.net/2021/05/28/koT6DRVJWyNu1X3.png" alt="image-20210527171405368" style="zoom:50%;float:left" />



删除多余文件：

<img src="https://i.loli.net/2021/05/28/xs2vwKB7LVz1aXk.png" alt="image-20210527171901367" style="zoom: 67%;float:left" />



导入web依赖：

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <version>2.5.0</version>
</dependency>
```

spring-boot-starter默认就是一个启动器。

测试：

```java
@Controller
@RequestMapping("/test01/")
public class hello {
    //返回字符串
    @RequestMapping("/hello")
    @ResponseBody
    public String test01(){
        return "我的第一个SpringBoot程序";
    }
}
```

<img src="https://i.loli.net/2021/05/28/sgCpQLtPRdE3lOJ.png" alt="image-20210527174749013" style="zoom:67%;float:left" />



可以直接在application.properties配置文件中修改端口号：

```properties
server.port=8081
```

创建自己的banner

<img src="https://i.loli.net/2021/05/28/IGdEVF3baKe68WO.png" alt="image-20210527180327437" style="zoom:67%;float:left" />



## banner.txt

```java
          _____                    _____                    _____                    _____
         /\    \                  /\    \                  /\    \                  /\    \
        /::\____\                /::\    \                /::\    \                /::\____\
       /::::|   |               /::::\    \              /::::\    \              /:::/    /
      /:::::|   |              /::::::\    \            /::::::\    \            /:::/    /
     /::::::|   |             /:::/\:::\    \          /:::/\:::\    \          /:::/    /
    /:::/|::|   |            /:::/__\:::\    \        /:::/__\:::\    \        /:::/    /
   /:::/ |::|   |           /::::\   \:::\    \      /::::\   \:::\    \      /:::/    /
  /:::/  |::|___|______    /::::::\   \:::\    \    /::::::\   \:::\    \    /:::/    /      _____
 /:::/   |::::::::\    \  /:::/\:::\   \:::\    \  /:::/\:::\   \:::\    \  /:::/____/      /\    \
/:::/    |:::::::::\____\/:::/  \:::\   \:::\____\/:::/  \:::\   \:::\____\|:::|    /      /::\____\
\::/    / ~~~~~/:::/    /\::/    \:::\  /:::/    /\::/    \:::\   \::/    /|:::|____\     /:::/    /
 \/____/      /:::/    /  \/____/ \:::\/:::/    /  \/____/ \:::\   \/____/  \:::\    \   /:::/    /
             /:::/    /            \::::::/    /            \:::\    \       \:::\    \ /:::/    /
            /:::/    /              \::::/    /              \:::\____\       \:::\    /:::/    /
           /:::/    /               /:::/    /                \::/    /        \:::\__/:::/    /
          /:::/    /               /:::/    /                  \/____/          \::::::::/    /
         /:::/    /               /:::/    /                                     \::::::/    /
        /:::/    /               /:::/    /                                       \::::/    /
        \::/    /                \::/    /                                         \::/____/
         \/____/                  \/____/                                           ~~

```







# 自动装配原理

## pom.xml

核心依赖spring-boot-dependencies在父工程中：

<img src="https://i.loli.net/2021/05/28/ef4TZXQEw5HL6F7.png" alt="image-20210527180733724" style="zoom:50%;float:left" />

在引入一些SpringBoot依赖的时候不需要指定版本就是因为有这个版本仓库。



## 启动器

就是Springboot的启动场景。

<img src="https://i.loli.net/2021/05/28/Ns4LrGn1zo6mHQt.png" alt="image-20210527180932487" style="zoom:67%;float:left" />

比如spring-boot-starter-web就会帮我们导入外部环境的所有依赖。



SpringBoot将所有的功能场景都变成了一个个启动器。

<img src="https://i.loli.net/2021/05/28/uCeYxy5nNboPGUX.png" alt="image-20210527181625903" style="zoom:67%;float:left" />



## 主程序

<img src="https://i.loli.net/2021/05/28/WMEyJpYzqoQnxv5.png" alt="image-20210527182013533" style="zoom:67%;float:left" />

注解：

- @SpringBootApplication

  <img src="https://i.loli.net/2021/05/28/V9rlGesvb6Io4kt.png" alt="image-20210527182156808" style="zoom:67%;float:left" />

  

  - @SpringBootConfiguration

    SpringBoot的配置

    <img src="https://i.loli.net/2021/05/28/EPehQbWclG7M4q3.png" alt="image-20210527182455513" style="zoom:67%;float:left" />

​               @Configuration



- @EnableAutoConfiguration

  - AutoConfigurationPackage

    自动导入配置,包注册

    <img src="https://i.loli.net/2021/05/28/rZdgabKfXp5hiSj.png" alt="image-20210527182728124" style="zoom:67%;float:left" />

  - @AutoConfigurationImportSelector.class  自动导入选择

    <img src="https://i.loli.net/2021/05/28/tl16UoQBngyrF8O.png" alt="image-20210527183227657" style="zoom:67%;float:left" />

    获取所有文件的配置：

    <img src="https://i.loli.net/2021/05/28/sFoHRWd9M5DkzeO.png" alt="image-20210527183648069" style="zoom:67%;float:left" />

    获取候选的配置:

    <img src="https://i.loli.net/2021/05/28/Z3zu6LlQ8wD4OdP.png" alt="image-20210527184203756" style="zoom:67%;float:left" />

    自动配置的核心文件：

    <img src="https://i.loli.net/2021/05/28/yTNAda4XFb3wU61.png" alt="image-20210527184524919" style="zoom:67%;float:left" />

    springboot工厂的加载：

    <img src="https://i.loli.net/2021/05/28/2qwGu71e3rRZCa6.png" alt="image-20210527185611491" style="zoom:67%;float:left" />

    

##   小结

SpringBoot中所有自动配置都是在启动的时候并加载：spring.factories包含所有的自动配置类，但是要导入对应的start启动器其对应的自动装配配置才能生效。

1. SpringBoot在启动的时候，从类路径下/META-INF/spring.factories获取指定的值；
2. 将这些自动配置类导入容器，自动配置就会生效，帮我们自动配置；
3. 以前我们需要自动配置的东西，现在SpringBoot帮我们做了；
4. 整个JavaEE，解决方案和自动配置的东西都在spring-boot-autoconfigure-2.4.4.jar下；
5. 它会将所有需要导入的组件，以类名的方式返回，这些组件就会被添加到容器；
6. 容器中也会存在非常多的xxxAutoConfiguration(@Bean)的文件，就是这些类给容器中导入了这个场景的所有组件；并自动配置，@Configuration  ,JavaConfig；
7. 有了自动配置类，就免去了我们手动编写配置文件的工作。

<img src="https://i.loli.net/2021/05/28/aNdO4zbqFHvVi6Y.png" alt="自动配置原理" style="zoom:150%;float:left" />

<img src="https://i.loli.net/2021/05/28/HSwB3XEJYTdvV9l.png" alt="image-20210527210042878" style="zoom: 200%; float: left;" />





# 主启动类运行

<img src="https://i.loli.net/2021/05/28/w76sjabHeRNOIox.png" alt="image-20210527210248285" style="zoom:50%;float:left" />

这个main方法其实是开启了一个服务。

分析该方法主要两部分，一部分是SpringApplication的实现，二是run方法的实现。

## SpringApplication类

JavaConfig @Configuraion @Bean

主要做4件事：

1. 推断应用的类型是普通的项目还是web项目；
2. 查找并加载所有可用初始化器，设置到intializers属性中；
3. 找出所有的应用程序监听器，设置到listens属性中；
4. 推断并设置main方法的定义类，找到运行的主类。

构造器：

<img src="https://i.loli.net/2021/05/28/GFmKvuiWaD4SPk3.png" alt="image-20210527210819367" style="zoom:80%;float:left" />



启动：

<img src="https://i.loli.net/2021/05/28/uYZ2LaqdCfbHNvA.png" alt="image-20210527211208936" style="zoom:150%;float:left" />





<img src="https://i.loli.net/2021/05/28/3UFHkdxGpyAjOTK.png" alt="image-20210527211400356" style="zoom:150%;float:left" />



<img src="https://i.loli.net/2021/05/28/jOZ2dQ1X6kWVLHR.png" alt="image-20210527211545790" style="zoom:150%;float:left" />



<img src="https://i.loli.net/2021/05/28/mXw7O62x8zS5EZf.png" alt="image-20210527211915139" style="zoom:50%;float:left" />



# yaml

## 概述

<img src="https://i.loli.net/2021/05/28/PJkwidGRrD1Cz6s.png" alt="image-20210527212452912" style="zoom: 67%;float:left" />



[(25条消息) Springboot-官方详细配置_叶巨岩的博客-CSDN博客](https://blog.csdn.net/weixin_38023579/article/details/82904245)



<img src="https://i.loli.net/2021/05/28/QhgfUGJYvax5cMH.png" alt="image-20210527213442558" style="zoom:67%;float:left" />



*YAML*是"YAML Ain't a Markup Language"（YAML不是一种[标记语言](https://baike.baidu.com/item/标记语言)）的[递归缩写](https://baike.baidu.com/item/递归缩写)。开发的这种语言时，*YAML* 的意思其实是："Yet Another Markup Language"（仍是一种[标记语言](https://baike.baidu.com/item/标记语言)），但为了强调这种语言以数据做为中心，而不是以标记语言为重点，而用反向缩略语重命名。

<img src="https://i.loli.net/2021/05/28/oPbupIxmh2VXLvg.png" alt="image-20210527213904623" style="zoom:67%;float:left" />



properties只能保存键值对。

application.yaml：对空格的要求非常严格，层级关系

```yaml
# 普通的k=name
name: 上官
# 对象
student:
  name: 婉儿
  age: 18

# 行内写法
student2: {name:婉儿,age:18}

# 数组
pets:
  - cat
  - dog
  - pig

pets2: [cat,dog,pig]
```

application.yaml强大之处在于可以注入到配置类和实体类当中。



## 属性赋值

### yaml

Spring方式：@Value()  @Autowired

```java
@Component
@Data
@AllArgsConstructor
@NoArgsConstructor
public class Dog {
    @Value("西西")
    private String name;
    @Value("9")
    private Integer age;
}
```

自动装配：

```java
    @Autowired
    //有很多条狗时用@Qualifier()指定
    Dog dog;
    @Test
    void contextLoads() {
    }
```

缺点：需要在源代码里配多个实体比较麻烦。



> 通过yaml实现   @ConfigurationProperties

```yaml
Person:
  name: 上官${ramdon.int}
  age: 18
  happy: true
  birth: 2021/5/27
  map: {k1: v1,k2: v2}
  list:
    - music
    - code
    - beauty
  dog:
    name: ${person.name:helllo}_花花
    age: 3
```

<img src="https://i.loli.net/2021/05/28/s7qOklTDAue4UMY.png" alt="image-20210528084434703" style="zoom:50%;float:left" />

```xml
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-configuration-processor</artifactId>
            <optional>true</optional>
        </dependency>
```



绑定：@ConfigurationProperties(prefix = "person")

```java
@Component
@Data
@AllArgsConstructor
@NoArgsConstructor
@ConfigurationProperties(prefix = "person")
public class Person {
    private String name;
    private Integer age;
    private boolean happy;
    private Date birth;
    private Map<String,Object> map;
    private List<Object> list;
    private Dog dog;
}
```



测试：

```java
    @Autowired
    private Person person;
    @Test
    void contextLoads() {
        System.out.println(person);
    }
```



### properties

指定配置文件。

```java
@PropertySource(value = "classpath:mf.properties")
```

<img src="https://i.loli.net/2021/05/28/l9xkwA4B8GyoE7K.png" alt="image-20210528082610745" style="zoom:67%;float:left" />

<img src="https://i.loli.net/2021/05/28/fTjOQKsd7lkhMYm.png" alt="image-20210528082639847" style="zoom:67%;float:left" />

还需要取，所以相对yaml不是很灵活。

```java
@PropertySource(value = "classpath:mf.properties")//加载指定的配置文件
public class Person {
    //Spring的El表达式取出配置文件的值
    @Value("${name}")
    private String name;
}
```



JavaConfig绑定配置文件的值可以采取以上两种方式。



## 对比

<img src="https://i.loli.net/2021/05/28/OWjgT9VilSHzUct.png" alt="image-20210528084612635" style="zoom:67%;float:left" />



- 松散绑定：比如yaml中写的last-name，这个和lastName是一样的。
- JSR303数据校验：这个就是我们可以在字段增加一层过滤器验证，可以保证数据合法性。
- 复杂类型封装：yaml中可以封装对象，使用@value就不行。

如果只是想获取其中的一个值可以使用@value,但是官方强烈推荐yaml.

### JSR303

> @Validated//开启数据校验

注解启动器：

```java
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-validation</artifactId>
        </dependency>
```



```java
@Component //注册bean
@Data
@AllArgsConstructor
@NoArgsConstructor
@ConfigurationProperties(prefix = "person")
@Validated//数据校验
public class Person {
    @Email(message="必须为邮件格式")
    private String name;
    @Max(value = 20,message="有点老哦")
    private Integer age;
    @NotNull(message="happy不能为空")
    private boolean happy;
    private Date birth;
    private Map<String,Object> map;
    private List<Object> list;
    private Dog dog;
}
```

有个小问题就是：Boolean不能用@NotNull判断。。。

<img src="https://i.loli.net/2021/05/28/d4K6EQurR5TDsob.png" alt="image-20210528091705287" style="zoom:67%;float:left" />

<img src="https://i.loli.net/2021/05/28/brqUD5n4fOxwayG.png" alt="image-20210528090255570" style="zoom:67%;float:left" />



## 环境配置

### 概述

多环境配置以及配置文件位置。

<img src="https://i.loli.net/2021/05/28/oaBmqbWOsyI6LHc.png" alt="image-20210528093311141" style="zoom:80%;float:left" />

<img src="https://i.loli.net/2021/05/28/LJ3bp1INvotdQXu.png" alt="image-20210528093820770" style="zoom:67%;float:left" />



四个有优先级：1>4>2>3  我们默认配置是3优先级最低的一个

<img src="https://i.loli.net/2021/06/02/bUAJZpycLhMVvge.png" alt="image-20210528094705083" style="zoom:67%;float:left" />



### 多环境切换

真实开发：测试环境，生产环境。。。

<img src="https://i.loli.net/2021/06/02/B2ncQDLlXKjRzN8.png" alt="image-20210528095809788" style="zoom:67%;float:left" />

profile是Spring对不同环境提供不同配置功能的支持，可以激活不同的环境版本，实现快速切换环境：

> 方式一：多配置文件

```yaml
server:
  port: 8081
#springboot的多环境配置，选择激活那一套环境
spring:
  profiles:
    active: dev
```



以上写法是properties的，懒得改了；



现在介绍yaml的可以直接在一个yaml文件配置多套环境：

```yaml
server:
  port: 8081
spring:
  profiles:
    active: dev
---
server:
  port: 8082
spring:
  profiles: dev
---
server:
  port: 8083
spring:
  profiles: test
```



## 自动配置再讲解

配置文件到底可以写什么。。。

与spring.factories具有非常强的联系。

举例：codec.CodecsAutoConfiguration

```java
@Configuration(//表示是一个配置类
    proxyBeanMethods = false
)
@ConditionalOnClass({CodecConfigurer.class, WebClient.class})//spring底层注解，根据不同条件判断当前类是否生效
@AutoConfigureAfter({JacksonAutoConfiguration.class})
@EnableConfigurationProperties({CodecProperties.class})//自动配置的配置属性
```

在我们的配置文件中能配置的东西都存在一个固有的规律：

 xxxAutoConfiguration--->xxxProperties--->配置文件绑定---》我们就可以使用自定义配置了。

<img src="https://i.loli.net/2021/06/02/4aGD8wfNcUq2Fvg.png" alt="image-20210528103225858" style="zoom:67%;float:left" />



自动装配原理精髓：

1. SpringBoot启动加载大量的自动配置类；
2. 我们看看需要的功能有没有在SpringBoot默认写好的自动配置类中；
3. 然后再看这个自动配置类中到底配置了那些组件，只要我们要用的组件存在其中我们就不需要手动配了；
4. 给容器中自动配置类添加组件时，会从properties类中获取某些属性，我们只需要在配置文件中指定这些属性的值就好。

xxxAutoConfiguration:自动配置类；给容器中添加组件；

xxxProperties:封装配置文件中相关属性。----》SpringBoot配置 yaml



查看哪些配置类生效：debug: true



# Web开发

## 概述

jar:webapp!

自动装配，SpringBoot到底帮我们配置了什么东西？可以修改吗？可以扩展吗？

- xxxAutoConfiguration：向容器中自动配置组件；
- xxxProperties：自动配置类装配配置文件中自定义的内容。



web开发要解决的问题：

- 导入静态资源。。。
- 首页
- jsp--》模板引擎Thymeleaf
- 装配和拓展springmvc
- 增删改查
- 拦截器
- 中英文切换



## 静态资源

> 方式一

<img src="https://i.loli.net/2021/06/02/7gyXwcbZsFYUSEv.png" alt="image-20210528115839238" style="zoom:50%;float:left" />

webjars是什么？

<img src="https://i.loli.net/2021/06/02/8pkCD5w6hb7NKeW.png" alt="image-20210528114434557" style="zoom: 50%; float: left;" />



<img src="https://i.loli.net/2021/06/02/EIzwX1fLYCK4Aos.png" alt="image-20210528114544084" style="zoom: 50%; float: left;" />



> 所支持的目录

<img src="https://i.loli.net/2021/06/02/nwDoN3X7Uum8l1B.png" alt="image-20210528120448732" style="zoom:50%;float:left" />

<img src="https://i.loli.net/2021/06/02/b6ODcEZgryjIoYX.png" alt="image-20210528120520689" style="zoom:50%;float:left" />



在/**下的东西都会在这四个静态资源的目录下找：

<img src="https://i.loli.net/2021/06/02/uix5lMpOCsgH7IY.png" alt="image-20210528153028656" style="zoom:67%;float:left" />



优先级：resource>static>public

一般：public放js，static放图片，resource放上传文件。



总结：

1. 在SpringBoot，我们可以使用一下几种方式处理静态资源
   - webjars   `映射localhost:808/webjars/`
   - /**>resource>static(默认)>public`直接映射localhost:808/`



## 首页

<img src="https://i.loli.net/2021/06/02/fNzcGj6Dh3WOKvE.png" alt="image-20210528160108177" style="zoom:67%;float:left" />



```java
//在template下的所有页面之只能通过controller来跳转
//需要模板引擎的支持
@Controller
public class Index {
    @RequestMapping("/index")
    public String index(){
        return "index";
    }

}
```



修改图片为ico:先另存为这串名字然后在删除；

直接另存为ico就行了。



## thymeleaf

### 概述

<img src="https://i.loli.net/2021/06/02/2iCgDFV15IT3W4c.png" alt="image-20210528163103703" style="zoom:67%;float:left" />



找到依赖：高版本还不好找

```java
https://docs.spring.io/spring-boot/docs/2.0.3.RELEASE/reference/htmlsingle/#using-boot-starter
```

导入依赖：

```xml
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>
```





<img src="https://i.loli.net/2021/06/02/xCo2ZJYsf36bjA1.png" alt="image-20210528171040091" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/06/02/A6rfz79olqW5KY1.png" alt="image-20210528171424164" style="zoom:67%;float:left" />



### 语法

导入约束

```html
<html lang="en" xmlns:th="http://www.thymeleaf.org">
```

```html
${...} 变量表达式，Variable Expressions

@{...} 链接表达式，Link URL Expressions

#{...} 消息表达式，Message Expressions

~{...} 代码块表达式，Fragment Expressions

*{...} 选择变量表达式，Selection Variable Expressions
```

测试：

```java
@Controller
public class Index {
    @RequestMapping("/test")
    public String test(Model model){
        model.addAttribute("msg","Thymeleaf by Model");
        return "test";
    }
}
```

所有的html元素都可以被thymeleaf替换接管：th:元素名

```html
<h2>thymeLeaf页面</h2>
<div th:text="${msg}"></div>
```



> 转义  th:utext

```java
 model.addAttribute("msg","<h1>Thymeleaf by Model</h1>");
```

```html
<div th:text="${msg}"></div>
<div th:utext="${msg}"></div>
```



> 遍历 th:each

```java
model.addAttribute("users", Arrays.asList("上官","婉儿","秦时","明月"));
```



```html
<hr>
<h4 th:each="user:${users}" th:text="${user}"></h4>
```



## MVC配置原理

[SpringMVC自动配置 - Maple_XL - 博客园 (cnblogs.com)](https://www.cnblogs.com/junlinsky/p/13262259.html)



> 自定义视图解析器



<img src="https://i.loli.net/2021/06/02/DyGKX9tSEeaF1Wf.png" alt="image-20210528181204711" style="zoom:80%;float:left" />



> 格式转换器

<img src="https://i.loli.net/2021/06/02/AMujG4FdZ93p2T6.png" alt="image-20210528181849198" style="zoom:80%;float:left" />

<img src="https://i.loli.net/2021/06/02/Kc18hNfFdjuDYHn.png" alt="image-20210528182103585" style="zoom:67%;foat:left" />



```properties
#自定义的日期格式化
#spring.mvc.format.date=""
```



```java
//拓展springMVC
@Configuration
public class MyMvcConfig implements WebMvcConfigurer {
    //自定义视图跳转
    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        registry.addViewController("/mafu").setViewName("test");
    }
}
```

如果我们要拓展SpringMVC，官方建议写一个config类。

但是不能加@EnableWebMvc：这东西就是导入了一个类，DelegatingWebMvcConfiguration：从容器中获取所有的webmvcConfig



在SpringBoot中，有非常多的xxx Configuration帮助我们进行拓展配置。



# 员工系统

## 准备

导入静态资源

<img src="https://i.loli.net/2021/06/02/vuElHeNyABVScR4.png" alt="image-20210528202236966" style="zoom:80%;float:left" />

pojo:

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class Employee {
    private Integer eId;
    private String eName;
    private String email;
    private Integer gender;

    private Department department;
    private Date date;
}
```

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class Department {
    private Integer dId;
    private String dName;
}
```



dao:

```java
@Repository
public class DepartmentDao {
    //模拟数据库中的数据
    private static Map<Integer, Department> department=null;
    static {
        department=new HashMap<>();//创建一个部门表
        department.put(101,new Department(101,"工部"));
        department.put(102,new Department(102,"礼部"));
        department.put(103,new Department(103,"吏部"));
        department.put(104,new Department(104,"户部"));

    }

    //获取所有部门信息
    public Collection<Department> getAllDepartment(){
        return department.values();
    }

    //通过id得到部门
    public Department getDepartmentById(Integer id){
        return department.get(id);
    }

}
```



```java
@Repository
public class EmployeeDao {
    //模拟数据库中的数据
    private static Map<Integer,Employee> employees=null;
    @Autowired
    private DepartmentDao departmentDao;
    static {
        employees=new HashMap<>();//创建一个部门表
        employees.put(1001,new Employee(1001,"蒙恬","111.qqCom",0,new Department(101,"工部"),new Date()));
        employees.put(1002,new Employee(1002,"易小川","112.qqCom",1,new Department(101,"工部"),new Date()));
        employees.put(1003,new Employee(1003,"千禧","113.qqCom",1,new Department(103,"吏部"),new Date()));
        employees.put(1004,new Employee(1004,"小凯","114.qqCom",0,new Department(104,"户部"),new Date()));

    }

    //增加一个员工，主键自增
    public static Integer initId=105;
    public void add(Employee employee){
        if (employee.getEId()==null) employee.setEId(initId++);
        employees.put(employee.getEId(),employee);
    }
    //获取全部员工
    public Collection<Employee> getAllEmployee(){
        return employees.values();
    }
    public Employee getEmployeeById(Integer id){
        return employees.get(id);
    }
    public void deleteEmployeeById(Integer id){
        employees.remove(id);
    }

}

```



完成首页映射：根目录下的东西一般在config下配就行。

```java
@Controller
public class IndexController {
    @RequestMapping({"/", "index.html"})
    public String index(){
        return "index";
    }
}
```

也可以通过config自定义配置：都可访问到走视图解析后的index.html

```java
//拓展springMVC
@Configuration
public class MyMvcConfig implements WebMvcConfigurer {
    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        registry.addViewController("/").setViewName("index");
        registry.addViewController("/index.html").setViewName("index");
    }
}
```



首页配置：注意点，所有的静态资源都需要使用thymeleaf接管。

url直接使用@{}

也可以改动

```properties
server.servlet.context-path=/mf
```

<img src="https://i.loli.net/2021/06/02/QTW3iXkuP9BeJqr.png" alt="image-20210528221007368" style="zoom: 50%;float:left" />



使用thymeleaf修改前端html。

```properties
#关闭模板引擎的缓存
spring.thymeleaf.cache=false
```

在线的连接不用改。



解决端口占用问题：

首先找到占用端口的pid

<img src="https://i.loli.net/2021/06/02/cbMunPwrLzaKFSH.png" alt="image-20210528210519185" style="zoom:80%;float:let" />





## 国际化

环境：

<img src="https://i.loli.net/2021/06/02/Q5y3YcadASFhuxr.png" alt="image-20210529104147258" style="zoom:67%;float:left" />

实现中英文切换。

<img src="D:\Typora\md\picture\SpringBoot\image-20210528221710732.png" alt="image-20210528221710732" style="zoom:80%;float:left" />

自动化国际转换的类：

`MessageSourceAutoConfiguration`



```properties
#配置文件的真实位置
spring.messages.basename=i18n.login
```

取值：

<img src="https://i.loli.net/2021/06/02/liURAw9CPbz81Nc.png" alt="image-20210529110113933" style="zoom: 67%;float:left" />



国际化消息转换类：

`AcceptHeaderLocaleContextResolver`



SpringMVCAutoConfig：本地解析  用户配了就走，没有就走默认的。

<img src="https://i.loli.net/2021/06/02/1yHFwh7z3kgYuGE.png" alt="image-20210529110622389" style="zoom:67%;float:left" />



继承接口编写配置类：

```java
public class MyLocaleResolver implements LocaleResolver {
    //解析请求
    @Override
    public Locale resolveLocale(HttpServletRequest httpServletRequest) {
        //获取请求中的语言参数
        String language = httpServletRequest.getParameter("l");
        Locale requestLocale = httpServletRequest.getLocale();//如果没有就使用默认的
        if (!StringUtils.isEmpty(language)){//如果不为空就使用我们自己传过来的
             //zh_CN 国家，地区
            String[] split = language.split("_");
            requestLocale = new Locale(split[0], split[1]);
        }
        return requestLocale;
    }

    @Override
    public void setLocale(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Locale locale) {

    }
}
```



```html
			<a class="btn btn-sm" th:href="@{/index.html(l='zh_CN')}">中文</a>
			<a class="btn btn-sm" th:href="@{/index.html(l='en_US')}">English</a>
```





MyMvcConfig中配置生效：

```java
    @Bean//自定义的国际化组件就生效了
    public LocaleResolver localeResolver(){
        return new MyLocaleResolver();
    }
```



build后运行：

<img src="https://i.loli.net/2021/06/02/q2SiZn5KHyuvQId.png" alt="image-20210529113140589" style="zoom: 50%; float: left;" />





<img src="https://i.loli.net/2021/06/02/QcaDJPEbmStCK3s.png" alt="image-20210529113207910" style="zoom: 50%; float: left;" />



小结:注意点 

1. 我们需要配置i18n文件；
2. 如果需要在项目中按钮自动切换，需要自定义组件LocaleResolver；
3. 然后配置到Spring容器，@Bean；
4. #{}

## 登录

```html
<form class="form-signin" th:action="@{/user/login}">
    
<p style="color: red" th:text="${error}" th:if="${not #strings.isEmpty(error)}"></p>
```

编写controller

```java
@Controller
public class LoginController {
    @RequestMapping("/user/login")
    public String login(@RequestParam("username") String username,
                        @RequestParam("password") String password,
                        Model model){
        //具体的业务
        if ("admin".equals(username)&&"123".equals(password))
            return "dashboard";
        else{
            model.addAttribute("error","用户名或密码错误");
            return "index";
        }
    }
}

```



<img src="https://i.loli.net/2021/06/02/OoZkU4Bndyc7QJh.png" alt="image-20210529120601055" style="zoom:80%;float:left" />

伪造页面：

```java
 registry.addViewController("/main.html").setViewName("dashboard");
```

```java
        //具体的业务
        if ("admin".equals(username)&&"123".equals(password))
            return "redirect:/main.html";
```

<img src="https://i.loli.net/2021/06/02/79tmrzAUxTyOEwR.png" alt="image-20210529120651811" style="zoom:80%;float:left" />



## 拦截器

`HandlerInterceptor`

<img src="https://i.loli.net/2021/06/02/inXCmsrMh3EGlov.png" alt="image-20210529122428367" style="zoom:80%;float:left" />



自己编写的拦截器：

```java
public class LoginHandlerInterceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        //登录成功应该有用户session
        if (request.getSession().getAttribute(Constant.USER_SESSION)==null){
            request.setAttribute("error","没有权限请先登录");
            request.getRequestDispatcher("/index.html").forward(request,response);
        }
        return false;
    }

}

```



配置重写拦截器：要拦截那些url除了那些。

```java
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new LoginHandlerInterceptor())
                .addPathPatterns("/**")
                .excludePathPatterns("/","/index.html","/user/login","/css/*","/js/*","/img/*");
    }
```

不要Constant类了：

<img src="https://i.loli.net/2021/06/02/kBuwXNbtlK8IvgY.png" alt="image-20210529124819822" style="zoom:67%;float:left" />



## 员工列表

<img src="https://i.loli.net/2021/06/02/g6boFQVyqLBATc4.png" alt="image-20210529130506644" style="zoom:80%;float:left" />

```java
@Controller
public class EmployeeController {
    //controller层调service层

    //查询所有员工
    @Autowired
    EmployeeDao employeeDao;

    @RequestMapping("/employee")
    public String list(Model model){
        Collection<Employee> allEmployee = employeeDao.getAllEmployee();
        model.addAttribute("allEmployee",allEmployee);
        return "employee/list";
    }

}
```



###  fragment

> 抽取公共页面:头部和侧边栏

dashboard.html

<img src="https://i.loli.net/2021/06/02/cd3f4EMoSYBh25U.png" alt="image-20210529131135424" style="zoom:67%;float:left" />

list.html:

```html
<!-- 公共头部-->
<div th:insert="~{dashboard::topbar}"></div>
<!-- 公共侧边栏-->
<div th:insert="~{dashboard::sidebar}"></div>
```



提取到commons

<img src="https://i.loli.net/2021/06/02/AX6lq2eINayZVhY.png" alt="image-20210529141406652" style="zoom:80%;float:left" />



> 实现点击高亮:active

url传参

```html
<!-- 传递参数给组件-->
<div th:replace="~{commons/commons::sidebar(active='main')}"></div>
```



接收：if判断

```html
  <a th:class="${active=='main'?'nav-link active':'nav-link'}" th:href="@{#}">
```



replace是直接替换掉而insert是嵌套一层，推荐前者。



### 查询

列表循环展示

```html
<thead>
    <tr>
        <th>编号</th>
        <th>姓名</th>
        <th>邮箱</th>
        <th>性别</th>
        <th>部门</th>
        <th>生日</th>
        <th>操作</th>
    </tr>
</thead>
<tbody>
    <tr th:each="employee:${allEmployee}">
        <td th:text="${employee.getEId()}"></td>
        <td th:text="${employee.getEName()}"></td>
        <td th:text="${employee.getEmail()}"></td>
        <td th:text="${employee.getGender()==0?'女':'男'}"></td>
        <td th:text="${employee.getDepartment().getDName()}"></td>
        <td th:text="${#dates.format(employee.getBirth(),'yyyy/MM/dd HH:mm:ss')}"></td>
        <td>
            <button class="btn btn-sm btn-primary">修改</button>
            <button class="btn btn-sm btn-danger">删除</button>
        </td>
    </tr>
```



<img src="https://i.loli.net/2021/06/02/ronzsAlcS6yC2p8.png" alt="image-20210529170729701" style="zoom:50%;float:left" />



### 添加

1. 按钮提交
2. 跳转添加页面
3. 添加成功
4. 返回首页

```java
    //restful风格
    @GetMapping("/add")
    public String toAddPage(Model model){
        //查出所有部门信息
        Collection<Department> allDepartment = departmentDao.getAllDepartment();
        model.addAttribute("allDepartment",allDepartment);
        return "employee/add";
    }
    @PostMapping ("/add")
    public String addEmployee(Employee employee){
        System.out.println("添加=》"+employee);
        //添加操作
        employeeDao.add(employee);
        return "redirect:/main.html";
    }
```



```html
<form th:action="@{/add}" method="post">
    <div class="form-group">
        <label>姓名</label>
        <input type="text" class="form-control" name="eName">
    </div>
    <div class="form-group">
        <label>邮箱</label>
        <input type="email" class="form-control" name="email">
    </div>
    <div class="form-group">
        <label>性别</label>
        <br>
        <div class="form-check-inline">
            <label class="form-check-label">男&nbsp</label>
            <input type="radio" name="gander" value="1">
        </div>
        <div class="form-check-inline">
            <label class="form-check-label">女&nbsp</label>
            <input type="radio" name="gander" value="0">
        </div>
    </div>
    <div class="form-group">
        <label>部门</label>
        <select class="form-control" name="department.dId">
            <option disabled selected>请选择</option>
            <option th:each="department:${allDepartment}"
                    th:text="${department.getDName()}"
                    th:value="${department.getDId()}">
            </option>
        </select>
    </div>
    <div class="form-group">
        <input type="date" class="form-control" name="birth" placeholder="生日">
    </div>

    <button class="btn btn-sm btn-primary">添加员工</button>
</form>

```

EmployeeDao:按部门id对应

```java
 employee.setDepartment(departmentDao.getDepartmentById(employee.getDepartment().getDId()));
```



springboot默认的日期格式是/，修改日期设置：

```properties
spring.mvc.format.date=yyyy-MM-dd
```

<img src="https://i.loli.net/2021/06/02/Ip8J9dCXtvzNUm4.png" alt="image-20210529185104904" style="zoom:67%;float:left" />



### 修改

1. 修改按钮提交
2. 跳转到修改表单页面
3. 修改提交返回首页

```html
<a class="btn btn-sm btn-primary" th:href="@{/update/}+${employee.getEId()}">修改</a>
```

```java
    @GetMapping("/update/{eid}")
    public String toUpdatePage(@PathVariable("eid")Integer eid,Model model){
        //查出原来的数据
        Employee employee = employeeDao.getEmployeeById(eid);
        model.addAttribute("employee",employee);
        Collection<Department> allDepartment = departmentDao.getAllDepartment();
        model.addAttribute("allDepartment",allDepartment);
        return "employee/update";
    }
```

```html
<form th:action="@{/update}" method="post">
    <input type="hidden" th:value="${employee.getEId()}" name="eId">
    <div class="form-group">
        <label>姓名</label>
        <input type="text" class="form-control" name="eName" th:placeholder="${employee.getEName()}">
    </div>
    <div class="form-group">
        <label>邮箱</label>
        <input type="email" class="form-control" name="email" th:placeholder="${employee.getEmail()}">
    </div>
    <div class="form-group">
        <label>性别</label>
        <br>
        <div class="form-check-inline">
            <label class="form-check-label">男&nbsp</label>
            <input th:checked="${employee.getGender()==1}" type="radio" name="gander" value="1">
        </div>
        <div class="form-check-inline">
            <label class="form-check-label">女&nbsp</label>
            <input th:checked="${employee.getGender()==0}" type="radio" name="gander" value="0">
        </div>
    </div>
    <div class="form-group">
        <label>部门</label>
        <select class="form-control" name="department.dId">
            <option th:selected="${department.getDId()==employee.getEId()}"
                    th:each="department:${allDepartment}"
                    th:text="${department.getDName()}"
                    th:value="${department.getDId()}">
            </option>
        </select>
    </div>
    <div class="form-group">
        <label>生日</label>
        <input th:value="${#dates.format(employee.getBirth(),'yyyy-MM-dd')}" type="date" class="form-control" name="birth">
    </div>

    <button class="btn btn-sm btn-primary">修改信息</button>
</form>

```



```java
    @PostMapping("/update")
    public String updateEmployee(Employee employee){
        System.out.println("修改=》"+employee);
        employeeDao.add(employee);//存储员工的是哈希表，id不重复，添加即修改
        return "redirect:/employee";
    }
```

<img src="https://i.loli.net/2021/06/02/FdDL7zoKHUEtqYf.png" alt="image-20210529204405003" style="zoom:67%;float:left" />





### 删除

```html
<a class="btn btn-sm btn-danger"  th:href="@{/delete/}+${employee.getEId()}">删除</a>
```

```java
    @GetMapping("/delete/{eid}")
    public String deleteEmployee(@PathVariable("eid")Integer eid){
        employeeDao.deleteEmployeeById(eid);
        return "redirect:/employee";
    }
```

### 404

只需要在templates下建立error文件夹，编写404.html，报错后自然找到。

### 注销

```java
    @RequestMapping("/user/logout")
    public String logout(HttpSession session){
        session.invalidate();
        return "redirect:/main.html";
    }
```



# 网站如何写

前端：(强烈推荐使用模板，没有个几年年前端经验肯定写不了)

- 模板：模版之家，源码之家；
- 框架组件：BootStrap，LayUI....飞冰，element。。需要自己手动组合。
  - 栅格系统
  - 导航栏
  - 侧边栏
  - 表单

步骤：

1. 前端搞定：页面长什么样；
2. 设计数据库（难点）；
3. 前端能够独立运行，独立化工程；
4. 数据库接口如何对接：json，对象，all in one；
5. 前后端联调测试。



1）后台：

有几套自己熟悉的后台模板：工作必要。

推荐：LayUI的Xadmin模板。



2）前端：

至少自己能够通过前端框架组合出来一个网站 

          - index
          - about
          - blog
          - post
          - user



3）让网站能够独立运行

# 整合

## JDBC

对于数据层的访问，无论是关系型数据库还是非关系型的数据库，SpringBoot的底层都是采用SpringData的方式进行统一处理。

<img src="https://i.loli.net/2021/06/02/KlM2xjN5nzuCZa4.png" alt="image-20210529215131814" style="zoom:80%;float:left" />

springboot自动帮我们注入数据源：hikari

```java
@SpringBootTest
class Springboot04DataApplicationTests {

    @Autowired
    DataSource dataSource;

    @Test
    void contextLoads() {
        //查看默认数据源
        System.out.println(dataSource.getClass());
        Connection conn = dataSource.getConnection();
        System.out.println(conn);
        conn.close();
    }

}
```

探究源码：

<img src="https://i.loli.net/2021/06/02/xv8FyaOQVgwImTG.png" alt="image-20210530101555997" style="zoom:67%;float:left" />

与配置文件绑定

<img src="https://i.loli.net/2021/06/02/SmFAPGDIzoa1jEJ.png" alt="image-20210529221049521" style="zoom:67%;float:left" />



xxxTemplate :SpringBoot写好的Bean    

直接使用即可。

<img src="https://i.loli.net/2021/06/02/jKzwDF1TGx2AqZP.png" alt="image-20210530093828968" style="zoom:67%;float:left" />

jdbc、redis、CRUD

JDBC的配置

<img src="https://i.loli.net/2021/06/02/PDC1Q5JLhRSFNzx.png" alt="image-20210530093549162" style="zoom:67%;float:left" />



测试：

导入web依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

<img src="https://i.loli.net/2021/06/02/YIPGCLxjZokUiVR.png" alt="image-20210530094424475" style="zoom:67%;float:left" />

```java
@RestController
public class JdbcController {
    @Autowired
    JdbcTemplate jdbcTemplate;
    //查询数据库的所有信息
    //没有实体类，如何获取数据库中的东西，Map？
    @GetMapping("/userList")
    public List<Map<String,Object>> userList(){
        String sql="select * from tb_user";
        return jdbcTemplate.queryForList(sql);
    }

}
```

SpringBoot自动提交事务

```java
    @GetMapping("/addUser")
    public int addUser(){
        String sql="insert into tb_user(id,username,pwd) values (?,?,?)";
        //封装
        Object[] objects = new Object[3];
        objects[0]=4;
        objects[1]="韩信";
        objects[2]="039";
        return jdbcTemplate.update(sql,objects);
    }
    @GetMapping("/updateUser")
    public int updateUser(){
        String sql="update tb_user set pwd=? where id=?";
        Object[] objects = new Object[2];
        objects[0]="990";
        objects[1]="4";
        return jdbcTemplate.update(sql,objects);
    }
```

restful风格传参：

```text
http://localhost:8080/deleteUser/3
```

```java
  @GetMapping("/deleteUser/{id}")
    public int deleteUser(@PathVariable("id")int id){
        String sql="delete from tb_user where id=?";
        return jdbcTemplate.update(sql,id);
    }
```



## Druid

> 概述

**Druid是一个JDBC组件，它包括三部分：** 

- DruidDriver 代理Driver，能够提供基于Filter－Chain模式的插件体系。 
- DruidDataSource 高效可管理的数据库连接池。 
- SQLParser 

**Druid可以做什么？** 

1) 可以监控数据库访问性能，Druid内置提供了一个功能强大的StatFilter插件，能够详细统计SQL的执行性能，这对于线上分析数据库访问性能有帮助。 

2) 替换DBCP和C3P0。Druid提供了一个高效、功能强大、可扩展性好的数据库连接池。 

3) 数据库密码加密。直接把数据库密码写在配置文件中，这是不好的行为，容易导致安全问题。DruidDruiver和DruidDataSource都支持PasswordCallback。 

4) SQL执行日志，Druid提供了不同的LogFilter，能够支持Common-Logging、Log4j和JdkLog，你可以按需要选择相应的LogFilter，监控你应用的数据库访问情况。 

扩展JDBC，如果你要对JDBC层有编程的需求，可以通过Druid提供的Filter-Chain机制，很方便编写JDBC层的扩展插件。 



> 导入依赖

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.2.6</version>
</dependency>
```

<img src="https://i.loli.net/2021/06/02/BzxYkGTMCDsWuhL.png" alt="image-20210530102401545" style="zoom:67%;float:left" />



> 指定数据源

```yaml
type: com.alibaba.druid.pool.DruidDataSource
```

配置数据源

```yaml
#Spring Boot 默认是不注入这些属性值的，需要自己绑定
#druid 数据源专有配置
initialSize: 5
minIdle: 5
maxActive: 20
maxWait: 60000
timeBetweenEvictionRunsMillis: 60000
minEvictableIdleTimeMillis: 300000
validationQuery: SELECT 1 FROM DUAL
testWhileIdle: true
testOnBorrow: false
testOnReturn: false
poolPreparedStatements: true

#配置监控统计拦截的filters，stat:监控统计、log4j：日志记录、wall：防御sql注入
#如果允许时报错  java.lang.ClassNotFoundException: org.apache.log4j.Priority
#则导入 log4j 依赖即可，Maven 地址：https://mvnrepository.com/artifact/log4j/log4j
filters: stat,wall,log4j
maxPoolPreparedStatementPerConnectionSize: 20
useGlobalDataSourceStat: true
connectionProperties: druid.stat.mergeSql=true;druid.stat.slowSqlMillis=500

```

导入log4j依赖。

绑定SpringBoot：

```java
    @ConfigurationProperties(prefix = "spring.datasource")
    @Bean
    public DataSource druidDataSource(){
        return new DruidDataSource();
    }
```

编写druid配置文件：

因为SpringBoot内置了servlet容器，所以没有web.xml，所以使用web.xml的方式就是使用替代类。ServletRegistrationBean。

```java
//后台监控：相当于web.xml  
@Bean
public ServletRegistrationBean statViewServlet(){
    ServletRegistrationBean<StatViewServlet> bean = new ServletRegistrationBean<>(new StatViewServlet(), "/druid/*");
    //后台需要，有人登陆，账号密码配置
    HashMap<String, String> initParameters = new HashMap<>();
    //增加配置
    initParameters.put("loginUsername","root");//loginUsername固定
    initParameters.put("loginPassword","123456");
    //允许谁访问
    initParameters.put("allow","");
    //禁止谁能访问initParameters.put("用户名","IP地址")

    bean.setInitParameters(initParameters);
    return bean;
}
```

<img src="https://i.loli.net/2021/06/02/oPZ2fyeaQ8vwBpM.png" alt="image-20210530105151772" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/06/02/PTm8CkBwprW2uyK.png" alt="image-20210530105220487" style="zoom:67%;float:left" />



执行一条sql

<img src="https://i.loli.net/2021/06/02/RuFQPeM2JywLqUp.png" alt="image-20210530105445771" style="zoom:67%;float:left" />



```java
//过滤
@Bean
public FilterRegistrationBean webStartFilter(){
    FilterRegistrationBean<Filter> bean = new FilterRegistrationBean<>();
    //设置阿里巴巴过滤器
    bean.setFilter(new WebStatFilter());
    //过滤那些请求
    HashMap<String, String> initParameters = new HashMap<>();
    initParameters.put("exclusions","*.js,*css,*img,/druid/*");//这些东西不进行统计

    bean.setInitParameters(initParameters);
    return bean;
}
```



## Mybatis

整合包：mybatis-spring-boot-start

```java
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>2.1.3</version>
</dependency>
```



新建项目：

<img src="https://i.loli.net/2021/06/02/AUtpLcHErd1eNYM.png" alt="image-20210530111032199" style="zoom:67%;float:left" />



```yaml
spring:
datasource:
username: root
password: 123456
url: jdbc:mysql://localhost:3306/mybatis?useSSL=false&useUnicode=true&characterEncoding=utf8
driver-class-name: com.mysql.cj.jdbc.Driver
```



pojo层：

Mapper层：

```java
@Mapper//表示这是一个Mybatis接口
@Repository
public interface UserMapper {

    List<User> queryUserList();
    User queryUserById(int id);
    int addUser(User user);
    int updateUser(User user);
    int deleteUserById(int id);

}
```

Mapper.xml：

<img src="https://i.loli.net/2021/06/02/buGfw5T2AFMLnWg.png" alt="image-20210530113151426" style="zoom:67%;float:left" />

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.mf.mapper.UserMapper">
    <select id="queryUserList" resultType="user">
        select * from tb_user;
    </select>
    <select id="queryUserById" resultType="user">
        select * from tb_user where id=#{id};
    </select>
    <insert id="addUser" parameterType="user">
        insert into tb_user(id, username, pwd) values (#{id},#{username},#{pwd});
    </insert>
    <update id="updateUser" parameterType="user">
        update tb_user set username=#{username},pwd=#{pwd} where id=#{id};
    </update>
    <delete id="deleteUserById" parameterType="int">
        delete from tb_user where id=#{id};
    </delete>
</mapper>
```



controller层：SpringBoot自动提交事务

<img src="https://i.loli.net/2021/06/02/rlG4xDLyWBd9Set.png" alt="image-20210530115310718" style="zoom:67%;float:left" />



M：数据好业务 V：交接 C：HTML

将员工系统前端与现在的Mybatis后端数据交接起来就okk了。



# SpringSecurity

## 概述

Spring Security 是 Spring 家族中的一个安全管理框架，实际上，在 Spring Boot 出现之前，Spring Security 就已经发展了多年了，但是使用的并不多，安全管理这个领域，一直是 Shiro 的天下。

相对于 Shiro，在 SSM/SSH 中整合 Spring Security 都是比较麻烦的操作，所以，Spring Security 虽然功能比 Shiro 强大，但是使用反而没有 Shiro 多（Shiro 虽然功能没有 Spring Security 多，但是对于大部分项目而言，Shiro 也够用了）。

自从有了 Spring Boot 之后，Spring Boot 对于 Spring Security 提供了 自动化配置方案，可以零配置使用 Spring Security。

因此，一般来说，常见的安全管理技术栈的组合是这样的：

- SSM + Shiro
- Spring Boot/Spring Cloud + Spring Security

**注意，这只是一个推荐的组合而已，如果单纯从技术上来说，无论怎么组合，都是可以运行的。**





web开发中，安全最重要，属于非功能性需求。漏洞：隐私泄露~，架构一旦确定就难以改变所以设计之初就需要设计好。

安全框架：两个很像

- shiro:
- springsecurity:

认证，等级授权，功能权限，访问权限，菜单权限，，，拦截器，过滤器需要大量原生代码。



## 准备

> 导入依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```



关闭thymeleaf缓存：

```yaml
spring:
  thymeleaf:
    cache: false
```



导入静态资源：

<img src="https://i.loli.net/2021/06/02/hiuo1YyIKlVF6sQ.png" alt="image-20210530124500877" style="zoom:67%;float:left" />



测试controller：

```java
@Controller
public class RouterController {
    @RequestMapping({"/","/index","/index.html"})
    public String index(){
        return "index";
    }

    @RequestMapping("/login")
    public String login(){
        return "views/login";
    }

    @RequestMapping("/level1/{id}")
    public String level1(@PathVariable("id")int id){
        return "views/level1/"+id;
    }
    @RequestMapping("/level2/{id}")
    public String level2(@PathVariable("id")int id){
        return "views/level2/"+id;
    }
    @RequestMapping("/level3/{id}")
    public String level3(@PathVariable("id")int id){
        return "views/level3/"+id;
    }
}
```



<img src="https://i.loli.net/2021/06/02/POl8BnV3SitQuma.png" alt="image-20210530124943541" style="zoom:67%;float:left" />

<img src="https://i.loli.net/2021/06/02/yQsSDnigIq9CVoE.png" alt="image-20210530125005901" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/06/02/V7pn86Wse3RIxiC.png" alt="image-20210530125032379" style="zoom:67%;float:left" />



AOP，横切，配置类。



## 认证和授权

springsecurity是针对Spring项目的安全框架，也是SpringBoot底层安全模块默认的技术选型，他可以实现强大的web安全机制，对于安全机制，我们仅需要引入spring-boot-security模块，进行少量的配置，即可实现强大的安全管理。

记住及各类：

- websecurityConfigurerAdapter:自定义security策略；
- authernticationManagerBuilder:自定义认证策略；
- @EnableWebSecurity:开启WebSecurity模式。

spring Security的两个主要目标是认证和授权（访问控制）。

认证（Authentication）

授权（Authorization）

> 编写安全配置类

链式编程

```java
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        //首页所有人可以访问.,但是对应功能需要权限
        http.authorizeRequests()
            .antMatchers("/").permitAll()
            .antMatchers("/level1/**").hasRole("vip1")
            .antMatchers("/level2/**").hasRole("vip2")
            .antMatchers("/level3/**").hasRole("vip3");

        //没有权限默认会到登录页
        //防止网站攻击  get   csrf跨站请求攻击
        http.csrf().disable();
        http.formLogin();
    }
}
```

<img src="https://i.loli.net/2021/06/02/26esk3uYRtAvoWj.png" alt="image-20210530161225257" style="zoom: 67%;float:left" />



```java
    //认证  springboot2.1.x可以直接使用
    //密码编码：PasswordEncoder
    //在spring security5.0+新增加密很多加密方式
    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
           //这些数据正常应该从内存中读取
            //从内存中验证
        	auth.inMemoryAuthentication().passwordEncoder(new BCryptPasswordEncoder())
                .withUser("mafu").password(new BCryptPasswordEncoder().encode("123")).roles("vip1","vip2")
                .and()
                .withUser("root").password(new BCryptPasswordEncoder().encode("333")).roles("vip1","vip2","vip3");
    }
```



<img src="https://i.loli.net/2021/06/01/AzJLjTM2d9QSbki.png" alt="image-20210530162605235" style="zoom:67%;float:left" />



## 注销和控制

<img src="https://i.loli.net/2021/06/01/ZF5rxsVg4pMkdDI.png" alt="image-20210530164301498" style="zoom:67%;float:left" />

```html
<!--注销-->
<a class="item" th:href="@{/logout}">
    <i class="sign-out icon"></i> 注销
</a>
```

<img src="https://i.loli.net/2021/06/01/fPYE1SnKc4xValD.png" alt="image-20210530165120664" style="zoom:67%;float:left" />

```java
        //没有权限默认会到登录页
        http.formLogin();
        //开启了注销功能,跳到首页
        http.logout().logoutSuccessUrl("/");
```



> 权限控制

不是该用户的权限界面元素不应该出现。

导入security-thymeleaf整合包

```xml
<dependency>
    <groupId>org.thymeleaf.extras</groupId>
    <artifactId>thymeleaf-extras-springsecurity4</artifactId>
    <version>3.0.2.RELEASE</version>
</dependency>
```

导入命名空间：

```html
xmlns:sec="http://www.thymeleaf.org/thymeleaf-extras-springsecurity4"
```



```html
<!--登录注销-->
<div class="right menu">
    <!--未登录-->
    <div sec:authorize="!isAuthenticated()">
        <a class="item" th:href="@{/login}">
            <i class="address card icon"></i> 登录
        </a>
    </div>
    <!--已登录：用户名，注销-->
    <div sec:authorize="isAuthenticated()">
        <a class="item">
            用户名：<span sec:authentication="name"></span>
        </a>
    </div>
    <div sec:authorize="isAuthenticated()">
        <a class="item" th:href="@{/logout}">
            <i class="sign-out icon"></i> 注销
        </a>
    </div>
</div>
```

springboot降低版本：2.0.7.RELEASE才支持整合。

<img src="https://i.loli.net/2021/06/01/KBxGwkUz3mhQPfq.png" alt="image-20210530173118649" style="zoom:67%;float:left" />



菜单根据用户权限显示：

```html
<div class="column" sec:authorize="hasRole('vip3')">
```



## 记住我

```java
//开启记住我功能
http.rememberMe();
```

<img src="https://i.loli.net/2021/06/01/EU2j4KL86BHqbRC.png" alt="image-20210530174554120" style="zoom:67%;float:left" />

cookie有效期到6.13号，默认2周。



## 首页定制

<img src="https://i.loli.net/2021/06/01/mwvFzdZRnyjrSOx.png" alt="image-20210530175827557" style="zoom:67%;float:left" />

```java
//没有权限默认会到登录页
http.formLogin().loginPage("/toLogin");
```

login表单提交走的是登录成功页面。

```html
 <form th:action="@{/toLogin}" method="post">
```



记住我：

```html
<div class="field">
    <input type="checkbox" name="remember"/>记住我&nbsp
</div>
```



```java
//开启记住我功能  cookie
http.rememberMe().rememberMeParameter("remember");
```



# Shiro

## 简介

Apache Shiro 是 Java 的一个安全框架。目前，使用 Apache Shiro 的人越来越多，因为它相当简单，对比 Spring Security，可能没有 Spring Security 做的功能强大，但是在实际工作时可能并不需要那么复杂的东西，所以使用小而简单的 Shiro 就足够了。对于它俩到底哪个好，这个不必纠结，能更简单的解决项目问题就好了。

Shiro 可以非常容易的开发出足够好的应用，其不仅可以用在 JavaSE 环境，也可以用在 JavaEE 环境。Shiro 可以帮助我们完成：认证、授权、加密、会话管理、与 Web 集成、缓存等。这不就是我们想要的嘛，而且 Shiro 的 API 也是非常简单；其基本功能点如下图所示：

<img src="https://i.loli.net/2021/06/01/9JRAXOEQTbBxuUV.png" alt="image-20210530183245483" style="zoom:67%;float:left" />

- **Authentication**：身份认证 / 登录，验证用户是不是拥有相应的身份；
- **Authorization**：授权，即权限验证，验证某个已认证的用户是否拥有某个权限；即判断用户是否能做事情，常见的如：验证某个用户是否拥有某个角色。或者细粒度的验证某个用户对某个资源是否具有某个权限；
- **Session** **Management**：会话管理，即用户登录后就是一次会话，在没有退出之前，它的所有信息都在会话中；会话可以是普通 JavaSE 环境的，也可以是如 Web 环境的；
- **Cryptography**：加密，保护数据的安全性，如密码加密存储到数据库，而不是明文存储；
- **Web Support**：Web 支持，可以非常容易的集成到 Web 环境；
- **Caching**：缓存，比如用户登录后，其用户信息、拥有的角色 / 权限不必每次去查，这样可以提高效率；
- **Concurrency**：shiro 支持多线程应用的并发验证，即如在一个线程中开启另一个线程，能把权限自动传播过去；
- **Testing**：提供测试支持；
- **Run As**：允许一个用户假装为另一个用户（如果他们允许）的身份进行访问；
- **Remember Me**：记住我，这个是非常常见的功能，即一次登录后，下次再来的话不用登录了。



**记住一点，Shiro 不会去维护用户、维护权限；这些需要我们自己去设计 / 提供；然后通过相应的接口注入给 Shiro 即可。**

接下来我们分别从外部和内部来看看 Shiro 的架构，对于一个好的框架，从外部来看应该具有非常简单易于使用的 API，且 API 契约明确；从内部来看的话，其应该有一个可扩展的架构，即非常容易插入用户自定义实现，因为任何框架都不能满足所有需求。

首先，我们从外部来看 Shiro 吧，即从应用程序角度的来观察如何使用 Shiro 完成工作。如下图：

<img src="https://i.loli.net/2021/06/01/RN5vgXMHeZhVaip.png" alt="image-20210530183436668" style="zoom:67%;float:left" />

可以看到：应用代码直接交互的对象是 Subject，也就是说 Shiro 的对外 API 核心就是 Subject；其每个 API 的含义：

**Subject**：主体，代表了当前 “用户”，这个用户不一定是一个具体的人，与当前应用交互的任何东西都是 Subject，如网络爬虫，机器人等；即一个抽象概念；所有 Subject 都绑定到 SecurityManager，与 Subject 的所有交互都会委托给 SecurityManager；可以把 Subject 认为是一个门面；SecurityManager 才是实际的执行者；

**SecurityManager**：安全管理器；即所有与安全有关的操作都会与 SecurityManager 交互；且它管理着所有 Subject；可以看出它是 Shiro 的核心，它负责与后边介绍的其他组件进行交互，如果学习过 SpringMVC，你可以把它看成 DispatcherServlet 前端控制器；

**Realm**：域，Shiro 从从 Realm 获取安全数据（如用户、角色、权限），就是说 SecurityManager 要验证用户身份，那么它需要从 Realm 获取相应的用户进行比较以确定用户身份是否合法；也需要从 Realm 得到用户相应的角色 / 权限进行验证用户是否能进行操作；可以把 Realm 看成 DataSource，即安全数据源。

也就是说对于我们而言，最简单的一个 Shiro 应用：

1. 应用代码通过 Subject 来进行认证和授权，而 Subject 又委托给 SecurityManager；
2. 我们需要给 Shiro 的 SecurityManager 注入 Realm，从而让 SecurityManager 能得到合法的用户及其权限进行判断。

**从以上也可以看出，Shiro 不提供维护用户 / 权限，而是通过 Realm 让开发人员自己注入。**

接下来我们来从 Shiro 内部来看下 Shiro 的架构，如下图所示：

<img src="https://i.loli.net/2021/06/01/pkYoxg6ydf31Sn4.png" alt="image-20210530183536330" style="zoom:67%;float:left" />

- **Subject**：主体，可以看到主体可以是任何可以与应用交互的 “用户”；
- **SecurityManager**：相当于 SpringMVC 中的 DispatcherServlet 或者 Struts2 中的 FilterDispatcher；是 Shiro 的心脏；所有具体的交互都通过 SecurityManager 进行控制；它管理着所有 Subject、且负责进行认证和授权、及会话、缓存的管理。
- **Authenticator**：认证器，负责主体认证的，这是一个扩展点，如果用户觉得 Shiro 默认的不好，可以自定义实现；其需要认证策略（Authentication Strategy），即什么情况下算用户认证通过了；
- **Authrizer**：授权器，或者访问控制器，用来决定主体是否有权限进行相应的操作；即控制着用户能访问应用中的哪些功能；
- **Realm**：可以有 1 个或多个 Realm，可以认为是安全实体数据源，即用于获取安全实体的；可以是 JDBC 实现，也可以是 LDAP 实现，或者内存实现等等；由用户提供；注意：Shiro 不知道你的用户 / 权限存储在哪及以何种格式存储；所以我们一般在应用中都需要实现自己的 Realm；
- **SessionManager**：如果写过 Servlet 就应该知道 Session 的概念，Session 呢需要有人去管理它的生命周期，这个组件就是 SessionManager；而 Shiro 并不仅仅可以用在 Web 环境，也可以用在如普通的 JavaSE 环境、EJB 等环境；所以呢，Shiro 就抽象了一个自己的 Session 来管理主体与应用之间交互的数据；这样的话，比如我们在 Web 环境用，刚开始是一台 Web 服务器；接着又上了台 EJB 服务器；这时想把两台服务器的会话数据放到一个地方，这个时候就可以实现自己的分布式会话（如把数据放到 Memcached 服务器）；
- **SessionDAO**：DAO 大家都用过，数据访问对象，用于会话的 CRUD，比如我们想把 Session 保存到数据库，那么可以实现自己的 SessionDAO，通过如 JDBC 写到数据库；比如想把 Session 放到 Memcached 中，可以实现自己的 Memcached SessionDAO；另外 SessionDAO 中可以使用 Cache 进行缓存，以提高性能；
- **CacheManager**：缓存控制器，来管理如用户、角色、权限等的缓存的；因为这些数据基本上很少去改变，放到缓存中后可以提高访问的性能
- **Cryptography**：密码模块，Shiro 提供了一些常见的加密组件用于如密码加密 / 解密的。



## 入门

新建maven项目。

导入依赖：版本冲突很重要，这里因为冲突弄了好久。。。

```java
<dependencies>
    <dependency>
    <groupId>org.apache.shiro</groupId>
    <artifactId>shiro-core</artifactId>
    <version>1.4.1</version>
    </dependency>
    <dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>jcl-over-slf4j</artifactId>
    <version>1.7.21</version>
    </dependency>
    <dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-log4j12</artifactId>
    <version>1.7.21</version>
    </dependency>
    <dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.17</version>
    </dependency>
 </dependencies>
```

不能匹配：

```xml
<scope>test</scope>
```



log4j.properties

```properties
log4j.rootLogger=INFO, stdout

log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%d %p [%c] - %m %n

# General Apache libraries
log4j.logger.org.apache=WARN

# Spring
log4j.logger.org.springframework=WARN

# Default Shiro logging
log4j.logger.org.apache.shiro=INFO

# Disable verbose logging
log4j.logger.org.apache.shiro.util.ThreadContext=WARN
log4j.logger.org.apache.shiro.cache.ehcache.EhCache=WARN

```

shiro.ini

```ini
[users]
# user 'root' with password 'secret' and the 'admin' role
root = secret, admin
# user 'guest' with the password 'guest' and the 'guest' role
guest = guest, guest
# user 'presidentskroob' with password '12345' ("That's the same combination on
# my luggage!!!" ;)), and role 'president'
presidentskroob = 12345, president
# user 'darkhelmet' with password 'ludicrousspeed' and roles 'darklord' and 'schwartz'
darkhelmet = ludicrousspeed, darklord, schwartz
# user 'lonestarr' with password 'vespa' and roles 'goodguy' and 'schwartz'
lonestarr = vespa, goodguy, schwartz

[roles]
# 'admin' role has all permissions, indicated by the wildcard '*'
admin = *
# The 'schwartz' role can do anything (*) with any lightsaber:
schwartz = lightsaber:*
# The 'goodguy' role is allowed to 'drive' (action) the winnebago (type) with
# license plate 'eagle5' (instance specific id)
goodguy = winnebago:drive:eagle5
```

Quickstart.java测试



## Subject

小结：

<img src="https://i.loli.net/2021/06/01/pC9A1gxdlHi2PV7.png" alt="image-20210530212054478" style="zoom:67%;float:left" />

这些方法springsecurity都有。。

```java
public class Quickstart {

    private static final transient Logger log = LoggerFactory.getLogger(Quickstart.class);


    public static void main(String[] args) {
        Factory<SecurityManager> factory = new IniSecurityManagerFactory("classpath:shiro.ini");
        SecurityManager securityManager = factory.getInstance();
        SecurityUtils.setSecurityManager(securityManager);


        Subject currentUser = SecurityUtils.getSubject();//获取用户Subject
        Session session = currentUser.getSession();//通过当前用户拿到Session
        session.setAttribute("someKey", "aValue");
        String value = (String) session.getAttribute("someKey");
        if (value.equals("aValue")) {
            log.info("Subject=》 session[" + value + "]");
        }

        if (!currentUser.isAuthenticated()) {//测试当前用户是否被认证
            //Token:令牌
            UsernamePasswordToken token = new UsernamePasswordToken("lonestarr", "vespa");
            token.setRememberMe(true);//设置记住我
            try {
                currentUser.login(token);//执行了登录操作~
            } catch (UnknownAccountException uae) {//账户不对
                log.info("There is no user with username of " + token.getPrincipal());
            } catch (IncorrectCredentialsException ice) {//密码不对
                log.info("Password for account " + token.getPrincipal() + " was incorrect!");
            } catch (LockedAccountException lae) {//锁住
                log.info("The account for username " + token.getPrincipal() + " is locked.  " +
                        "Please contact your administrator to unlock it.");
            }
            catch (AuthenticationException ae) {
            }
        }

        log.info("User [" + currentUser.getPrincipal() + "] logged in successfully.");

        //角色
        if (currentUser.hasRole("schwartz")) {
            log.info("May the Schwartz be with you!");
        } else {
            log.info("Hello, mere mortal.");
        }

        //简单权限
        if (currentUser.isPermitted("lightsaber:wield")) {
            log.info("You may use a lightsaber ring.  Use it wisely.");
        } else {
            log.info("Sorry, lightsaber rings are for schwartz masters only.");
        }

        //更有力量的权限
        if (currentUser.isPermitted("winnebago:drive:eagle5")) {
            log.info("You are permitted to 'drive' the winnebago with license plate (id) 'eagle5'.  " +
                    "Here are the keys - have fun!");
        } else {
            log.info("Sorry, you aren't allowed to drive the 'eagle5' winnebago!");
        }

        //注销
        currentUser.logout();

        System.exit(0);
    }
}

```



## 集成SpringBoot

### 概述

新建spring项目导入thymeleaf依赖。

shiro三大对象：

- Subject    用户
- SecurityManager  管理所有用户
- Realm  连接数据

导入整合包：

```xml
<dependency>
    <groupId>org.apache.shiro</groupId>
    <artifactId>shiro-spring-boot-web-starter</artifactId>
    <version>1.7.1</version>
</dependency>
```



编写配置类：

ShiroConfig：

```java
@Configuration
public class ShiroConfig {

    //3.ShiroFilterFactory
    @Bean
    public ShiroFilterFactoryBean getShiroFilterFactoryBean(@Qualifier("getDefaultWebSecurityManager") DefaultWebSecurityManager defaultWebSecurityManager){
        ShiroFilterFactoryBean shiroFilterFactoryBean = new ShiroFilterFactoryBean();
        shiroFilterFactoryBean.setSecurityManager(defaultWebSecurityManager);//设置安全管理器
        return shiroFilterFactoryBean;
    }
    //2.DefaultWebSecurityManger
    //@Qualifier指定方法名与下面注入到bean中的方法绑定起来
    @Bean
    public DefaultWebSecurityManager getDefaultWebSecurityManager(@Qualifier("userRealm")UserRealm userRealm){
        DefaultWebSecurityManager securityManager = new DefaultWebSecurityManager();
        //关联userRealm
        securityManager.setRealm(userRealm);

        return securityManager;
    }
    //1.创建realm对象
    @Bean(name = "userRealm")
    public UserRealm userRealm(){
        return new UserRealm();
    }

}
```

UserRealm：

```java
//自定义的Realm对象
public class UserRealm extends AuthorizingRealm {
    @Override//授权
    protected AuthorizationInfo doGetAuthorizationInfo(PrincipalCollection principalCollection) {
        System.out.println("执行==》授权PrincipalCollection");
        return null;
    }

    @Override//认证
    protected AuthenticationInfo doGetAuthenticationInfo(AuthenticationToken authenticationToken) throws AuthenticationException {
        System.out.println("执行==》认证AuthenticationToken");
        return null;
    }
}
```



测试页面：

<img src="https://i.loli.net/2021/06/01/L4i9cp1Z6dbQDsh.png" alt="image-20210531084345660" style="zoom:67%;float:left" />

```html
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>增加</title>
</head>
<body>
<h2>增加</h2>
<hr>
<a th:href="@{/user/add}">add</a>&nbsp;&nbsp;<a th:href="@{/user/update}">update</a>
</body>
</html>
```

编写controller跳转：

```java
@RequestMapping("user/add")
public String toAdd(){
    return "user/add";
}
@RequestMapping("user/update")
public String toUpdate(){
    return "user/update";
}
```

问题：

<img src="https://i.loli.net/2021/06/01/4VpFbXQGo1ETNay.png" alt="image-20210531092041722" style="zoom:67%;float:left" />

<img src="https://i.loli.net/2021/06/01/nuob4pZcfyx1QMr.png" alt="image-20210531093331200" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/06/01/Nc4YwmJZICF2Apa.png" alt="image-20210531100029062" style="zoom:67%;float:left" />



### 登录拦截

```java
        /*
        添加shiro的内置过滤器:
        anon:无需认证就可以访问
        authc:必须认证才能访问
        user：必须拥有 记住我 功能才能用
        perms：拥有对某个资源的权限才能访问
        role：拥有某个角色权限才能访问
        * */
        Map<String, String> filterMap=new LinkedHashMap<>();
//        filterMap.put("/user/add","authc");
//        filterMap.put("/user/update","authc");
        filterMap.put("/user/*","authc");
        shiroFilterFactoryBean.setFilterChainDefinitionMap(filterMap);
        shiroFilterFactoryBean.setLoginUrl("/toLogin");//设置登录请求，没登录跳到登录页面
```

<img src="https://i.loli.net/2021/06/01/Gj3mZipF7xJSunO.png" alt="image-20210531102431607" style="zoom:67%;float:left" />



### 用户认证

UserRealm：

```java
public class UserRealm extends AuthorizingRealm {
    @Override//授权
    protected AuthorizationInfo doGetAuthorizationInfo(PrincipalCollection principalCollection) {
        System.out.println("执行==》授权PrincipalCollection");
        return null;
    }

    @Override//认证
    protected AuthenticationInfo doGetAuthenticationInfo(AuthenticationToken authenticationToken) throws AuthenticationException {
        System.out.println("执行==》认证AuthenticationToken");
        //用户名 ，密码~  数据读取
        String  name="admin";
        String password="123";
        UsernamePasswordToken userToken = (UsernamePasswordToken) authenticationToken;
        if(!userToken.getUsername().equals(name)){
            return null;//抛出异常 UnknownAccountException
        }
        //密码认证交给shiro做
        return new SimpleAuthenticationInfo("",password,"");
    }
}
```



controller:

```java
@RequestMapping("/login")
public String login(String username,String password,Model model){
    //1.获取当前的用户
    Subject subject = SecurityUtils.getSubject();
    //2.封装用户的登录数据
    UsernamePasswordToken passwordToken = new UsernamePasswordToken(username,password);
    //3.执行登录
    try {
        subject.login(passwordToken);
        return "index";
    } catch (UnknownAccountException uae) {//账户不对
        model.addAttribute("msg","用户不存在");
        return "login";
    } catch (IncorrectCredentialsException ice) {//密码不对
        model.addAttribute("msg","密码有误");
        return "login";
    }


}
```



## 整合Mybatis

导入依赖：

```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>5.1.49</version>
</dependency>
<dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.17</version>
</dependency>
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.2.6</version>
</dependency>
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>2.1.3</version>
</dependency>
```



application.yml

```yaml
spring:
      datasource:
      username: root
      password: 123456
      url: jdbc:mysql://localhost:3306/mybatis?useSSL=false&useUnicode=true&characterEncoding=utf8
      driver-class-name: com.mysql.cj.jdbc.Driver
#Spring Boot 默认是不注入这些属性值的，需要自己绑定
#druid 数据源专有配置
initialSize: 5
minIdle: 5
maxActive: 20
maxWait: 60000
timeBetweenEvictionRunsMillis: 60000
minEvictableIdleTimeMillis: 300000
validationQuery: SELECT 1 FROM DUAL
testWhileIdle: true
testOnBorrow: false
testOnReturn: false
poolPreparedStatements: true

#配置监控统计拦截的filters，stat:监控统计、log4j：日志记录、wall：防御sql注入
#如果允许时报错  java.lang.ClassNotFoundException: org.apache.log4j.Priority
#则导入 log4j 依赖即可，Maven 地址：https://mvnrepository.com/artifact/log4j/log4j
filters: stat,wall,log4j
maxPoolPreparedStatementPerConnectionSize: 20
useGlobalDataSourceStat: true
connectionProperties: druid.stat.mergeSql=true;druid.stat.slowSqlMillis=500
```

```yaml
mybatis:
      type-aliases-package: com.mf.pojo
      mapper-locations: classpath:mapper/*.xml
```



编写pojo，mapper，service层和测试。。。。

```java
@Override//认证
protected AuthenticationInfo doGetAuthenticationInfo(AuthenticationToken authenticationToken) throws AuthenticationException {
    System.out.println("执行==》认证AuthenticationToken");
    //用户名 ，密码~  数据读取
    UsernamePasswordToken userToken = (UsernamePasswordToken) authenticationToken;
    User user = userService.queryUserByName(userToken.getUsername());
    if (user==null) return null;//抛出异常
    //密码认证交给shiro做
    return new SimpleAuthenticationInfo("",user.getPwd(),"");
}
```



## 授权

```java
//授权
filterMap.put("/user/add","perms[user:add]");
```

<img src="D:\Typora\md\picture\SpringBoot\image-20210531150954243.png" alt="image-20210531150954243" style="zoom:67%;float:left" />

设置未授权页面

```java
@RequestMapping("/noAuth")
@ResponseBody
public String unauthorized(){
     return "未经授权无法访问";
}
```

ShiroConfig：

```java
//设置未授权页面
shiroFilterFactoryBean.setUnauthorizedUrl("/noAuth");
```



授予用户权限：

每个人进来每点击一次add都会被授权。

```java
@Override//授权
protected AuthorizationInfo doGetAuthorizationInfo(PrincipalCollection principalCollection) {
    System.out.println("执行==》授权PrincipalCollection");
    SimpleAuthorizationInfo info = new SimpleAuthorizationInfo();
    info.addStringPermission("user:add");
    return info;
}
```



用户权限保存在数据库中，增加user表的字段perms

<img src="https://i.loli.net/2021/06/01/ylo9O4CdsKR5Lkg.png" alt="image-20210531152655865" style="zoom:67%;float:left" />

<img src="https://i.loli.net/2021/06/01/YCVHxm2GNa5q4fJ.png" alt="image-20210531154119202" style="zoom:67%;float:left" />



## 权限菜单

导入shiro和thymeleaf整合包。

```xml
<dependency>
    <groupId>com.github.theborakompanioni</groupId>
    <artifactId>thymeleaf-extras-shiro</artifactId>
    <version>2.0.0</version>
</dependency>
```



```java
//整合 ShiroDialect :整合Shiro thymeleaf
@Bean
public ShiroDialect getShiroDialect(){
    return new ShiroDialect();
}
```

UserRealm:认证方法中

```java
Subject subject = SecurityUtils.getSubject();
subject.getSession().setAttribute("USER_SESSION",user);
```



```html
<div th:if="${session.USER_SESSION==null}">
    <a th:href="@{/toLogin}">登录</a>
</div>
```



```html
<div shiro:hasPermission="user:add">
    <a th:href="@{/user/add}">add</a>&nbsp;
</div>
<div shiro:hasPermission="user:update">
    &nbsp;<a th:href="@{/user/update}">update</a>
</div>
```



---

> 分析开源项目

---



# Swagger

前后端分离：主流  Vue+SpringBoot

后端时代：前端只用管理静态页面，html=》后端，模板引擎jsp，后端作为主力。

<img src="https://i.loli.net/2021/06/01/jzNWu3MGYIL6dk5.png" alt="image-20210531183053289" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/06/01/wbxpzAKBPDokEmQ.png" alt="image-20210531183339935" style="zoom:67%;float:left" />



- Swagger号称世界上最流行的API框架；
- RestFul API文档在线自动生成工具=》API文档与API定义同步更新；
- 直接运行，可以在线测试API接口，支持多种语言。



## 概述

Swagger 是一个规范且完整的框架，用于生成、描述、调用和可视化 RESTful 风格的 Web 服务。

Swagger 的目标是对 REST API 定义一个标准且和语言无关的接口，可以让人和计算机拥有无须访问源码、文档或网络流量监测就可以发现和理解服务的能力。当通过 Swagger 进行正确定义，用户可以理解远程服务并使用最少实现逻辑与远程服务进行交互。与为底层编程所实现的接口类似，Swagger 消除了调用服务时可能会有的猜测。

> Swagger 的优势

- 支持 API 自动生成同步的在线文档：使用 Swagger 后可以直接通过代码生成文档，不再需要自己手动编写接口文档了，对程序员来说非常方便，可以节约写文档的时间去学习新技术。
- 提供 Web 页面在线测试 API：光有文档还不够，Swagger 生成的文档还支持在线测试。参数和格式都定好了，直接在界面上输入参数对应的值即可在线测试接口。



## 入门

在项目中使用Swagger需要使用Springfox：

- swagger2
- ui



> SpringBoot继承Swagger

导入依赖

```xml
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>2.9.2</version>
</dependency>
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>2.9.2</version>
</dependency>
```

配置swagger

```java
@Configuration
@EnableSwagger2//开启swagger
public class SwaggerConfig {
}
```

测试运行

```tex
http://localhost:8080/swagger-ui.html
```

<img src="https://i.loli.net/2021/06/01/P9ZmFcY7rhI5XRM.png" alt="image-20210531185519537" style="zoom:67%;float:left" />



配置swagger信息：swagger的bean实例Docker。

```java
@Configuration
@EnableSwagger2//开启swagger
public class SwaggerConfig {
    @Bean//配置swagger的Docket的bean实例
    public Docket getDocket(){
        return new Docket(DocumentationType.SWAGGER_2)
                   .apiInfo(getApiInfo());
    }
    //配置swagger信息apiInfo
    private ApiInfo getApiInfo(){
        //作者信息
        Contact DEFAULT_CONTACT = new Contact("淮阴侯", "", "");
        return new ApiInfo("韩信的API文档",
                      "长枪一战",
                         "1.0",
                 "urn:tos",
                                 DEFAULT_CONTACT,
                          "Apache 2.0",
                        "http://www.apache.org/licenses/LICENSE-2.0",
                                  new ArrayList());
    }

}
```



## 扫描接口

Docket.select()

```java
@Bean//配置swagger的Docket的bean实例
public Docket getDocket(){
    return new Docket(DocumentationType.SWAGGER_2)
               .apiInfo(getApiInfo())
               .select()
               //配置要扫描接口的方式  RequestHandlerSelectors
               .apis(RequestHandlerSelectors.basePackage("com.mf.controller"))
               .paths(PathSelectors.ant("/mf/**"))   //过滤
               .build();
}
```

<img src="https://i.loli.net/2021/06/01/hHb9z16wEqgmJcL.png" alt="image-20210531192400583" style="zoom:80%;float:left" />



> 配置是否启动swagger

```java
.enable(false)
```



如何设置swagger在生产环境中使用在发布环境中不使用。

- 判断是否为生产环境  flag=false
- 注入enable(flag)

```java
Profiles profiles=Profiles.of("dev");//设置要显示的swagger环境
//获取项目的环境，通过environment.acceptsProfiles监听环境是否处在自己设定的环境当中
boolean b = environment.acceptsProfiles(profiles);
```



## 分组及注释

```java
.groupName("韩信")
```

<img src="https://i.loli.net/2021/06/01/L8YtR5FqV4bDiyp.png" alt="image-20210531203337083" style="zoom:67%;float:left" />

如何配置多个组？

多个Docket。

<img src="https://i.loli.net/2021/06/01/KEj2e1fIvwhqaLC.png" alt="image-20210531203755850" style="zoom:67%;float:left" />





> 实体类配置

实体类上也可以用@Api注释

```java
@ApiModel("用户实体类")
public class User {
    @ApiModelProperty("用户名")
    public String username;
    @ApiModelProperty("密码")
    public String password;
}
```

```java
//@ApiOperation()用在接口的注释
@RestController
public class TestController {
    @GetMapping("/test")
    public String test1(){
        return "SpringBoot-Swagger";
    }
    //只要我们的接口返回值中存在实体类，就会被扫描
    @PostMapping("/user")
    public User test2(){
        return new User();
    }
}
```

<img src="https://i.loli.net/2021/06/01/1MkXtR2EleALcri.png" alt="image-20210531205457490" style="zoom:67%;float:left" />

```java
    @ApiOperation("hello控制类")
    @GetMapping("/hello")
    public String hello(@ApiParam("用户名") String username){
        return "hello"+username;
    }
```



测试。。。

<img src="https://i.loli.net/2021/06/01/HcAuVwjZiKJ9aIR.png" alt="image-20210531210822676" style="zoom:67%;float:left" />

# 任务

## 异步任务

异步任务~先返回信息

定时任务~

邮件任务~时间



```java
@Service
public class AsynchronousService {
    @Async    //告诉spring，这是一个异步方法
    public void delay() throws InterruptedException {
        Thread.sleep(2000);
        System.out.println("数据正在处理....");
    }
}
```

```java
@EnableAsync//开启异步注解功能
@RestController
public class AsynchronousController {
    @Autowired
    AsynchronousService asynchronousService;
    @GetMapping("/delay")
    public String delay() throws InterruptedException {
        asynchronousService.delay();
        return "延迟了两秒";
    }
}
```



网站请求会转圈~~~~

解决。

## 邮件发送

导入依赖

```xml
<dependency>
    <!-- javax.mail：配置 -->
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-mail</artifactId>
</dependency>
```

```yaml
spring:
  mail:
    username: 3460942872@qq.com
    password: vljwlulxbhnhcidh
    host: smtp.qq.com
    #qq的话要开启加密验证
    properties:
      mail:
        smtp:
          ssl:
            enable: true
```

> 简单邮件

```java
@Autowired
JavaMailSenderImpl mailSender;

@Test
void contextLoads() {
    //一个简单的邮件
    SimpleMailMessage message = new SimpleMailMessage();
    //邮件的标题
    message.setSubject("欢迎注册！");
    message.setText("祝您消费愉快！");
    message.setTo("1106486773@qq.com");
    message.setFrom("3460942872@qq.com");
    mailSender.send(message);
}
```

> 复杂邮件

```java
@Test
void contextLoads02() throws MessagingException {
    //一个复杂的邮件
    MimeMessage mimeMessage = mailSender.createMimeMessage();
    //组装复杂邮件
    MimeMessageHelper helper = new MimeMessageHelper(mimeMessage,true);
    helper.setSubject("复杂的邮件");
    helper.setText("<h2 style='color:green'>消费愉快</h2>",true);
    //附件
    helper.addAttachment("1.jpg",new File("C:\\Users\\Administrator\\Pictures\\壁纸\\315653.jpg"));
    helper.addAttachment("2.jpg",new File("C:\\Users\\Administrator\\Pictures\\壁纸\\314101.jpg"));
    helper.setTo("1106486773@qq.com");
    helper.setFrom("3460942872@qq.com");
    mailSender.send(mimeMessage);
}
```



<img src="https://i.loli.net/2021/06/01/2CF1aUZwb9mMI4S.png" alt="image-20210531230619227" style="zoom:67%;float:left" />



## 定时任务

```java
TaskExecutor  任务执行者
TaskScheduler  任务调度程序
@EnableScheduling//开启定时功能注解
@Schedulde  //什么时候执行 
cron表达式
```

```java
@EnableAsync
@EnableScheduling//开启定时功能注解
@SpringBootApplication
public class Springboot09TaskApplication {

    public static void main(String[] args) {
        SpringApplication.run(Springboot09TaskApplication.class, args);
    }

}
```



```java
@Service
public class ScheduledService {
    //cron表达式
    //秒，分，时，日，月，周几
    @Scheduled(cron = "0 * * * * 0-7")//周一到周天的每天的0秒执行
    public void schedule(){
        System.out.println("在特定时间被执行了");
    }
}
```

<img src="https://i.loli.net/2021/06/01/KsomPHJzFYic94B.png" alt="image-20210531233650751" style="zoom:67%;float:left" />



# Redis



<img src="https://i.loli.net/2021/06/01/TUxO4A8j6m3dCu2.png" alt="image-20210601082255163" style="zoom:67%;float:left" />

---

先导课：

<img src="https://i.loli.net/2021/06/01/sFPtlTNVQSW9p61.png" alt="image-20210601083039056" style="zoom:67%;float:left" />



---



## 概述

Redis 是一个开源（BSD许可）的，内存中的数据结构存储系统，它可以用作数据库、缓存和消息中间件。 它支持多种类型的数据结构，如 [字符串（strings）](http://www.redis.cn/topics/data-types-intro.html#strings)， [散列（hashes）](http://www.redis.cn/topics/data-types-intro.html#hashes)， [列表（lists）](http://www.redis.cn/topics/data-types-intro.html#lists)， [集合（sets）](http://www.redis.cn/topics/data-types-intro.html#sets)， [有序集合（sorted sets）](http://www.redis.cn/topics/data-types-intro.html#sorted-sets) 与范围查询， [bitmaps](http://www.redis.cn/topics/data-types-intro.html#bitmaps)， [hyperloglogs](http://www.redis.cn/topics/data-types-intro.html#hyperloglogs) 和 [地理空间（geospatial）](http://www.redis.cn/commands/geoadd.html) 索引半径查询。 Redis 内置了 [复制（replication）](http://www.redis.cn/topics/replication.html)，[LUA脚本（Lua scripting）](http://www.redis.cn/commands/eval.html)， [LRU驱动事件（LRU eviction）](http://www.redis.cn/topics/lru-cache.html)，[事务（transactions）](http://www.redis.cn/topics/transactions.html) 和不同级别的 [磁盘持久化（persistence）](http://www.redis.cn/topics/persistence.html)， 并通过 [Redis哨兵（Sentinel）](http://www.redis.cn/topics/sentinel.html)和自动 [分区（Cluster）](http://www.redis.cn/topics/cluster-tutorial.html)提供高可用性（high availability）。





简单来说 redis 就是一个数据库，不过与传统数据库不同的是 redis 的数据是存在内存中的，所以读写速度非常快，因此 redis 被广泛应用于缓存方向。另外，redis 也经常用来做分布式锁。redis 提供了多种数据类型来支持不同的业务场景。除此之外，redis 支持事务 、持久化、LUA脚本、LRU驱动事件、多种集群方案。



## 整合测试

<img src="https://i.loli.net/2021/06/01/6hj5IFSEBskLAiG.png" alt="image-20210601083645415" style="zoom:50%;float:left" />



说明：在SpringBoot2.x之后，原来使用的jedis被替换成了lettuce？

jedis：采用直连，多线程操作不安全（连接池解决）BIO阻塞。

lettuce：采用netty，实例可以在多个线程共享，不存在线程不安全，NIO模式，



> 源码分析



```java
@Configuration(proxyBeanMethods = false)
@ConditionalOnClass(RedisOperations.class)
@EnableConfigurationProperties(RedisProperties.class)
@Import({ LettuceConnectionConfiguration.class, JedisConnectionConfiguration.class })
public class RedisAutoConfiguration {

   @Bean
   @ConditionalOnMissingBean(name = "redisTemplate")
   public RedisTemplate<Object, Object> redisTemplate(RedisConnectionFactory redisConnectionFactory)
         throws UnknownHostException {
       //默认的RedisTemplate没有过多的设置，Redis对象都是序列化的！
       //<Object, Object>后面使用的需要强制转换
      RedisTemplate<Object, Object> template = new RedisTemplate<>();
      template.setConnectionFactory(redisConnectionFactory);
      return template;
   }

   @Bean
   @ConditionalOnMissingBean
   public StringRedisTemplate stringRedisTemplate(RedisConnectionFactory redisConnectionFactory)
         throws UnknownHostException {
      StringRedisTemplate template = new StringRedisTemplate();
      template.setConnectionFactory(redisConnectionFactory);
      return template;
   }

}
```

配置：

```yaml
spring:
  redis:
    host: 127.0.0.1
    port: 
    ......
```



测试：

```java
@Autowired
private RedisTemplate redisTemplate;

@Test
void contextLoads() {
    //opsForValue()操作字符串
    //opsForXxx  操作不同数据类型
    //除了基本的操作，我们常用的方法都可以直接操作，比如CRUD
    redisTemplate.opsForValue().set("myKey","Study Redis");
    System.out.println(redisTemplate.opsForValue().get("myKey"));
    //RedisConnection connection = redisTemplate.getConnectionFactory().getConnection();
    //connection.flushDb();
    //connection.flushAll();

}
```

实际开放中会编写RedisUItils工具类操操作。

RedisUtil

```java
package com.mf.utils;

import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.stereotype.Component;
import org.springframework.util.CollectionUtils;

import javax.annotation.Resource;
import java.util.Collection;
import java.util.List;
import java.util.Map;
import java.util.Set;
import java.util.concurrent.TimeUnit;

@Component
public final class RedisUtil {

    @Resource
    private RedisTemplate<String, Object> redisTemplate;

    // =============================common============================

    /**
     * 指定缓存失效时间
     *
     * @param key  键
     * @param time 时间(秒)
     */
    public boolean expire(String key, long time, TimeUnit timeUnit) {
        try {
            if (time > 0) {
                redisTemplate.expire(key, time, timeUnit);
            }
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }

    /**
     * 根据key 获取过期时间
     *
     * @param key 键 不能为null
     * @return 时间(秒) 返回0代表为永久有效
     */
    public long getExpire(String key) {
        return redisTemplate.getExpire(key, TimeUnit.SECONDS);
    }


    /**
     * 判断key是否存在
     *
     * @param key 键
     * @return true 存在 false不存在
     */
    public boolean hasKey(String key) {
        try {
            return redisTemplate.hasKey(key);
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 删除缓存
     *
     * @param key 可以传一个值 或多个
     */
    @SuppressWarnings("unchecked")
    public void del(String... key) {
        if (key != null && key.length > 0) {
            if (key.length == 1) {
                redisTemplate.delete(key[0]);
            } else {
                redisTemplate.delete((Collection<String>) CollectionUtils.arrayToList(key));
            }
        }
    }


    // ============================String=============================

    /**
     * 普通缓存获取
     *
     * @param key 键
     * @return 值
     */
    public Object get(String key) {
        return key == null ? null : redisTemplate.opsForValue().get(key);
    }

    /**
     * 普通缓存放入
     *
     * @param key   键
     * @param value 值
     * @return true成功 false失败
     */

    public boolean set(String key, Object value) {
        try {
            redisTemplate.opsForValue().set(key, value);
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 普通缓存放入并设置时间
     *
     * @param key   键
     * @param value 值
     * @param time  时间(秒) time要大于0 如果time小于等于0 将设置无限期
     * @return true成功 false 失败
     */

    public boolean set(String key, Object value, long time) {
        try {
            if (time > 0) {
                redisTemplate.opsForValue().set(key, value, time, TimeUnit.SECONDS);
            } else {
                set(key, value);
            }
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 递增
     *
     * @param key   键
     * @param delta 要增加几(大于0)
     */
    public long incr(String key, long delta) {
        if (delta < 0) {
            throw new RuntimeException("递增因子必须大于0");
        }
        return redisTemplate.opsForValue().increment(key, delta);
    }


    /**
     * 递减
     *
     * @param key   键
     * @param delta 要减少几(小于0)
     */
    public long decr(String key, long delta) {
        if (delta < 0) {
            throw new RuntimeException("递减因子必须大于0");
        }
        return redisTemplate.opsForValue().increment(key, -delta);
    }


    // ================================Map=================================

    /**
     * HashGet
     *
     * @param key  键 不能为null
     * @param item 项 不能为null
     */
    public Object hget(String key, String item) {
        return redisTemplate.opsForHash().get(key, item);
    }

    /**
     * 获取hashKey对应的所有键值
     *
     * @param key 键
     * @return 对应的多个键值
     */
    public Map<Object, Object> hmget(String key) {
        return redisTemplate.opsForHash().entries(key);
    }

    /**
     * HashSet
     *
     * @param key 键
     * @param map 对应多个键值
     */
    public boolean hmset(String key, Map<String, Object> map) {
        try {
            redisTemplate.opsForHash().putAll(key, map);
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * HashSet 并设置时间
     *
     * @param key  键
     * @param map  对应多个键值
     * @param time 时间(秒)
     * @return true成功 false失败
     */
    public boolean hmset(String key, Map<String, Object> map, long time, TimeUnit timeUnit) {
        try {
            redisTemplate.opsForHash().putAll(key, map);
            if (time > 0) {
                expire(key, time, timeUnit);
            }
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 向一张hash表中放入数据,如果不存在将创建
     *
     * @param key   键
     * @param item  项
     * @param value 值
     * @return true 成功 false失败
     */
    public boolean hset(String key, String item, Object value) {
        try {
            redisTemplate.opsForHash().put(key, item, value);
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }

    /**
     * 向一张hash表中放入数据,如果不存在将创建
     *
     * @param key   键
     * @param item  项
     * @param value 值
     * @param time  时间(秒) 注意:如果已存在的hash表有时间,这里将会替换原有的时间
     * @return true 成功 false失败
     */
    public boolean hset(String key, String item, Object value, long time, TimeUnit timeUnit) {
        try {
            redisTemplate.opsForHash().put(key, item, value);
            if (time > 0) {
                expire(key, time, timeUnit);
            }
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 删除hash表中的值
     *
     * @param key  键 不能为null
     * @param item 项 可以使多个 不能为null
     */
    public void hdel(String key, Object... item) {
        redisTemplate.opsForHash().delete(key, item);
    }


    /**
     * 判断hash表中是否有该项的值
     *
     * @param key  键 不能为null
     * @param item 项 不能为null
     * @return true 存在 false不存在
     */
    public boolean hHasKey(String key, String item) {
        return redisTemplate.opsForHash().hasKey(key, item);
    }


    /**
     * hash递增 如果不存在,就会创建一个 并把新增后的值返回
     *
     * @param key  键
     * @param item 项
     * @param by   要增加几(大于0)
     */
    public double hincr(String key, String item, double by) {
        return redisTemplate.opsForHash().increment(key, item, by);
    }


    /**
     * hash递减
     *
     * @param key  键
     * @param item 项
     * @param by   要减少记(小于0)
     */
    public double hdecr(String key, String item, double by) {
        return redisTemplate.opsForHash().increment(key, item, -by);
    }


    // ============================set=============================

    /**
     * 根据key获取Set中的所有值
     *
     * @param key 键
     */
    public Set<Object> sGet(String key) {
        try {
            return redisTemplate.opsForSet().members(key);
        } catch (Exception e) {
            e.printStackTrace();
            return null;
        }
    }


    /**
     * 根据value从一个set中查询,是否存在
     *
     * @param key   键
     * @param value 值
     * @return true 存在 false不存在
     */
    public boolean sHasKey(String key, Object value) {
        try {
            return redisTemplate.opsForSet().isMember(key, value);
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 将数据放入set缓存
     *
     * @param key    键
     * @param values 值 可以是多个
     * @return 成功个数
     */
    public long sSet(String key, Object... values) {
        try {
            return redisTemplate.opsForSet().add(key, values);
        } catch (Exception e) {
            e.printStackTrace();
            return 0;
        }
    }


    /**
     * 将set数据放入缓存
     *
     * @param key    键
     * @param time   时间(秒)
     * @param values 值 可以是多个
     * @return 成功个数
     */
    public long sSetAndTime(String key, long time, TimeUnit timeUnit, Object... values) {
        try {
            Long count = redisTemplate.opsForSet().add(key, values);
            if (time > 0) {
                expire(key, time, timeUnit);
            }
            return count;
        } catch (Exception e) {
            e.printStackTrace();
            return 0;
        }
    }


    /**
     * 获取set缓存的长度
     *
     * @param key 键
     */
    public long sGetSetSize(String key) {
        try {
            return redisTemplate.opsForSet().size(key);
        } catch (Exception e) {
            e.printStackTrace();
            return 0;
        }
    }


    /**
     * 移除值为value的
     *
     * @param key    键
     * @param values 值 可以是多个
     * @return 移除的个数
     */

    public long setRemove(String key, Object... values) {
        try {
            Long count = redisTemplate.opsForSet().remove(key, values);
            return count;
        } catch (Exception e) {
            e.printStackTrace();
            return 0;
        }
    }

    // ===============================list=================================

    /**
     * 获取list缓存的内容
     *
     * @param key   键
     * @param start 开始
     * @param end   结束 0 到 -1代表所有值
     */
    public List<Object> lGet(String key, long start, long end) {
        try {
            return redisTemplate.opsForList().range(key, start, end);
        } catch (Exception e) {
            e.printStackTrace();
            return null;
        }
    }


    /**
     * 获取list缓存的长度
     *
     * @param key 键
     */
    public long lGetListSize(String key) {
        try {
            return redisTemplate.opsForList().size(key);
        } catch (Exception e) {
            e.printStackTrace();
            return 0;
        }
    }


    /**
     * 通过索引 获取list中的值
     *
     * @param key   键
     * @param index 索引 index>=0时， 0 表头，1 第二个元素，依次类推；index<0时，-1，表尾，-2倒数第二个元素，依次类推
     */
    public Object lGetIndex(String key, long index) {
        try {
            return redisTemplate.opsForList().index(key, index);
        } catch (Exception e) {
            e.printStackTrace();
            return null;
        }
    }


    /**
     * 将list放入缓存
     *
     * @param key   键
     * @param value 值
     */
    public boolean lSet(String key, Object value) {
        try {
            redisTemplate.opsForList().rightPush(key, value);
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 将list放入缓存
     *
     * @param key   键
     * @param value 值
     * @param time  时间(秒)
     */
    public boolean lSet(String key, Object value, long time,TimeUnit timeUnit) {
        try {
            redisTemplate.opsForList().rightPush(key, value);
            if (time > 0) {
                expire(key, time,timeUnit);
            }
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }

    }


    /**
     * 将list放入缓存
     *
     * @param key   键
     * @param value 值
     * @return
     */
    public boolean lSet(String key, List<Object> value) {
        try {
            redisTemplate.opsForList().rightPushAll(key, value);
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }

    }


    /**
     * 将list放入缓存
     *
     * @param key   键
     * @param value 值
     * @param time  时间(秒)
     * @return
     */
    public boolean lSet(String key, List<Object> value, long time,TimeUnit timeUnit) {
        try {
            redisTemplate.opsForList().rightPushAll(key, value);
            if (time > 0) {
                expire(key, time,timeUnit);
            }
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 根据索引修改list中的某条数据
     *
     * @param key   键
     * @param index 索引
     * @param value 值
     * @return
     */

    public boolean lUpdateIndex(String key, long index, Object value) {
        try {
            redisTemplate.opsForList().set(key, index, value);
            return true;
        } catch (Exception e) {
            e.printStackTrace();
            return false;
        }
    }


    /**
     * 移除N个值为value
     *
     * @param key   键
     * @param count 移除多少个
     * @param value 值
     * @return 移除的个数
     */

    public long lRemove(String key, long count, Object value) {
        try {
            Long remove = redisTemplate.opsForList().remove(key, count, value);
            return remove;
        } catch (Exception e) {
            e.printStackTrace();
            return 0;
        }

    }

    // ===============================HyperLogLog=================================

    public long pfadd(String key, String value) {
        return redisTemplate.opsForHyperLogLog().add(key, value);
    }

    public long pfcount(String key) {
        return redisTemplate.opsForHyperLogLog().size(key);
    }

    public void pfremove(String key) {
        redisTemplate.opsForHyperLogLog().delete(key);
    }

    public void pfmerge(String key1, String key2) {
        redisTemplate.opsForHyperLogLog().union(key1, key2);
    }


}
```





## Template

```java
@Component
@Data
@AllArgsConstructor
@NoArgsConstructor
public class User implements Serializable{//企业开发中所有的实体类都会序列化

    private String name;
    private String pwd;

}
```



```java
@Test
void test01() throws JsonProcessingException {
    //真实开发一般使用json传递对象
    User user = new User("韩信", "999");
    String json = new ObjectMapper().writeValueAsString(user);
    redisTemplate.opsForValue().set("user",json);
}
```

固定模板：

```java
@Configuration
public class RedisConfig {

    //编写自己的RedisTemplate
    @Bean
    public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory factory)
            throws UnknownHostException {
        //为了开发方便一般直接使用<String, Object>
        RedisTemplate<String , Object> template = new RedisTemplate<>();
        template.setConnectionFactory(factory);
        //序列化配置
        Jackson2JsonRedisSerializer jackson2JsonRedisSerializer = new Jackson2JsonRedisSerializer(Object.class);
        ObjectMapper mapper = new ObjectMapper();
        mapper.setVisibility(PropertyAccessor.ALL, JsonAutoDetect.Visibility.PUBLIC_ONLY);
        mapper.enableDefaultTyping(ObjectMapper.DefaultTyping.NON_FINAL);
        jackson2JsonRedisSerializer.setObjectMapper(mapper);
        StringRedisSerializer stringRedisSerializer = new StringRedisSerializer();

        //配置具体的序列化方式
        template.setKeySerializer(stringRedisSerializer);
        template.setHashKeySerializer(stringRedisSerializer);
        template.setValueSerializer(jackson2JsonRedisSerializer);
        template.setHashValueSerializer(jackson2JsonRedisSerializer);
        template.afterPropertiesSet();
        return template;
    }

}
```





所有的Redis操作对开发人员来说十分简单，重要的是理解Redis的思想和每一种数据结构的作用场景。



# 分布式

<img src="https://i.loli.net/2021/06/01/xteTmdgFBfLYIka.png" alt="image-20210601094539753" style="zoom:67%;float:left" />

随着互联网的发展，网站的应用规模不断扩大，常规的垂直应用框架已经无法应对，分布式框架和流动式计算框架势在必行。

----

> 分布式框架介绍



<img src="https://i.loli.net/2021/06/01/ovhiOJGL3dDS2gw.png" alt="image-20210601095252041" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/06/01/ehCn5SoPQMTHs29.png" alt="image-20210601095625932" style="zoom:80%;float:left" />

适用小型网站，小型管理系统，将所有功能都部署到一个功能里，简单易用。

缺点：

1. 性能拓展困难；
2. 协同开发问题；
3. 不利于升级维护。



<img src="https://i.loli.net/2021/06/01/aj5wSpcxuG9POfV.png" alt="image-20210601095838946" style="zoom:80%;float:left" />



通过切分业务来实现各个模块独立部署，降低了维护和部署的难度，团队各司其职更加容易管理，性能拓展也更加方便，更加有针对性。

缺点：公用模块无法重复利用，开发性浪费。



<img src="https://i.loli.net/2021/06/01/aOpXtKuseIG2MEA.png" alt="image-20210601100119929" style="zoom:80%;float；left" />



<img src="https://i.loli.net/2021/06/01/EwrX3ZVUA8qj27f.png" alt="image-20210601100209162" style="zoom:80%;float:left" />



> RPC介绍

<img src="https://i.loli.net/2021/06/01/y71eBHXTx4WQhRL.png" alt="image-20210601100511092" style="zoom:80%;float:left" />





<img src="https://i.loli.net/2021/06/01/y3p8b72wCjtTMSA.png" alt="image-20210601100600217" style="zoom:67%;float:left" />



在微服务的设计中，一个服务A如果访问另一个Module下的服务B，可以采用HTTP REST传输数据，并在两个服务之间进行序列化和反序列化操作，服务B把执行结果返回过来。

<img src="https://i.loli.net/2021/06/01/syJ7tVhE1X64Y9Z.png" alt="image-20210601100952076" style="zoom:67%;float:left" />

由于HTTP在应用层中完成，整个通信的代价较高，远程过程调用中直接基于TCP进行远程调用，数据传输在传输层TCP层完成，更适合对效率要求比较高的场景，RPC主要依赖于客户端和服务端之间建立Socket链接进行，底层实现比REST更复杂。



RPC的两个核心：通讯，序列化。

序列化就是为了方便数据传输。



<img src="https://i.loli.net/2021/06/01/SyNXb9K2Y5jreok.png" alt="image-20210601101617774" style="zoom:67%;float:left" />



# Dubbo

## 概述

是一款高性能，轻量级额开源Java RPC框架，提供三大核心能力：

1. 面向接口的远程方法调用；
2. 智能容错和负载均衡；
3. 服务自动注册和发现。



Dubbo 采用全 Spring 配置方式，透明化接入应用，对应用没有任何 API 侵入，只需用 Spring 加载 Dubbo 的配置即可，Dubbo 基于 [Spring 的 Schema 扩展](https://docs.spring.io/spring/docs/4.2.x/spring-framework-reference/html/xsd-configuration.html) 进行加载。

如果不想使用 Spring 配置，可以通过 [API 的方式](https://dubbo.apache.org/zh/docs/v2.7/user/configuration/api) 进行调用。



<img src="https://i.loli.net/2021/06/01/qLdTs1ceCz5hwPj.png" alt="image-20210601102401385" style="zoom: 80%;float:left" />



<img src="https://i.loli.net/2021/06/01/aKVkZ1BW3cdbQSt.png" alt="image-20210601102641460" style="zoom:67%;float:left" />



## Zookeeper安装

ZooKeeper是一个[分布式](https://baike.baidu.com/item/分布式/19276232)的，开放源码的[分布式应用程序](https://baike.baidu.com/item/分布式应用程序/9854429)协调服务，是[Google](https://baike.baidu.com/item/Google)的Chubby一个[开源](https://baike.baidu.com/item/开源/246339)的实现，是Hadoop和[Hbase](https://baike.baidu.com/item/Hbase/7670213)的重要组件。它是一个为分布式应用提供一致性服务的软件，提供的功能包括：配置维护、域名服务、分布式同步、组服务等。

ZooKeeper的目标就是封装好复杂易出错的关键服务，将简单易用的接口和性能高效、功能稳定的系统提供给用户。

ZooKeeper包含一个简单的原语集，提供Java和C的接口。

ZooKeeper代码版本中，提供了分布式独享锁、选举、队列的接口，代码在$zookeeper_home\src\recipes。其中分布锁和队列有[Java](https://baike.baidu.com/item/Java/85979)和C两个版本，选举只有Java版本



安装：

3.6以上版本有问题。

<img src="https://i.loli.net/2021/06/01/v3twGCeBuWOzsQL.png" alt="image-20210601105803327" style="zoom: 67%;float:left" />



安装教程：

[(26条消息) windows环境下安装zookeeper教程详解（单机版）_风轩雨墨的博客-CSDN博客](https://blog.csdn.net/qq_33316784/article/details/88563482)



连接客户端：

<img src="https://i.loli.net/2021/06/01/aFzXTZJePpECSrd.png" alt="image-20210601112400183" style="zoom:67%;float:left" />

通过Zookeeper存值取值。



## Dubbo安装

dubbo本身并不是一个服务软件，他其实就是一个jar包，能够帮助你的java程序连接到Zookeepr，并利用zookeeper的消费，提供业务。

但是为了用户更好的管理监控众多的dubbo服务，官方提供一个可视化的监控程序dubbo-admin。

<img src="https://i.loli.net/2021/06/01/Ax6EhZLn1YtMB4Q.png" alt="image-20210601152410398" style="zoom:67%;float:left" />



注册中心的地址：

dubbo.registry.address=zookeeper://127.0.0.1:21



使用IDEA打开，注意使用JDK1.8。

<img src="https://i.loli.net/2021/06/01/rsUVq9S4d2WZaJC.png" alt="image-20210601155421807" style="zoom:67%;float:left" />

<img src="https://i.loli.net/2021/06/01/kOAegRzMnsTQGKj.png" alt="image-20210601155342122" style="zoom:67%;float:left" />





## 服务器注册开发实战

整合SpringBoot。

<img src="https://i.loli.net/2021/06/01/qLdTs1ceCz5hwPj.png" alt="image-20210601102401385" style="zoom: 80%;float:left" />

创建生产者服务项目

创建消费服务项目

<img src="https://i.loli.net/2021/06/01/r16zUNeDg9WLd57.png" alt="image-20210601162944545" style="zoom:67%;float:left" />



生产者导入Dubbo和Zookeeper依赖。

日志可能会冲突和SpringBoot。

```xml
    <dependencies>
        <!--springBoot动态的引入springMVC全部的配置 -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.apache.dubbo</groupId>
            <artifactId>dubbo-spring-boot-starter</artifactId>
            <version>2.7.7</version>
            <exclusions>
                <exclusion>
                    <groupId>org.slf4j</groupId>
                    <artifactId>slf4j-log4j12</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-framework</artifactId>
            <version>4.3.0</version>
        </dependency>
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-recipes</artifactId>
            <version>2.8.0</version>
        </dependency>

    </dependencies>
```



配置

```properties
server.port=8081
#服务应用名字
dubbo.application.name=provider-server
#注册中心地址
dubbo.registry.address=zookeeper://127.0.0.1:2181
#那些服务要被注册
dubbo.scan.basePackages=com.mf.service
```





```java
//zookeeper：服务注册与发现
@DubboService
public class GetTicketServiceImpl implements GetTicketService{

    @Override
    public String buy() {
        return "恭喜买到了票";
    }
}
```

```java
@EnableDubboConfig
@SpringBootApplication
public class ProviderServerApplication {

    public static void main(String[] args) {
        SpringApplication.run(ProviderServerApplication.class, args);
    }

}
```



启动zookeeper和provider-server。

打开dubbo-admin管理页面。

问题：provider-server启动不了。

防坑[(26条消息) SpringBoot整合Dubbo+ZK注册失败的坑_a15119273009的博客-CSDN博客](https://blog.csdn.net/a15119273009/article/details/107396865)



<img src="https://i.loli.net/2021/06/01/DLG6YSZ3c4m21uh.png" alt="image-20210601172009954" style="zoom:67%;float:left" />





启动consumer-server

```properties
server.port=8082
#消费者从那个地方拿，需要暴露自己的名字
dubbo.application.name=consumer-server
#注册中心的地址
dubbo.registry.address=zookeeper://127.0.0.1:2181
```



GetTicketService



import org.apache.dubbo.config.annotation.Reference;

```java
import org.apache.dubbo.config.annotation.Reference;
import org.springframework.stereotype.Service;

@Service
public class UserService {
    //想拿到provider-server提供的服务，要去注册中心拿
    @Reference
    GetTicketService getTicketService;
    public void buy(){
        getTicketService.buy();
        System.out.println("在注册中心拿到票");
    }

}
```



测试：

```java
@SpringBootTest
class ConsumerServerApplicationTests {

    @Autowired
    UserService userService;

    @Test
    void contextLoads() {
        userService.buy();
    }

}
```



<img src="https://i.loli.net/2021/06/01/dpuXr24BnxNAezC.png" alt="image-20210601174242532" style="zoom:33%;float:left" />





小结：

<img src="https://i.loli.net/2021/06/01/U86I2PimADZ4pQq.png" alt="image-20210601174602753" style="zoom: 67%;float:left" />



# 小结

<img src="https://i.loli.net/2021/06/01/vPDBmCofkshnHQl.png" alt="image-20210601181642954" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/06/01/1EQehiYU3V8GN29.png" alt="image-20210601182346897" style="zoom:67%;float:left" />



<img src="https://i.loli.net/2021/06/01/qaLybMZ5wvVzjKH.png" alt="image-20210601182703567" style="zoom:67%;float:left" />















