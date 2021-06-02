[我的工作台 - Gitee.com](https://gitee.com/ma-fu/dashboard/projects)

# Java概述

> 应用场景

<img src="https://i.loli.net/2021/05/20/C1zyO7aRZX2qJdY.png" alt="1" style="zoom:50%;float:left" />

> 学习路线

1. **JavaSE(18-20天)**

      计算机基础

      博客的重要性

      Java基础语法

      流程控制和方法

      数组

      面向对象

      异常

      常用类

      集合框架

      IO

      多线程

      GUI(可选，纯桌面端像qq这样的应用，爬虫)

   ​    网络编程

   ​    注解和反射

   ​    JUC编程(高并发编程)

   ​    JVM探究

   ​    [拓展]23种设计模式

   ​    [拓展]XML

   ​    [拓展]数据结构和算法

   ​    [拓展]正则表达式

   

2. **数据库(4天)**

   ​    MySQL

   ​    JDBC

   ​    UML类图

   ​    数据库设计

   

3. **前端(7天)**

​            HTML

​            CSS

​             JS

​             jQuery

​             Layui/BootStrap

​             Vue



4. **JavaWeb(7天)**

​             Tomcat

​             Http

​             Maven

​              Servlet

​              Session,Cookie

​              JSP

​              三层架构

​              过滤器

​              监听器

​              文件上传

​              邮件收发

​              [拓展] 富本编辑器



学完上面四个阶段可基本搭建网站了，但是过程比较繁琐。

-------------------------------------------------------------------------------------------------------------------

5. **SSM框架(9天)**

​               Git

​               MyBatis

​               Spring

​               SpringMVC

学完SSM，常规企业开发没有问题。

-----------------------------------------------------------------------------------------------------------------

6. **Linux(7天)**

​              Linux基础

​              Redis

​              Nginx

​              Docker

Linux几乎将所有大型公司的服务器市场都占领了。

 以上6各阶段是作为JAVA程序员进入小公司的基本要求。

-------------------------------------------------------------------------------------------------------------------

以下是微服务学习阶段

7. **SpringBoot(8天)**

​               SpringBoot基础

​               SpringBoot配置及原理

​               SpringBoot持久层操作

​               SpringBoot Web开发

​               SpringBoot 缓存

​                SpringBoot 消息

​                SpringBoot 检索

​                 SpringBoot 任务

​                 SpringBoot 安全

​                 Dubbo+Zookeeper 分布式开发

​               

8. **SpringCloud(8天)**

​                  微服务即及微服务架构

​                   SpringCloud

​                   Eureka服务注册与发现

​                   Feign,Ribbon负载均衡

​                   Hystrix熔断机制

​                   Zuul路由网关

​                   SpringCloud Config配置中心



9. **Hadoop(8天)**

​                   大数据时代

​                    Hadoop简介

​                    Hadoop环境搭建

​                    HDFS

​                    MapReduce

​                    Yarn

​                    Hive

​                    Hbase

​                    

## 博客重要性

总结和思考，逻辑思维文笔组织能力。

wordpress

typecho



> Markdown基础语法

划线，斜体，加粗，分割线；

~~哈哈哈哈~~

*哈哈*

***哈哈哈***

---

## 计算机预科

> 计算机硬件，软件

一些物理装置按照系统结构的要求构成一个有机整体为计算机软件运行提供物质基础。

冯诺依曼体系结构

<img src="https://i.loli.net/2021/05/20/Eu9wYglUK4RfXJ7.png" alt="QQ截图20210510195020" style="zoom:67%;float:left" />

> 快捷键

window+E 打开我的电脑；

> Dos命令

cmd 在资源路径地址栏

dir 查看目录文件

cd .. 上一级

cls 清理

exit 退出

cd /d 路径  跳到当前路径

md 创建文件夹

rd 删除目录

cd> 创建文件

del 删除文件



> 计算机发展史

二进制->汇编->高级语言->、、、

大体分为面向过程和对象：C是面向过程，C++和JAVA是面向对象。



> Java三大版本

write once ,run anywhere...JVM使其可移植跨平台

标准版、嵌入式开发、E企业级开发

JavaSE、~~JavaME~~、JavaEE



Java2标准版(J2SE):桌面，控制台开发

~~Java2移动版(J2ME):手机,小家电~~

Java2企业版(J2EE):服务器，web端



3高：高可用，高性能，高并发。



> Java特性和优势

简单性

面向对象

可移植性

高性能

分布式

动态性

多线程

安全性

健壮性



> JDK,JRE,JVM

JDK->JRE->JVM 由外到里具有包含关系

JDK:java develpoment kit

JRE:java run environment

JVM:java virtual machine



> Java运行机制

编译型，解释型

<img src="https://i.loli.net/2021/05/20/KmSFDgAi2OoyGPn.png" alt="QQ截图20210510203543" style="zoom:67%;float:left" />

# Java基础语法

## 数据类型

强类型语言(Java)：所有变量使用严格符合规定

弱类型语言(JavaScript)

> Java数据类型分为2大类

基本类型 （primitive type）

引用类型   (reference type)



8个基本类型：

**整数类型**

byte:1字节

short：2字节

int：4字节

long：8字节

**浮点类型**

float：4字节

double：8字节

**字符串类型**

char:2字节

**boolean类型**

boolean：1字节



long num4=30L;//long类型需要在后面加个L

float num5=50.1F;

String不是一个关键字是一个类。

## 数据类型拓展及面试题讲解

> 整数拓展

二进制0b

八进制0

十进制

十六进制0x

```java
           int i1=10;
           int i2=010;
           int i3=0x10;
           System.out.println(i1);
           System.out.println(i2);
           System.out.println(i3);
//输出
10
8
16
```

> 浮点数拓展

银行业务怎么表示？

用float和double是有问题的。。。

```java
          float f=0.1f;
          double d=1.0/10;
          System.out.println(f==d);
//
flase?
          float f1=233333322222f;
          float f2=f1+1;
          System.out.println(f1==f2);
//
true?
```

float  有限 离散 舍入误差



```java
           String s1=new String("hello world");
           String s2=new String("hello world");
           System.out.println(s1==s2);

           String s3="hello world";
           String s4="hello world";
           System.out.println(s3==s4);
//
false
true
```

String 对象，从内存分析



> StringBuffer和StringBuilder

StringBuffer：可变长，append()，多线程数据量较大，效率低安全；

StringBuilder：可变长，append()，单线程数据量较大，效率高不安全；





**最好不使用浮点数进行比较！！！**

推荐使用大数类型：BigDecimal  数学工具类

> 字符拓展

强制类型转换

```java
            char c1='a';
            char c2='中';
            System.out.println(c1);
            System.out.println(c2);
            System.out.println((int)c1);
            System.out.println((int)c2);


//
a
中
97
20013
```

所有字符本子还是数字

编码 Unicode  表： 2字节 0-66536  Excel表格最长2^16

U0000 UFFFF

```java
          char c='\u0061';
          System.out.println(c);
//
a
```

> 转义字符

\t  制表符4空格

\n 换行

## 类型装换

自动转换：低->高    

运算过程中不同类型运算先转同一类型然后进行运算

byte->short->int->long->float->double

强制转换：高->低

> 问题

不能对布尔值进行转哈

转换是可能存在内存溢出和精度损失

```java
         int a=10_0000_0000;
         System.out.println(a);
//JDk7新特性可以用下划线分割数字
```

操作比较大的数时候注意溢出问题

```java
         int a=10_0000_0000;
         int b=20;
         int total1=a*b;
         System.out.println(total1);
         long total2=a*b;//转换之前已经存在问题了？
         System.out.println(total2);
//
-1474836480
-1474836480
         long total3=a*((long)b);
         System.out.println(total3);
//
20000000000
```

## 变量

局部变量：必须声明和初始化

实例变量：从属对象，不进行初始化默认为0 null false

类变量：static  从属类，随着类一起存在或消失

常量：final 一般使用大写字符   MAX_VALUE

变量：驼峰命名规则

类型：首字母大写GoodMan或者驼峰原则

方法名：首字母小写和驼峰原则

## 运算符

短路运算

```java
        int c=5;
        boolean d=(c<4)&&(c++<4);
        System.out.println(c);
        System.out.println(d);
//
5
false
```

> 位运算

&    |    ^      ~   >>    <<

> 拼接前后问题

```java
        int a=10;
        int b=20;
        System.out.println(a+b+"");
        System.out.println(""+a+b);
//
30
1020
```

## 包机制

一般利用公司域名倒置作为包名 www.bai.com   com.baidu.www

通配符：com.baidu.*

## JavaDoc

javadoc命令是用来生成自己API文档的

@author作者名

@version版本号

@since指明需要最早使用的jdk版本

@param参数名

@return返回值情况

@throws异常抛出情况

/****回车生成注释



进入代码路径然后 cmd

javadoc -encoding UTF-8 -charset UTF-8 XXX.java

会生成一个index.html文档类开发文档。

# Java流程控制

```tex
scanner
hashNext()和hasNextLine()判断是否还有输入的数据
```

> 增强for循环

```java
for(声明语句：表达式){
    //
}
```

打印三角形：

<img src="https://i.loli.net/2021/05/20/BIJqyS1jAMzDkhC.png" alt="QQ截图20210511101308" style="zoom:67%;float:left" />

```java
        //打印三角形:分解为4部分
        for(int i=1;i<=5;i++){
            //打印左半三角形：
            //第1部分用空格填充
            for(int j=5;j>=i;j--){
                System.out.print(" ");
            }
            //第2部分用*填充
            for(int j=1;j<=i;j++){
                System.out.print("*");
            }
            //打印做右半三角形：
            for(int j=1;j<i;j++){
                System.out.print("*");
            }
            System.out.println();
        }
```

<img src="https://i.loli.net/2021/05/20/pWkAjtE2KJuCohH.png" alt="QQ截图20210511102211" style="zoom:50%;float:left" />



# Java方法

设计方法的原则：方法的本意是功能块，就是实现某个功能的语句的集合，我们设计方法的时候，最好保持方法的**原子性**：就是一个方法只完成1个功能，这样利于我们后期拓展。

> 方法的重载

重载就是在一个类中，有相同的函数名称，但形参不同的函数。

方法的重载规则：

方法名称必须相同；

参数列表必须不同(个数，类型，排列顺序);

**返回类型可同可不同，但仅仅返回类型不同不足以成为方法的重载**。



> 命令行传参

```java
package LeetCode;
public class Main {
    public static void main(String[] args) {
          //遍历参数
          for (int i = 0; i < args.length; i++) {
             System.out.println("args["+i+"]:"+args[i]);
          }           
    }

}
```

注意路径问题：

<img src="https://i.loli.net/2021/05/20/6fCx359VENcYSO2.png" alt="QQ截图20210511104710" style="zoom:67%;float:left" />

> 可变参数，不定向参数

参照命令行传参，解决重载出现过多方法问题。

1. JDK1.5开始，Java支持传递同类型的可变参数给一个方法；
2. 在声明方法中，在指定参数类型后加一个省略号(...)；
3. 一个方法中只能指定一个可变参数，它必须是方法的最后一个参数。

可变长参数本质就是一个数组：

```java
public class Main {
    public static void text(int... i){//表明有多个i
        for(int j=0;j<i.length;j++)
          System.out.println(i[j]);
    }
    public static void main(String[] args) {
          text(1,2,3,44,22);      
          System.out.println("===================");
          text(new int[]{1,2,3,44,22}); //可变参数本质还是一个数组 
    }

}
```

> 递归

```java
public class Main {
    public static int f(int n){
        if(n==1) return 1;
        return n*f(n-1);
    }
    public static void main(String[] args) {
         System.out.println(f(3));
    }

}
```

# 数组

> Java内存分析

<img src="https://i.loli.net/2021/05/20/jgenOubIQycvXNd.png" alt="QQ截图20210511110910" style="zoom:70%;float:left" />

<img src="https://i.loli.net/2021/05/20/XVLvRd8S7Hi9TpA.png" alt="QQ截图20210511111500" style="zoom:70%;float:left" />

静态初始化,创建+赋值;

动态初始化(包含默认初始化)；

```java
int[] a={0,1,2,3};
int[] b=new int[10];
```

**数组对象本身是保存在堆中**

Arrays.for



> Arrays工具类

查看JDK帮助文档

Arrays类中方法都是static静态方法，可以直接使用类型进行调用，不用使用对象调用。

通常具有以下常用功能：

```tex
fill赋值
sort排序
equals比较
binarySearch方法能对排序好的数组进行二分查找操作
```

```java
       int[] a={1,3,10,2,333,6};
       System.out.println(a);//[I@5d22bbb7
       //打印数组元素
       System.out.println(Arrays.toString(a));
       //数组排序
       Arrays.sort(a);
       System.out.println(Arrays.toString(a));
       //数组部分填充
       System.out.println(Arrays.toString(a));
        Arrays.fill(a, 1, 2, 300);//[1,2) 左闭右开
       System.out.println(Arrays.toString(a));
```

> 冒泡排序

```java
    public static void sort(int[] a){
        for(int i=0;i<a.length;i++){
            //内层循环，大数往上冒
            for(int j=0;j<a.length-1-i;j++){
                if(a[j+1]<a[j]){
                    int temp=a[j+1];
                    a[j+1]=a[j];
                    a[j]=temp;
                }
            }
        }
    }
```

O(n^2)

假设内部部分已经有序，如何优化？加个标记记录是否有交换若无提前结束for

```java
    public static void sort(int[] a){
        for(int i=0;i<a.length;i++){

            boolean isOrder=false;

            //内层循环，大数往上冒
            for(int j=0;j<a.length-1-i;j++){
                if(a[j+1]<a[j]){
                    int temp=a[j+1];
                    a[j+1]=a[j];
                    a[j]=temp;
                    isOrder=true;
                }
            }
            //如果这轮没有进行交换操作，表明全部已经有序
            if(!isOrder) break;
        }
    }
```



> 数组压缩-----稀疏数组

当一个数组中大部分元素为0，或者为同一值的时候，可以使用稀疏数组来保存该数组。

处理方式：

-  记录数组一共几行几列，有多少个不同值；
- 把具有不同值元素和行列及值记录在一个小规模的数组中从而压缩。

<img src="https://i.loli.net/2021/05/20/7UqdaxnLoAGj6XQ.png" alt="QQ截图20210511115458" style="zoom:50%;float:left" />

6行7列有效值为8个

```tex
创建一个二维数组
输出原始数组
转换为稀疏数组保存
获取有效值的个数
创建稀疏数组 int[][] a2=new int[sum+1][3]
遍历二维数组，将非零值存放入稀疏数组 a2[count++][0]=i...
输出稀疏数组 
读取稀疏数组 int[][] a3=new int[a2[0][0]][a[0][1]]
给其中元素还原
```

# 面向对象

核心思想就是OOP。

面向对象的本质：**以类的方式组织代码，以对象封装数据。**

3大特性：**继承、封装、多态。**

值传递和引用传递(对象)

> 构造方法

必须与类名相同，不能有返回值，也不能是void类型。

作用：1.使用neew关键本质是调用有构造器，2. 实例化初始值

注意：一旦定义有参构造就必须显示定义无参构造。

> 创建内存分析

<img src="https://i.loli.net/2021/05/20/6lbGKDqXIjyWnev.png" alt="QQ截图20210511144517" style="zoom:67%;float:left" />

> 封装

高内聚，低耦合；

封装(数据的隐藏)private->属性私有:get/set

作用：

1.提高程序的安全性，保护数据；

2.隐藏代码的实现细节；(数据验证)

3.统一接口；

4.系统可维护性。

> 继承

Java中类只有单继承没有多继承；

Object类；java中所有类都默认继承Object类

**super类；(与this对比)**

方法重写--->多态

Ctrl+h打开继承树

```java
public class Person {
    protected String name="mafu_person";
    public void print(){
        System.out.println("person!");
    }

}
```

```java
public class Student extends Person{
        private String name="mafu_student";
        public void test1(){
            System.out.println(name);
            System.out.println(this.name);
            System.out.println(super.name);
        }
        public void test2(){
            print();
            this.print();
            super.print();
        }
        public void print(){
            System.out.println("student!");
        }

}
```

```java
public class Application {
    public static void main(String[] args) {
        Student student = new Student();
        student.test1();
    }
}
```

隐藏代码：构造器执行。

Super注意点：

​      super调用必须在构造方法第一个

​      Super和this不能同时调用构造方法

Super VS this

  代表的对象不同：

​       this：不同调用者这个对象 

​       super:代表父类对象的引用

> 重写

静态text方法：方法的调用只和左边数据类型有关，不算重写



```java
A a=new A();
B b=new A();父类的引用指向了子类
a.text();//a
b.text();//b
```

非静态：**重写只和非静态方法有关，public**

方法的调用只和右边数据类型有关

对象执行那些方法之和左边有关

```java
//a
//a
```

静态方法和非静态方法区别很大。



重写：

修饰符：范围可以扩大但不能缩小：public->protected->Default->private;

抛出异常：范围，可以被缩小，，但不能被放大



> instanceof和类型转换

有关系的类型才能进行instanceof判断

x instanceof y 存在父子关系，才能编译通过。

强制转换,后调用子类方法；子类转父类可能丢失一些方法

```java
Person student=new Student();
((Student) student).go()
```

1.父类引用指向子类对象；

2.子类转换父类，向上转型；

3.父类向下转子类，强制转型；

4.方便方法调用，减少重复代码。



> static 详解

静态代码块，跟类加载只执行一次，赋初始值。

```java
static {
    
}
```



> 抽象类

abstract      extends     类单继承

```java
public abstract class Action{
    //抽象方法，只有方法名字，没有方法的实现
    public abstract void doSomething();
}
```

抽象类的所有方法，子类必须实现。

1.不能new这个抽象类，只能由子类去实现它。

2.抽象类中也可以写普通方法。



intereface    impelments   接口伪多继承

专业的抽象，约束和实现分离，面向接口编程。

接口本质是契约，面向对象的精髓。

接口中方法都是抽象的public abstract 不用写。



> 内部类

通过外部类来实例化内部类~

```java
Outer outer=new Outer();
Outer.Inner inner=new Outer.new Inner();
```

内部类可以访问外部类私有变量。



静态内部类



一个Java类中可以有多个Class(可以有main方法方便测试)，单是只能有一个public class



匿名实例类



> 异常erro和exception

异常3种类型：

检查性异常

运行时异常

错误error



Throwable异常体系结构：



快捷键：Ctrl+alt+t

异常处理机制：try catch finally throw throws

捕获异常

抛出异常

```java
try{//监控
    if(){
        // throws 用在更高级方法名中抛出
        throw new ArithmeticException()//主动抛出异常
    }
}catch(Error ){//捕获,想要捕获的异常类型
    
}catch(Exception e){//捕获多个异常
    //尽量去处理异常
    e.printStackTrace()//打印异常栈信息
}finally{//善后，可有可无
    //释放资源
}
```



> 自定义异常

继承Exception



