

# 初识MySql #

JavaEE:企业级Java开发 Web

前端  (页面：展示，数据！)

后台 (连接点：连接数据库JDBC，连接前端(控制，控制视图跳转和前端传递数据))

数据库（存数据 Txt,Excel,word,变量）

500万以下的数据都可以存，500万以上数据需要做下索引优化。

大型网站也可以用：因为MySql是可以**集群**的。



## 什么是数据库 ##

- 数据库DataBase    简称DB
- 关系型数据库SQL：MySql，Oracle，SQL Server，SQLite，DB2……
- 非关系型数据库NOSQL：Redis,MongoDB……

## 什么是DBMS ##

- 数据库管理系统 (DataBase Management System)

## MySql安装 ##

尽量不用.exe安装，注册表，卸载麻烦。

尽可能使用压缩包安装。

- zip压缩包

- 环境变量：PATH 添加bin文件夹

- 编辑my.ini文件

  ```java
  [mysqld]
  basedir=D:\Program Files\mysql-5.7\
  datadir=D:\Program Files\mysql-5.7\data\
  port=3306
  skip-grant-tables
  ```

- cmd 切换到mysql的bin目录  输入mysqld -install

- 输入 mysqld --initialize-insecure --user=mysql

- net start mysql 启动

- mysql -u root -p 进入mysql管理界面

- 更改root密码

  ```java
  update mysql.user set authentication_string=password('123456') where user='root' and Host = 'localhost';
  ```

- 刷新权限

  ```java
     flush privileges；
  ```

- 修改my,ini文件删除最后一句 skip-grant-tables

- 重启 

  ```java
  exit退出
  net stop mysql
  net start mysql
  ```

- 连接测试 mysql -uroot -pxxxxx

可视化工具**SQLyog**

## 几个基本的数据库操作命令 ##

```sql
update user set password=password('123456')where user='root';修改密码
flush priveleges;刷新数据库
show databases;显示所有数据库
use dbname;打开某个数据库
show tables;显示数据库中所有表
describe user;打印数据库表user表的列信息
create database name;创建数据库

exit;退出Mysql
? 寻求帮助
--注释
```



# 数据库操作 #

## 结构化查询语句分类 ##

- DDL 数据定义语言

  ```sql
  create drop alter
  ```

- DML 数据操作语言

  ```sql
  insert update delete
  ```

- DQL 数据查询语言

  ```sql
  select
  ```

- DCL  数据控制语言

  ```sql
  grant commit rollback
  ```

## 数据库操作 ##

```sql
create database [if not exists] 数据库名;
drop database [if not exists] 数据库名;
use 数据库名;

数值类型：
tinyint  --1字节
smallint --2字节
mediumint --3字节
int  --4字节 常用
bigint --8字节
float --4字节
double --8字节
decimal --金融银行领域常使用，，字符串形式的浮点数

字符串类型：
char   --固定0~255
varchar --可变0~65535 常用
tinytext 
text --文本串 2^16-1 保存大文本

日期时间类型：
date -- YYYY-MM-DD日期
time -- HH:mm:ss时间
datetime-- YYYY-MM-DD HH:mm:ss最常用的时间格式 常用
timestamp--时间戳全球统一 1979.1.1
year

数据字段属性：
Unsigned
zerofill
auto_increment
null --没有值，未知
not null
default

id 主键
`version` 乐观锁
is_delete 伪删除
```

## 练习 ##

### 建库，建表 ###

- 练习1

```sql
create database if not exists school;
use school;
create table if not exists student (
    id int not null auto_increment comment'学号',
    name varchar(30) not null default '匿名' comment '姓名',
    password varchar(20)  not null default '123456' comment'密码',
    sex varchar(2) not null default '男' comment'性别',
    birtyday date default null comment'生日',
    address varchar(100) default null comment'地址',
    email varchar(50) default null comment'邮箱',
    primary key(id)
)engine=InnoDB;
--查看定义
show create database school;
show create table student;
--查看结构
desc student;
-- 单行注释#
-- 多行注释/*  */
```

```sql
--  (标准SQL注释风格，要求双破折号后加一空格符（空格、TAB、换行等）)
模式通配符：
_ 任意单个字符
% 任意多个字符包括0个
单引号需要进行转义 \'
```

### 外键约束 ###

- 练习2

```sql
create database mybatis;
use mybatis;
drop table if exists tb_user;
create table tb_user(
   id int not null,
   username varchar(30) default null,
   pwd varchar(30) default null,
   primary key(id)
)engine=InnoDB;
insert into tb_user(id,username,pwd) values
(1,'狂神','11111'),
(2,'张三','22222'),
(3,'李四','33333');

create table tb_teacher(
    id int not null,
    username varchar(30) default null,
    primary key(id)
)engine=InnoDB;
insert into tb_teacher(id,username) values (1,'马老师');
create table tb_student(
     id int not null,
     username varchar(30) default null,
     tid int default null,
     primary key(id),
     key fktid (tid),
     constraint fktid foreign key(tid) references tb_teacher(id)
)engine=InnoDB;
insert into tb_student (id,username,tid) values ('1', '小明', '1');
insert into tb_student (id,username,tid) values ('2', '小鸿', '1');
insert into tb_student (id,username,tid) values ('3', '小环', '1');
insert into tb_student (id,username,tid) values ('4', '小路', '1');

create table tb_blog(
	   id varchar(50) not null comment '博客id',
       title varchar(100) not null comment '博客标题',
       author varchar(30) not null comment '博客作者',
       create_time datetime not null comment '创建时间',
       views int not null comment '浏览量'
)engine=InnoDB;


```

MySQL的数据表的类型：常见的 MyISAM 与 InnoDB 类型：

<img src="D:\Typora\md\picture\Mysql\image-20210517092715396.png" alt="image-20210517092715396" style="zoom:80%;float:left"/>





 <img src="D:\Typora\md\picture\Mysql\image-20210517092953358.png" alt="image-20210517092953358" style="zoom:80%;float:left" />





















 <img src="D:\Typora\md\picture\Mysql\image-20210517093206953.png" alt="image-20210517093206953" style="zoom:80%;float:left" />















不推荐在配置文件设置，防止到被电脑跑出现乱码。





### 修改表 ###

```sql
-- 修改表名字
alter table student rename as highStudent;
alter table highStudent rename as student;
-- 增加字段
alter table student add classroom int not null default 1 comment'教室';

-- 重命名用change 修改约束使用modify
-- 修改字段属性
alter table student modify classroom char(10) null comment'教室';
-- 修改字段名
alter table student change classroom class char(10) not null default '123' comment'教室';
-- 删除字段
alter table student drop class;
alter table student drop classroom;
```

 <img src="D:\Typora\md\picture\Mysql\image-20210517093831507.png" alt="image-20210517093831507" style="zoom:80%;float:left" />















# DML语言 #

## 外键 ##

### 作用 ###

一致性，完整性，约束。





### 创建外键 ###

创建表后添加外键

```sql
use school;
alter table student add gradeid int default null comment '年级';
alter table student add key FK_gradeid(gradeid);
alter table student rename as tb_student;
alter table grade rename as tb_grade;
alter table tb_student add constraint FK_gradeid foreign key (gradeid) references tb_grade (gradeid);
```



### 删除外键 ###

**删除外键注意**：删除具有主外键关系的表时，要先删子表，后删主表；

```sql
alter table tb_student drop foreign key FK_gradeid;
-- 执行上面sql语句后，为外键索引还在，因为index 外键这个索引是建立外键时候默认生成的
desc  tb_student;
alter table tb_student drop index FK_gradeid;
```





```sql
-- 表的名称和字段尽量用``圈起来;

CREATE TABLE IF NOT EXISTS `student`(
      `id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
      `name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
      `pwd` VARCHAR(20) NOT NULL DEFAULT '123456' COMMENT '密码',
      `sex` VARCHAR(2) NOT NULL DEFAULT '男' COMMENT '性别',
      `birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
      `address` VARCHAR(100) DEFAULT NULL COMMENT '家庭地址',
      `email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
      PRIMARY KEY(`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8;
SHOW CREATE DATABASE `school`;
SHOW CREATE TABLE `student`;

DROP TABLE IF EXISTS `grade`;
CREATE TABLE IF NOT EXISTS `grade`(
       `gradeid` INT(10) NOT NULL AUTO_INCREMENT COMMENT '年级id',
       `gradename` VARCHAR(50) NOT NULL COMMENT '年级名称',
        PRIMARY KEY (`gradeid`)
)ENGINE=INNODB DEFAULT CHARSET=utf8;

-- 创建表时没外键
ALTER TABLE `student`
ADD `gradeid` INT(10) NOT NULL COMMENT '学生的年级id';

ALTER TABLE `student`
ADD CONSTRAINT `FK_gradeid` FOREIGN KEY (`gradeid`) REFERENCES `grade`(`gradeid`);
```

阿里的java规范强制：不得使用外键与级联，一切外键概念都必须在应用层解决。

首先每次做delete或者update都必须考虑外键约束，导致开发时候痛苦，测试数据也非常不方便。



**以上的操作都是物理外键，数据库级别的挖减，我们不建议使用！(避免数据库过多造成困扰)**

最佳实践：

- 数据库就是单纯的表，只用来存数据，只有行(数据)和列(字段)
- 想使用多张表的数据，想使用外键(程序去实现)













## DML数据操作语言 ##

### 增删改 ###

insert into

update set

```sql
insert  添加数据语句
delete  删除数据语句
update  更新数据语句
```



### insert命令 ###

```sql
insert into 表名(字段1，字段，2，字段3，……) values (值1,'值2','值3')


insert into tb_grade(gradename) values ('大一');
-- 主键自增能省略
insert into tb_grade values ('大一');
--Error Code: 1136. Column count doesn't match value 
-- 其他部分可以省略但是，添加的值必须与表结构相一致

-- 一次插入多个数据

insert into tb_grade(gradename,teacher) values ('大一','马老师'),('大二','秦老师');
insert into tb_grade(gradename) values ('大三');
```

 <img src="D:\Typora\md\picture\Mysql\image-20210517153722026.png" alt="image-20210517153722026" style="zoom:80%;float:left" />











```sql
USE school;
SHOW TABLES;
DROP TABLE IF EXISTS student;
-- 表的名称和字段尽量用``圈起来;

CREATE TABLE IF NOT EXISTS `student`(
      `id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
      `name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
      `pwd` VARCHAR(20) NOT NULL DEFAULT '123456' COMMENT '密码',
      `sex` VARCHAR(2) NOT NULL DEFAULT '男' COMMENT '性别',
      `birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
      `address` VARCHAR(100) DEFAULT NULL COMMENT '家庭地址',
      `email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
      PRIMARY KEY(`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8;

SHOW CREATE DATABASE `school`;
SHOW CREATE TABLE `student`;

DROP TABLE IF EXISTS `grade`;
CREATE TABLE IF NOT EXISTS `grade`(
       `gradeid` INT(10) NOT NULL AUTO_INCREMENT COMMENT '年级id',
       `gradename` VARCHAR(50) NOT NULL COMMENT '年级名称',
        PRIMARY KEY (`gradeid`)
)ENGINE=INNODB DEFAULT CHARSET=utf8;

-- 创建表时没外键
ALTER TABLE `student`
ADD `gradeid` INT(10) DEFAULT 0  COMMENT '学生的年级id';

ALTER TABLE `student`
ADD CONSTRAINT `FK_gradeid` FOREIGN KEY (`gradeid`) REFERENCES `grade`(`gradeid`);

ALTER TABLE `student` DROP FOREIGN KEY `FK_gradeid`;-- 外键索引还在
DESCRIBE `student`;
ALTER TABLE `student` DROP INDEX `FK_gradeid`;

INSERT INTO `grade`(`gradename`) VALUES
('大一'),('大二'),('大三'),('大四');
INSERT INTO `student`(`name`) VALUES
('小楠'),('小化');
INSERT INTO `student`(`name`,`sex`)VALUES
('小红','女');

```





### update命令 ###

```sql
update 表名 set cloumn_name=value[,cloum_name=value2……] [where condition]

-- where 条件字句

```

 <img src="D:\Typora\md\picture\Mysql\image-20210517154756187.png" alt="image-20210517154756187" style="zoom:80%;" />

 <img src="D:\Typora\md\picture\Mysql\image-20210517155040689.png" alt="image-20210517155040689" style="zoom:80%;float:left" />















### delete命令 ###

#### delete和truncate的区别 ####

```sql
delete from 表名 [where condition]

-- tip：完全清空表数据，truncate功能更加强大速度更快
delete from tb_grade;
Error Code: 1175. You are using safe update mode and you tried to update a table without a WHERE that uses a KEY column.

truncate tb_grade;

-- 结论：
/*
delete 如果不指定where则删除所有数据，自增值在原来的基础上进行，会记录日志；
truncate 自增值会恢复到初始值不会记录日志；

同样使用delete清空不同引擎的数据库表数据，重启数据库服务后：
InnoDB：自增列从初始值开始(因为是存储在内存中，断电即失);
MyISAN:自增列依然从上一个自增数据基础开始(存在文件中，，不会丢失)
```

 <img src="D:\Typora\md\picture\Mysql\image-20210517155523361.png" alt="image-20210517155523361" style="zoom:80%;float:left" />











# DQL查询函数 #

## 简介 ##

- **Data QUery Language** 数据查询语言
- 简单的单表查询和多表的复杂查询和嵌套查询，select语句
- 数据库语言中最核心，最重要，使用频率最高的语句





## select语法 ##

```sql
-- []可选 {}必选
select [all|distinct]
{*|table.*|[table.filed1[as alias1]][,table.filed2[as alias2]]……}
from table_name [as table_alias]
  [left|right|inner join table_name2] -- 联合查询
  [where ……] -- 指定结果需要满足的条件
  [group by……] -- 指定结果按照那几字段来分组
  [having] -- 过滤分组的记录必须满足的次要条件
  [order by……] -- 指定查询记录按照一个或多个条件排序
  [limit {[offset,]row_count|row_countOFFSET offfset}] -- 指定查询的记录从那条道那条
```



### 指定查询 ###

```sql
-- 查询所有学生信息
select * from tb_test;
-- 查询指定列
select roll from tb_test;
```

### as取别名 ###

```sql
--- 为列取别名
select id as 编号,roll as 序号 from tb_test;
```

```sql
--- 给表取别名
select id as 编号,roll as 序号 from tb_test as s;
--- 给查询结果取别名
select concat('序号:',roll) as 新序号 from tb_test;-- concat()函数拼接字符串
```

```sql
SELECT CONCAT('名字：',`name`) AS '新名字' FROM `student` AS s;
```

 <img src="D:\Typora\md\picture\Mysql\image-20210517160222327.png" alt="image-20210517160222327" style="zoom:80%;float:left" />









### distinct去重 ###

作用：去掉select查询返回的记录结果中重复的记录，返回所有列的值都相同，只返回一条。

```sql
select distinct roll from tb_test;
```





### 表达式 ###

应用场景：

1.select返回结果列中使用；

2.select语句中的order by,having等子句中使用；

3.DMl语句中where条件语句中使用表达式。

```sql
select @@auto_increment_increment;-- 查询自增步长
select version(); -- 查询版本号
select 100*3-1 as 计算结果; -- 表达式
-- 集体提高一分看看
select roll,score+1 as 提分后 from tb_test;
```





### where条件语句 ###

```sql
select sid,score from tb_student where score>=80 and score<=100;
select sid,score from tb_student where score>=80 && score<=100;
-- 模糊查询
select sid,score from tb_student where score between 80 and 100;
-- 除了2号同学，要其他所有人的成绩alter
select sid,score from tb_student where sid!=2;
-- 使用not
select sid,score from tb_student where not sid=2;
```



模糊查询比较符：

- is null
- is not null
- betweeen and
- like
- in



**like    通配符查询% _**

```sql
-- % 0到任意个字符，_一个字符
select sid,sname from tb_student where sname like '刘%';
select sid,sname from tb_student where sname like '%翔';
select sid,sname from tb_student where sname like '_翔';
-- 查询含有富字的
select sid,sname from tb_student where sname like '%富%';
```



**in**

```sql
select sid,sname from tb_student where sid in(1,5,3);
```

in()是1个或多个具体的值。



**null**

```sql
-- 查询名字没有填写的学号  不能直接写=null,这代表是错误，用is null
select sid from tb_student where sname=null;
select sid from tb_student where sname is not null or sname='';
```



## 连接查询 ##

JOIN对比



```sql
内连接inner join  
表的结果集的交集

左外连接left join  
以左表为基准，右表来一一匹配，匹配不上的返回左表的记录，右表以null填充

右外连接right join 
以右表为基准，左表来一一匹配，匹配不上的返回右表的记录，左表以null填充

等值连接，非等值连接

自连接
```

连接查询：需要多张表的数据进行查询，通过连接运算符号符实现多个查询；

 <img src="D:\Typora\md\picture\Mysql\image-20210517163045488.png" alt="image-20210517163045488" style="zoom:80%;float:left" />























### 内连接&左(右)连接 ###

```sql
-- 查询参加了考试同学的信息(学号，姓名，科目号，分数)

-- 内连接
select s.id,s.sname,r.subjectid,r.score 
from tb_student s
inner join tb_result r 
on s.id=r.sid;

-- 右连接
select s.id,s.sname,r.subjectid,r.score 
from tb_student s
right join tb_result r 
on s.id=r.sid;

-- 左连接 没有考试的同学也会查出来
select s.id,s.sname,r.subjectid,r.score 
from tb_student s
left join tb_result r 
on s.id=r.sid;

-- 等值连接
select s.id,s.sname,r.subjectid,r.score 
from tb_student s,tb_result r 
where s.id=r.sid;

-- 思考：查询参加了考试的同学的信息（多表查询）
-- 内连接
-- 右连接
-- 等值连接
```

join on   --连接查询

where    --等值查询

 <img src="D:\Typora\md\picture\Mysql\image-20210517164016975.png" alt="image-20210517164016975" style="zoom:80%;" />

  <img src="D:\Typora\md\picture\Mysql\image-20210517164350095.png" alt="image-20210517164350095" style="zoom:80%;" />



### 自连接 ###

```sql
drop table if exists tb_category;
create table tb_category(
     categoryid int unsigned not null auto_increment comment'主题ID',
     pid int not null comment'父ID',
     categoryname varchar(50) not null comment'名称',
     primary key(categoryid)
)engine=InnoDB;

INSERT INTO `tb_category` (`categoryid`, `pid`, `categoryname`)
VALUES('2','1','信息技术'),
('3','1','软件开发'),
('4','3','数据库'),
('5','1','美术设计'),
('6','3','web开发'),
('7','5','ps技术'),
('8','2','办公信息');

-- 需要：查询父栏目名称和其子栏目名称
-- 谁的父ID是他
-- 编写sql语句，将栏目的父子关系呈现出来(父栏目名称，栏目名称)
-- 核心思想：把一张表看成两张表，然后连接查询

select a.categoryname as '父栏目',b.categoryname as '子栏目'
from tb_category a,tb_category b 
where a.categoryid=b.pid;
```



### 多表查询 ###

```sql
-- 三表查询
-- 思考题:查询参加了考试的同学信息(学号,学生姓名,科目名,分数)
SELECT s.studentno,studentname,subjectname,StudentResult
FROM student s
INNER JOIN result r
ON r.studentno = s.studentno
INNER JOIN `subject` sub
ON sub.subjectno = r.subjectno

-- 查询学员及所属的年级(学号,学生姓名,年级名)
SELECT studentno AS 学号,studentname AS 学生姓名,gradename AS 年级名称
FROM student s
INNER JOIN grade g
ON s.`GradeId` = g.`GradeID`

-- 查询科目及所属的年级(科目名称,年级名称)
SELECT subjectname AS 科目名称,gradename AS 年级名称
FROM SUBJECT sub
INNER JOIN grade g
ON sub.gradeid = g.gradeid

-- 查询 数据库结构-1 的所有考试结果(学号 学生姓名 科目名称 成绩)
SELECT s.studentno,studentname,subjectname,StudentResult
FROM student s
INNER JOIN result r
ON r.studentno = s.studentno
INNER JOIN `subject` sub
ON r.subjectno = sub.subjectno
WHERE subjectname='数据库结构-1'

```

 <img src="D:\Typora\md\picture\Mysql\image-20210517165217759.png" alt="image-20210517165217759" style="zoom:80%;" />



## 排序和分页 ##

- 分页 limit
- 排序order by

 <img src="D:\Typora\md\picture\Mysql\image-20210517165541568.png" alt="image-20210517165541568" style="zoom:80%;float:left" />













主语关键字的先后顺序。



### 排序 ###

语法

```sql
-- 用于根据指定的类对结果集排序
-- 语句默认按照ASCII升序，DESC关键降序
order by
```



```sql
-- 查询 数据库结构-1 的所有考试结果(学号 学生姓名 科目名称 成绩)
-- 按成绩降序排序
SELECT s.studentno,studentname,subjectname,StudentResult
FROM student s
INNER JOIN result r
ON r.studentno = s.studentno
INNER JOIN `subject` sub
ON r.subjectno = sub.subjectno
WHERE subjectname='数据库结构-1'
ORDER BY StudentResult DESC
```



### 分页 ###

100万；

为什么要分页？缓解数据库压力，给人的体验更好，，（图片抖音瀑布流）。

语法

```sql
作用：用户体验，网络传输，查询压力
select * from tablename limit [offset,] row|rows OFFSET offset

推导:
   第一页 : limit 0,5
   第二页 : limit 5,5
   第三页 : limit 10,5
   ......
   第N页 : limit (pageNo-1)*pageSzie,pageSzie
   [pageNo:页码,pageSize:单页面显示条数]
   
*/
```

 <img src="D:\Typora\md\picture\Mysql\image-20210517170031338.png" alt="image-20210517170031338" style="zoom:80%;" />

 <img src="D:\Typora\md\picture\Mysql\image-20210517170246989.png" alt="image-20210517170246989" style="zoom:80%;" />





```sql
-- 每页显示5条数据
SELECT s.studentno,studentname,subjectname,StudentResult
FROM student s
INNER JOIN result r
ON r.studentno = s.studentno
INNER JOIN `subject` sub
ON r.subjectno = sub.subjectno
WHERE subjectname='数据库结构-1'
ORDER BY StudentResult DESC , studentno
LIMIT 0,5


-- 查询 JAVA第一学年 课程成绩前10名并且分数大于80的学生信息(学号,姓名,课程名,分数)
```

 <img src="D:\Typora\md\picture\Mysql\image-20210517170607017.png" alt="image-20210517170607017" style="zoom:80%;" />



## 子查询 ##

where(这个值是计算出来的)

where条件字句又嵌套另一个查询语句，子查询返回的结果一般是集合，故使用IN关键字。

```sql
-- 查询 数据库结构-1 的所有考试结果(学号,科目编号,成绩),并且成绩降序排列
-- 方法一:使用连接查询
SELECT studentno,r.subjectno,StudentResult
FROM result r
INNER JOIN `subject` sub
ON r.`SubjectNo`=sub.`SubjectNo`
WHERE subjectname = '数据库结构-1'
ORDER BY studentresult DESC;

-- 方法二:使用子查询(执行顺序:由里及外)
SELECT studentno,subjectno,StudentResult
FROM result
WHERE subjectno=(
   SELECT subjectno FROM `subject`
   WHERE subjectname = '数据库结构-1'
)
ORDER BY studentresult DESC;
```



```sql
-- 查询课程为 高等数学-2 且分数不小于80分的学生的学号和姓名
-- 方法一:使用连接查询
SELECT s.studentno,studentname
FROM student s
INNER JOIN result r
ON s.`StudentNo` = r.`StudentNo`
INNER JOIN `subject` sub
ON sub.`SubjectNo` = r.`SubjectNo`
WHERE subjectname = '高等数学-2' AND StudentResult>=80

-- 方法二:使用连接查询+子查询
-- 分数不小于80分的学生的学号和姓名
SELECT r.studentno,studentname FROM student s
INNER JOIN result r ON s.`StudentNo`=r.`StudentNo`
WHERE StudentResult>=80

-- 在上面SQL基础上,添加需求:课程为 高等数学-2
SELECT r.studentno,studentname FROM student s
INNER JOIN result r ON s.`StudentNo`=r.`StudentNo`
WHERE StudentResult>=80 AND subjectno=(
   SELECT subjectno FROM `subject`
   WHERE subjectname = '高等数学-2'
)

-- 方法三:使用子查询
-- 分步写简单sql语句,然后将其嵌套起来
SELECT studentno,studentname FROM student WHERE studentno IN(
   SELECT studentno FROM result WHERE StudentResult>=80 AND subjectno=(
       SELECT subjectno FROM `subject` WHERE subjectname = '高等数学-2'
  )
)
```



# MySQL函数

## 常用函数

> 数据函数

```sql
select abs();-- 绝对自
select ceiling();-- 向上取整
select floor();-- 向下取整
select rand()-- 返回0-1的随机数
select sign()-- 符号函数，负数返回-1，正数返回1,0返回0
```



> 字符串函数

```sql
SELECT CHAR_LENGTH('狂神说坚持就能成功'); /*返回字符串包含的字符数*/
 SELECT CONCAT('我','爱','程序');  /*合并字符串,参数可以有多个*/
 SELECT INSERT('我爱编程helloworld',1,2,'超级热爱');  /*替换字符串,从某个位置开始替换某个长度*/
 SELECT LOWER('KuangShen'); /*小写*/
 SELECT UPPER('KuangShen'); /*大写*/
 SELECT LEFT('hello,world',5);   /*从左边截取*/
 SELECT RIGHT('hello,world',5);  /*从右边截取*/
 SELECT REPLACE('狂神说坚持就能成功','坚持','努力');  /*替换字符串*/
 SELECT SUBSTR('狂神说坚持就能成功',4,6); /*截取字符串,开始和长度*/
 SELECT REVERSE('狂神说坚持就能成功'); /*反转
 
 -- 查询姓周的同学,改成邹
 SELECT REPLACE(studentname,'周','邹') AS 新名字
 FROM student WHERE studentname LIKE '周%';
```



> 日期和时间函数

```sql
 SELECT CURRENT_DATE();   /*获取当前日期*/
 SELECT CURDATE();   /*获取当前日期*/
 SELECT NOW();   /*获取当前日期和时间*/
 SELECT LOCALTIME();   /*获取当前日期和时间*/
 SELECT SYSDATE();   /*获取当前日期和时间*/
 
 -- 获取年月日,时分秒
 SELECT YEAR(NOW());
 SELECT MONTH(NOW());
 SELECT DAY(NOW());
 SELECT HOUR(NOW());
 SELECT MINUTE(NOW());
 SELECT SECOND(NOW());
```



> 系统信息函数

```sql
 SELECT VERSION();  /*版本*/
 SELECT USER();     /*用户*/
```

# 聚合函数

## 几个函数

| **函数名称** | **描述**                                                     |
| ------------ | ------------------------------------------------------------ |
| COUNT()      | 返回满足Select条件的记录总和数，如 select count(*) 【不建议使用 *，效率低】 |
| SUM()        | 返回数字字段或表达式列作统计，返回一列的总和。               |
| AVG()        | 通常为数值字段或表达列作统计，返回一列的平均值               |
| MAX()        | 可以为数值字段，字符字段或表达式列作统计，返回最大的值。     |
| MIN()        | 可以为数值字段，字符字段或表达式列作统计，返回最小的值。     |


```sql
 -- 聚合函数
 /*COUNT:非空的*/
 SELECT COUNT(studentname) FROM student;
 SELECT COUNT(*) FROM student;  -- 效率低不建议使用
 SELECT COUNT(1) FROM student;  /*推荐*/
```

 从含义上讲，count(1) 与 count(*) 都表示对全部数据行的查询。
 count(字段) 会统计该字段在表中出现的次数，忽略字段为null 的情况。即不统计字段为null 的记录。
 count(*) 包括了所有的列，相当于行数，在统计结果的时候，包含字段为null 的记录；
 count(1) 用1代表代码行，在统计结果的时候，包含字段为null 的记录 。




> 比较

```sql

 /*
 很多人认为count(1)执行的效率会比count(*)高，原因是count(*)会存在全表扫描，而count(1)可以针对一个字段进行查询。其实不然，count(1)和count(*)都会对全表进行扫描，统计所有记录的条数，包括那些为null的记录，因此，它们的效率可以说是相差无几。而count(字段)则与前两者不同，它会统计该字段不为null的记录条数。
 
 下面它们之间的一些对比：
 
 1）在表没有主键时，count(1)比count(*)快
 2）有主键时，主键作为计算条件，count(主键)效率最高；
 3）若表格只有一个字段，则count(*)效率较高。
 */
```

## 练习

> 题目

```sql
 -- 查询不同课程的平均分,最高分,最低分
 -- 前提:根据不同的课程进行分组
```

 

```sql
 SELECT subjectname,AVG(studentresult) AS 平均分,MAX(StudentResult) AS 最高分,MIN(StudentResult) AS 最低分
 FROM result AS r
 INNER JOIN `subject` AS s
 ON r.subjectno = s.subjectno
 GROUP BY r.subjectno
 HAVING 平均分>80;
```

必须要分组，否则只能出现一组。

```tex
 where写在group by前面.
 要是放在分组后面的筛选
 要使用HAVING..
 因为having是从前面筛选的字段再筛选，而where是从数据表中的>字段直接进行的筛选的
```



## MD5加密

> 简介

MD5即Message-Digest Algorrithm 5 （信息-摘要算法5，用于确保信息传输完整一致）。

 <img src="D:\Typora\md\picture\Mysql\image-20210517174458868.png" alt="image-20210517174458868" style="zoom:80%;float:left" />











> 实现数据加密

语法：

更新数据加密：

```sql
 update testmd5 set pwd = md5(pwd);
```

单独对某个用户加密：

```sql
 INSERT INTO testmd5 VALUES(3,'kuangshen2','123456')
 update testmd5 set pwd = md5(pwd) where name = 'kuangshen2';
```

插入新数据自动加密：

```sql
 INSERT INTO testmd5 VALUES(4,'kuangshen3',md5('123456'));
```

如何校验：

查询登录用户信息(md5对比使用，查看用户输入加密后密码进行对比)

```sql
SELECT * FROM testmd5 WHERE `name`='kuangshen' AND pwd=MD5('123456');
```





## 小结

 <img src="D:\Typora\md\picture\Mysql\image-20210517175147518.png" alt="image-20210517175147518" style="zoom:80%;float:left" />











```sql
 -- ================ 内置函数 ================
 -- 数值函数
 abs(x)            -- 绝对值 abs(-10.9) = 10
 format(x, d)    -- 格式化千分位数值 format(1234567.456, 2) = 1,234,567.46
 ceil(x)            -- 向上取整 ceil(10.1) = 11
 floor(x)        -- 向下取整 floor (10.1) = 10
 round(x)        -- 四舍五入去整
 mod(m, n)        -- m%n m mod n 求余 10%3=1
 pi()            -- 获得圆周率
 pow(m, n)        -- m^n
 sqrt(x)            -- 算术平方根
 rand()            -- 随机数
 truncate(x, d)    -- 截取d位小数
 
 -- 时间日期函数
 now(), current_timestamp();     -- 当前日期时间
 current_date();                    -- 当前日期
 current_time();                    -- 当前时间
 date('yyyy-mm-dd hh:ii:ss');    -- 获取日期部分
 time('yyyy-mm-dd hh:ii:ss');    -- 获取时间部分
 date_format('yyyy-mm-dd hh:ii:ss', '%d %y %a %d %m %b %j');    -- 格式化时间
 unix_timestamp();                -- 获得unix时间戳
 from_unixtime();                -- 从时间戳获得时间
 
 -- 字符串函数
 length(string)            -- string长度，字节
 char_length(string)        -- string的字符个数
 substring(str, position [,length])        -- 从str的position开始,取length个字符
 replace(str ,search_str ,replace_str)    -- 在str中用replace_str替换search_str
 instr(string ,substring)    -- 返回substring首次在string中出现的位置
 concat(string [,...])    -- 连接字串
 charset(str)            -- 返回字串字符集
 lcase(string)            -- 转换成小写
 left(string, length)    -- 从string2中的左边起取length个字符
 load_file(file_name)    -- 从文件读取内容
 locate(substring, string [,start_position])    -- 同instr,但可指定开始位置
 lpad(string, length, pad)    -- 重复用pad加在string开头,直到字串长度为length
 ltrim(string)            -- 去除前端空格
 repeat(string, count)    -- 重复count次
 rpad(string, length, pad)    --在str后用pad补充,直到长度为length
 rtrim(string)            -- 去除后端空格
 strcmp(string1 ,string2)    -- 逐字符比较两字串大小
 
 -- 聚合函数
 count()
 sum();
 max();
 min();
 avg();
 group_concat()
 
 -- 其他常用函数
 md5();
 default();
```





# 事务和索引

## 什么是事务

**要么都成功，要么都失败。**

 <img src="D:\Typora\md\picture\Mysql\image-20210517175434719.png" alt="image-20210517175434719" style="zoom:80%;" />

- 事务就是将一组SQL语句放在同一批次去执行
- 如果一个SQL语句出错则该批次内所有的SQL将被取消执行
- MySQL事务处理只支持InnoDB和BDB数据表类型



## 事务ACID原则

隔离导致的问题：脏读，幻读，不可重复度。。。。

 <img src="D:\Typora\md\picture\Mysql\image-20210517204252716.png" alt="image-20210517204252716" style="zoom:80%;float:left" />















 <img src="D:\Typora\md\picture\Mysql\image-20210517180200133.png" alt="image-20210517180200133" style="zoom:80%;float:left" />



























 <img src="D:\Typora\md\picture\Mysql\image-20210517180313196.png" alt="image-20210517180313196" style="zoom:80%;float:left" />















<img src="D:\Typora\md\picture\Mysql\image-20210517180348512.png" alt="image-20210517180348512" style="zoom:80%;float:left" />









 <img src="D:\Typora\md\picture\Mysql\image-20210517180348512.png" style="zoom:80%;float:left;" />























 <img src="D:\Typora\md\picture\Mysql\image-20210517180516614.png" alt="image-20210517180516614" style="zoom:80%;float:left" />





















**原子性(Atomic)**

- 整个事务中的所有操作，要么全部完成，要么全部不完成，不可能停滞在中间某个环节。事务在执行过程中发生错误，会被回滚（ROLLBACK）到事务开始前的状态，就像这个事务从来没有执行过一样。

**一致性(Consist)**

- 一个事务可以封装状态改变（除非它是一个只读的）。事务必须始终保持系统处于一致的状态，不管在任何给定的时间并发事务有多少。也就是说：如果事务是并发多个，系统也必须如同串行事务一样操作。其主要特征是保护性和不变性(Preserving an Invariant)，以转账案例为例，假设有五个账户，每个账户余额是100元，那么五个账户总额是500元，如果在这个5个账户之间同时发生多个转账，无论并发多少个，比如在A与B账户之间转账5元，在C与D账户之间转账10元，在B与E之间转账15元，五个账户总额也应该还是500元，这就是保护性和不变性。

   <img src="D:\Typora\md\picture\Mysql\image-20210517175649161.png" alt="image-20210517175649161" style="zoom:80%;float:left" />







**隔离性(Isolated)**

- 隔离状态执行事务，使它们好像是系统在给定时间内执行的唯一操作。如果有两个事务，运行在相同的时间内，执行相同的功能，事务的隔离性将确保每一事务在系统中认为只有该事务在使用系统。这种属性有时称为串行化，为了防止事务操作间的混淆，必须串行化或序列化请求，使得在同一时间仅有一个请求用于同一数据。

 <img src="D:\Typora\md\picture\Mysql\image-20210517175939614.png" alt="image-20210517175939614" style="zoom:80%;float:left" />



















**持久性(Durable)**

- 在事务完成以后，该事务对数据库所作的更改便持久的保存在数据库之中，并不会被回滚。

 <img src="D:\Typora\md\picture\Mysql\image-20210517175853435.png" alt="image-20210517175853435" style="zoom:80%;float:left" />













## 基本语法

```sql
-- 使用set语句来改变自动提交模式
SET autocommit = 0;   /*关闭*/
SET autocommit = 1;   /*开启*/

-- 注意:
--- 1.MySQL中默认是自动提交
--- 2.使用事务时应先关闭自动提交

-- 开始一个事务,标记事务的起始点
START TRANSACTION  

-- 提交一个事务给数据库
COMMIT

-- 将事务回滚,数据回到本次事务的初始状态
ROLLBACK

-- 还原MySQL数据库的自动提交
SET autocommit =1;

-- 保存点
SAVEPOINT 保存点名称 -- 设置一个事务保存点
ROLLBACK TO SAVEPOINT 保存点名称 -- 回滚到保存点
RELEASE SAVEPOINT 保存点名称 -- 删除保存点
```



 <img src="D:\Typora\md\picture\Mysql\image-20210517180820437.png" alt="image-20210517180820437" style="zoom:80%;float:left" />















<img src="D:\Typora\md\picture\Mysql\image-20210517181019736.png" alt="image-20210517181019736" style="zoom:80%;float:left" />





 <img src="D:\Typora\md\picture\Mysql\image-20210517181019736.png" alt="image-20210517181019736" style="zoom:80%;float:left" />















## 练习

 <img src="D:\Typora\md\picture\Mysql\image-20210517182007513.png" alt="image-20210517182007513" style="zoom:80%;float:left" />









不要选择全部执行。

> 题目

```tex
A在线买一款价格为500元商品,网上银行转账.
A的银行卡余额为2000,然后给商家B支付500.
商家B一开始的银行卡余额为10000
创建数据库shop和创建表account并插入2条数据
```

```sql
-- ===================事务=======================
CREATE DATABASE shop CHARACTER SET utf8 COLLATE utf8_general_ci;
USE shop;
CREATE TABLE IF NOT EXISTS `acount`(
   `id` INT(3) NOT NULL AUTO_INCREMENT,
   `name` VARCHAR(30) NOT NULL,
   `money` DECIMAL(9,2) NOT NULL,
   PRIMARY KEY (`id`)
)ENGINE=INNODB DEFAULT CHARSET utf8;

INSERT INTO `acount`(`name`,`money`) VALUES
('A',2000),('B',10000);
-- =====模拟转账
SET autocommit=0;
START TRANSACTION
UPDATE `acount` SET `money`=`money`-500 WHERE `name`='A';
UPDATE `acount` SET `money`=`money`+500 WHERE `name`='B';
COMMIT;-- 事务一旦提交就被持久化
ROLLBACK;
SET autocommit=1;
```



## 索引

**索引的本质是数据结构**。

> 索引的作用

- 提高查询速度
- 确保数据的唯一性
- 可以加速表和表之间的连接 , 实现表与表之间的参照完整性
- 使用分组和排序子句进行数据检索时 , 可以显著减少分组和排序的时间
- 全文检索字段进行搜索优化.



> 分类

- 主键索引 (Primary Key)
- 唯一索引 (Unique)
- 常规索引 (Index)
- 全文索引 (FullText)

不宜添加太多常规索引,影响数据的插入,删除和修改操作

 <img src="D:\Typora\md\picture\Mysql\image-20210517183445091.png" alt="image-20210517183445091" style="zoom:80%;" />

 <img src="D:\Typora\md\picture\Mysql\image-20210517183758065.png" alt="image-20210517183758065" style="zoom:80%;float:left" />



索引名(列名)

 <img src="D:\Typora\md\picture\Mysql\image-20210517183710206.png" alt="image-20210517183710206" style="zoom:80%;float:left" />





 <img src="D:\Typora\md\picture\Mysql\image-20210517184126254.png" alt="image-20210517184126254" style="zoom:80%;float:left" />





 <img src="D:\Typora\md\picture\Mysql\image-20210517184304531.png" alt="image-20210517184304531" style="zoom:80%;float:left" />















## 百万数据测试

 <img src="D:\Typora\md\picture\Mysql\image-20210517184614493.png" alt="image-20210517184614493" style="zoom:80%;float:left" />















随机数生成：

  <img src="D:\Typora\md\picture\Mysql\image-20210517185814048.png" alt="image-20210517185814048" style="zoom:80%;float:left" />





```sql
TRUNCATE `student`;
DESCRIBE `student`;
-- ===============百万数据测试==============
DELIMITER $$ -- 写函数之前必须写的标志
CREATE FUNCTION `mock_data`()
RETURNS INT
BEGIN
     DECLARE num INT DEFAULT 1000000;
     DECLARE i INT DEFAULT 0;
     WHILE i<num DO
       INSERT INTO `student`(`name`) VALUES(CONCAT('用户名:',1));
       SET i=i+1;
     END WHILE;
     RETURN i;
END
```



 ```sql

SELECT * FROM `student` WHERE  `name`='用户名:99998'; -- 0.852 sec
SELECT * FROM `student` WHERE  `name`='用户名:99998';-- 0.863 sec
EXPLAIN SELECT * FROM `student` WHERE  `name`='用户名:99998';-- 995796条数据

CREATE INDEX id_student_name ON `student`(`name`);
SELECT * FROM `student` WHERE  `name`='用户名:99998';-- 0.093 sec
EXPLAIN SELECT * FROM `student` WHERE  `name`='用户名:99998';-- 1条数据
 ```





# 权限及如何设计数据库

## 用户管理

> 基本命令

```sql
/* 用户和权限管理 */ ------------------
用户信息表：mysql.user

-- 刷新权限
FLUSH PRIVILEGES

-- 增加用户 CREATE USER kuangshen IDENTIFIED BY '123456'
CREATE USER 用户名 IDENTIFIED BY [PASSWORD] 密码(字符串)
  - 必须拥有mysql数据库的全局CREATE USER权限，或拥有INSERT权限。
  - 只能创建用户，不能赋予权限。
  - 用户名，注意引号：如 'user_name'@'192.168.1.1'
  - 密码也需引号，纯数字密码也要加引号
  - 要在纯文本中指定密码，需忽略PASSWORD关键词。要把密码指定为由PASSWORD()函数返回的混编值，需包含关键字PASSWORD

-- 重命名用户 RENAME USER kuangshen TO kuangshen2
RENAME USER old_user TO new_user

-- 设置密码
SET PASSWORD = PASSWORD('密码')    -- 为当前用户设置密码
SET PASSWORD FOR 用户名 = PASSWORD('密码')    -- 为指定用户设置密码

-- 删除用户 DROP USER kuangshen2
DROP USER 用户名

-- 分配权限/添加用户
GRANT 权限列表 ON 表名 TO 用户名 [IDENTIFIED BY [PASSWORD] 'password']
  - all privileges 表示所有权限
  - *.* 表示所有库的所有表
  - 库名.表名 表示某库下面的某表

-- 查看权限   SHOW GRANTS FOR root@localhost;
SHOW GRANTS FOR 用户名
   -- 查看当前用户权限
  SHOW GRANTS; 或 SHOW GRANTS FOR CURRENT_USER; 或 SHOW GRANTS FOR CURRENT_USER();

-- 撤消权限
REVOKE 权限列表 ON 表名 FROM 用户名
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 用户名    -- 撤销所有权限
```

> 权限解释

```sql
-- 权限列表
ALL [PRIVILEGES]    -- 设置除GRANT OPTION之外的所有简单权限
ALTER    -- 允许使用ALTER TABLE
ALTER ROUTINE    -- 更改或取消已存储的子程序
CREATE    -- 允许使用CREATE TABLE
CREATE ROUTINE    -- 创建已存储的子程序
CREATE TEMPORARY TABLES        -- 允许使用CREATE TEMPORARY TABLE
CREATE USER        -- 允许使用CREATE USER, DROP USER, RENAME USER和REVOKE ALL PRIVILEGES。
CREATE VIEW        -- 允许使用CREATE VIEW
DELETE    -- 允许使用DELETE
DROP    -- 允许使用DROP TABLE
EXECUTE        -- 允许用户运行已存储的子程序
FILE    -- 允许使用SELECT...INTO OUTFILE和LOAD DATA INFILE
INDEX     -- 允许使用CREATE INDEX和DROP INDEX
INSERT    -- 允许使用INSERT
LOCK TABLES        -- 允许对您拥有SELECT权限的表使用LOCK TABLES
PROCESS     -- 允许使用SHOW FULL PROCESSLIST
REFERENCES    -- 未被实施
RELOAD    -- 允许使用FLUSH
REPLICATION CLIENT    -- 允许用户询问从属服务器或主服务器的地址
REPLICATION SLAVE    -- 用于复制型从属服务器（从主服务器中读取二进制日志事件）
SELECT    -- 允许使用SELECT
SHOW DATABASES    -- 显示所有数据库
SHOW VIEW    -- 允许使用SHOW CREATE VIEW
SHUTDOWN    -- 允许使用mysqladmin shutdown
SUPER    -- 允许使用CHANGE MASTER, KILL, PURGE MASTER LOGS和SET GLOBAL语句，mysqladmin debug命令；允许您连接（一次），即使已达到max_connections。
UPDATE    -- 允许使用UPDATE
USAGE    -- “无权限”的同义词
GRANT OPTION    -- 允许授予权限


/* 表维护 */

-- 分析和存储表的关键字分布
ANALYZE [LOCAL | NO_WRITE_TO_BINLOG] TABLE 表名 ...
-- 检查一个或多个表是否有错误
CHECK TABLE tbl_name [, tbl_name] ... [option] ...
option = {QUICK | FAST | MEDIUM | EXTENDED | CHANGED}
-- 整理数据文件的碎片
OPTIMIZE [LOCAL | NO_WRITE_TO_BINLOG] TABLE tbl_name [, tbl_name] ...
```





> 数据库备份

为什么备份？

保证重要的数据不丢失，数据转移。

备份方式？

直接拷贝物理文件。。。

在sqlyog这种可视化工具导出。。。

命令行。。

```sql
-- 导出
1. 导出一张表 -- mysqldump -uroot -p123456 school student >D:/a.sql
　　mysqldump -u用户名 -p密码 库名 表名 > 文件名(D:/a.sql)
2. 导出多张表 -- mysqldump -uroot -p123456 school student result >D:/a.sql
　　mysqldump -u用户名 -p密码 库名 表1 表2 表3 > 文件名(D:/a.sql)
3. 导出所有表 -- mysqldump -uroot -p123456 school >D:/a.sql
　　mysqldump -u用户名 -p密码 库名 > 文件名(D:/a.sql)
4. 导出一个库 -- mysqldump -uroot -p123456 -B school >D:/a.sql
　　mysqldump -u用户名 -p密码 -B 库名 > 文件名(D:/a.sql)

可以-w携带备份条件

-- 导入
1. 在登录mysql的情况下：-- source D:/a.sql
　　source 备份文件
2. 在不登录的情况下
　　mysql -u用户名 -p密码 库名 < 备份文件
```





## 规范法数据库设计



 **软件项目开发周期中数据库设计 :**

- 需求分析阶段: 分析客户的业务和数据处理需求

- 概要设计阶段:设计数据库的E-R模型图 , 确认需求信息的正确和完整.

  

**设计数据库步骤**

- 收集信息

- - 与该系统有关人员进行交流 , 座谈 , 充分了解用户需求 , 理解数据库需要完成的任务.

- 标识实体[Entity]

  

- - 标识数据库要管理的关键对象或实体,实体一般是名词

- 标识每个实体需要存储的详细信息[Attribute]

- 标识实体之间的关系[Relationship]



 <img src="D:\Typora\md\picture\Mysql\image-20210517212232975.png" alt="image-20210517212232975" style="zoom:80%;" />





> 三大范式

**第一范式 (1st NF)**

第一范式的目标是确保每列的原子性,如果每列都是不可再分的最小数据单元,则满足第一范式

 <img src="D:\Typora\md\picture\Mysql\image-20210517212947627.png" alt="image-20210517212947627" style="zoom:80%;float:left" />





















**第二范式(2nd NF)**

第二范式（2NF）是在第一范式（1NF）的基础上建立起来的，即满足第二范式（2NF）必须先满足第一范式（1NF）。

第二范式要求每个表只描述一件事情

 <img src="D:\Typora\md\picture\Mysql\image-20210517213126770.png" alt="image-20210517213126770" style="zoom:80%;float:left" />























**第三范式(3rd NF)**

如果一个关系满足第二范式,并且除了主键以外的其他列都不传递依赖于主键列,则满足第三范式.

第三范式需要确保数据表中的每一列数据都和主键直接相关，而不能间接相关。

 <img src="D:\Typora\md\picture\Mysql\image-20210517213241847.png" alt="image-20210517213241847" style="zoom:80%;float:left" />

























**规范化和性能的关系**

阿里规范：关联查询的表不能超过三张表。

为满足某种商业目标 , 数据库性能比规范化数据库更重要(用户，成本体验)

在数据规范化的同时 , 要综合考虑数据库的性能

通过在给定的表中添加额外的字段,以大量减少需要从中搜索信息所需的时间

通过在给定的表中插入计算列,以方便查询；

故意增加冗余字段(多表查询变为单表查询)；

故意增加一些计算列(从大数据量降低为小数据量的查询：索引)



# JDBC(重点)

数据库驱动。 

 <img src="D:\Typora\md\picture\Mysql\image-20210517213807513.png" alt="image-20210517213807513" style="zoom:80%;float:left" />













 <img src="D:\Typora\md\picture\Mysql\image-20210517213852195.png" alt="image-20210517213852195" style="zoom:80%;" />



 <img src="D:\Typora\md\picture\Mysql\image-20210517213930691.png" alt="image-20210517213930691" style="zoom:80%;float:left" />

















## 第一个JDBC程序

1. 创建项目
2. 创建lib目录导入数据库驱动，记得Add as library..
3. 测试

```java
public class TestJDBC01 {
    public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //1.加载驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.用户信息和url
        String url="jdbc:mysql://localhost:3306/tb_jdbc?useSSL=false&useUnicode=true&characterEncoding=UTF-8";
        String username="root";
        String password="123456";
        //3.连接成功，数据库对象  connection 代表数据库
        Connection connection = DriverManager.getConnection(url,username,password);
        //4.执行sql对象 statement执行sql的对象
        Statement statement = connection.createStatement();
        //5.执行sql,可能存在结果，查看返回结果
        String sql="SELECT * FROM `users`;";
        ResultSet resultSet = statement.executeQuery(sql);//返回结果集
        while (resultSet.next()){
            System.out.println("id=" + resultSet.getObject("id"));
            System.out.println("name=" + resultSet.getObject("name"));
            System.out.println("password=" + resultSet.getObject("password"));
            System.out.println("email=" + resultSet.getObject("email"));
            System.out.println("birthday=" + resultSet.getObject("birthday"));
        }

        //6.释放连接
        resultSet.close();
        statement.close();
        connection.close();
    }

}
```

 <img src="D:\Typora\md\picture\Mysql\image-20210518082053734.png" alt="image-20210518082053734" style="zoom:80%;float:left" />

<img src="D:\Typora\md\picture\Mysql\image-20210518082855119.png" alt="image-20210518082855119" style="zoom:80%;float:left" />



 <img src="D:\Typora\md\picture\Mysql\image-20210518082604598.png" alt="image-20210518082604598" style="zoom:80%;float:left" />

















 <img src="D:\Typora\md\picture\Mysql\image-20210518082720605.png" alt="image-20210518082720605" style="zoom:80%;float:left" />















 <img src="D:\Typora\md\picture\Mysql\image-20210518082740457.png" alt="image-20210518082740457" style="zoom:80%;float:left" />











 <img src="D:\Typora\md\picture\Mysql\image-20210518082053734.png" alt="image-20210518082053734" style="zoom:80%;float:left" />![















 <img src="D:\Typora\md\picture\Mysql\image-20210518083104414.png" alt="image-20210518083104414" style="zoom:80%;float:left" />























最后需要关闭连接，因为connection非常消耗资源。

## statement对象

JDBC核心是使用statement来进行sql增删改查。

 <img src="D:\Typora\md\picture\Mysql\image-20210518083352152.png" alt="image-20210518083352152" style="zoom:80%;" />

 <img src="D:\Typora\md\picture\Mysql\image-20210518083428009.png" alt="image-20210518083428009" style="zoom:80%;float:left" />















 <img src="D:\Typora\md\picture\Mysql\image-20210518083511057.png" alt="image-20210518083511057" style="zoom:80%;float:left" />













 <img src="D:\Typora\md\picture\Mysql\image-20210518083539173.png" alt="image-20210518083539173" style="zoom:80%;float:left" />

 







<img src="D:\Typora\md\picture\Mysql\image-20210518083610957.png" alt="image-20210518083610957" style="zoom:80%;float:left" />



## 提取工具类

UtilsJDBC

```bash
driver=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/tb_jdbc?useSSL=false&useUnicode=true&characterEncoding=utf8
username=root
password=123456

```

TestInsert

```java
public class TestInsert {
    public static void main(String[] args) throws SQLException {
        Connection connection =null;
        Statement statement =null;
        ResultSet resultSet=null;
        try {
           connection = UtilsJDBC.getConnection();
           statement = connection.createStatement();
           String sql="INSERT INTO `users`(`id`,`name`,`password`,`email`,`birthday`) VALUES\n" +
                    "('3','上官婉儿','3344','qq.com','2000-10-1');";
           int i = statement.executeUpdate(sql);
           if(i>0) System.out.println("插入成功");
           else System.out.println("插入失败");
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            UtilsJDBC.releaseConnection(connection, statement, resultSet);
        }
    }
}
```

增删改................................只用改动sql语句

```java
public class TestDelete {
    public static void main(String[] args) throws SQLException {
        Connection connection =null;
        Statement statement =null;
        ResultSet resultSet=null;
        try {
            connection = UtilsJDBC.getConnection();
            statement = connection.createStatement();
            String sql="DELETE FROM `users` WHERE `name`='张无忌';";
            int i = statement.executeUpdate(sql);
            if(i>0) System.out.println("删除成功");
            else System.out.println("删除失败");
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            UtilsJDBC.releaseConnection(connection, statement, resultSet);
        }
    }
}
```

```java
public class TestUpdate {
    public static void main(String[] args) throws SQLException {
        Connection connection =null;
        Statement statement =null;
        ResultSet resultSet=null;
        try {
            connection = UtilsJDBC.getConnection();
            statement = connection.createStatement();
            String sql="UPDATE `users` SET `email`='966' WHERE `name`='上官婉儿';";
            int i = statement.executeUpdate(sql);
            if(i>0) System.out.println("更新成功");
            else System.out.println("更新失败");
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            UtilsJDBC.releaseConnection(connection, statement, resultSet);
        }
    }
}
```

```java
public class TestQuery {
    public static void main(String[] args) throws SQLException {
        Connection connection =null;
        Statement statement =null;
        ResultSet resultSet=null;
        try {
            connection = UtilsJDBC.getConnection();
            statement = connection.createStatement();
            String sql="SELECT * FROM `users`;";
            resultSet = statement.executeQuery(sql);//返回结果集
            while (resultSet.next()){
                System.out.println("id=" + resultSet.getObject("id"));
                System.out.println("name=" + resultSet.getObject("name"));
                System.out.println("password=" + resultSet.getObject("password"));
                System.out.println("email=" + resultSet.getObject("email"));
                System.out.println("birthday=" + resultSet.getObject("birthday"));
                System.out.println("=========================================================");
            }
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            UtilsJDBC.releaseConnection(connection, statement, resultSet);
        }
    }
}
```



## SQL注入

sql数据泄露，会被攻击导致数据泄露。**sql会被拼接or**

 <img src="D:\Typora\md\picture\Mysql\image-20210518105744211.png" alt="image-20210518105744211" style="zoom:80%;float:left" />





 <img src="D:\Typora\md\picture\Mysql\image-20210518105519627.png" alt="image-20210518105519627" style="zoom:80%;float:left" />





盗取所有用户信息：

 <img src="D:\Typora\md\picture\Mysql\image-20210518105558496.png" alt="image-20210518105558496" style="zoom:80%;float:left" />







## PreparedStatement对象

statement不安全，容易受到sql注入攻击。

PreparedStatement是安全的。

preparedstatement防止sql注入的本质，把传递进来的参数当做字符。

假设期中存在转义字符,就直接忽略掉，'会被直接转义  （Mybastis）

```java
public class TestInsert {
    public static void main(String[] args) throws SQLException {
        Connection conn = UtilsJDBC.getConnection();
        //区别
        String sql = "INSERT INTO `users`(`id`,`name`,`password`,`email`,`birthday`) VALUES(?,?,?,?,?)";
        PreparedStatement st = conn.prepareStatement(sql);//预编译sql,先写sql，不执行
        //手动赋值
        st.setInt(1,5);
        st.setString(2,"韩信");
        st.setString(3,"2222");
        st.setString(4,"@126.com");
        //注意点：sql.Data   util.Data
        //new java.util.Date().getTime()获得时间戳
        st.setString(5, String.valueOf(new Date(new java.util.Date().getTime())));
        int i = st.executeUpdate();
        if(i>0) System.out.println("插入成功");
        else System.out.println("插入失败");
        UtilsJDBC.releaseConnection(conn,st,null);
    }
}
```

```java
public class TestDelete {
    public static void main(String[] args) throws SQLException {
        Connection conn = UtilsJDBC.getConnection();

        String sql="DELETE FROM `users` WHERE `name`=?;";
        PreparedStatement st = conn.prepareStatement(sql);

        st.setString(1,"韩信");
        int i = st.executeUpdate();
        if(i>0) System.out.println("删除成功");
        else System.out.println("删除失败");
        UtilsJDBC.releaseConnection(conn, st, null);
    }
}
```

```java
public class TestQuery {
    public static void main(String[] args) throws SQLException {
        Connection conn = UtilsJDBC.getConnection();

        String sql="SELECT * FROM `users` where `id`>=?;";
        PreparedStatement st = conn.prepareStatement(sql);
        st.setInt(1,2);
        ResultSet res = st.executeQuery();

        while (res.next()){
            System.out.println("id=" + res.getObject("id"));
            System.out.println("name=" + res.getObject("name"));
            System.out.println("password=" + res.getObject("password"));
            System.out.println("email=" + res.getObject("email"));
            System.out.println("birthday=" + res.getObject("birthday"));
            System.out.println("=========================================================");
        }
        UtilsJDBC.releaseConnection(conn, st, res);
    }
}public class TestUpdate {
    public static void main(String[] args) throws SQLException {
        Connection conn = UtilsJDBC.getConnection();

        String sql="UPDATE `users` SET `email`='966' WHERE `name`=?;";
        PreparedStatement st = conn.prepareStatement(sql);
        st.setString(1,"孙尚香");

        int i = st.executeUpdate();
        if(i>0) System.out.println("更新成功");
        else System.out.println("更新失败");
        UtilsJDBC.releaseConnection(conn, st, null);
    }
}
```

## 使用IDEA连接数据库

 <img src="D:\Typora\md\picture\Mysql\image-20210518115612069.png" alt="image-20210518115612069" style="zoom:80%;float:left" />

























## 事务操作

要么都成功要么都失败

ACID原则。

 <img src="D:\Typora\md\picture\Mysql\image-20210518120104270.png" alt="image-20210518120104270" style="zoom:80%;float:left" />





















```java
public class TestTransaction {
    public static void main(String[] args){
       Connection conn =null;
       PreparedStatement st =null;
        try {
            conn = UtilsJDBC.getConnection();
            //关闭事务自动提交,关闭后自动开启事务
            conn.setAutoCommit(false);
            String sql1="UPDATE `account` SET `money`=`money`-500 WHERE `name`='A'";
            String sql2="UPDATE `account` SET `money`=`money`+500 WHERE `name`='B'";
            st = conn.prepareStatement(sql1);
            st.executeUpdate();
            //模拟失败
            int i=1/0;
            st = conn.prepareStatement(sql2);
            st.executeUpdate();
            conn.commit();
            System.out.println("提交成功");
            conn.setAutoCommit(true);
        } catch (SQLException e) {
            try {
                assert conn != null;
                conn.rollback();//默认失败回滚，可以不设置
            } catch (SQLException e1) {
                e1.printStackTrace();
            }
            System.out.println("操作失败");
            e.printStackTrace();
        } finally {
            UtilsJDBC.releaseConnection(conn,st,null);
        }
    }
}
```

## 数据库连接池

### DBCP

数据库连接--执行完毕--释放  --连接--释放  十分浪费系统资源，开销非常法。

**池化技术：准备一些预先准备好的资源，过来就先连接预先准备好饿连接。**

最小连接数-----常用连接数

最大连接数-----业务最高承载上限

排队等待，等待超时。。

编写连接池只需要实现一个接口DataSource

 <img src="D:\Typora\md\picture\Mysql\image-20210518122752992.png" alt="image-20210518122752992" style="zoom:80%;float:left" />













1. 创建项目
2. 导入jar包

 <img src="D:\Typora\md\picture\Mysql\image-20210518153923959.png" alt="image-20210518153923959" style="zoom:80%;float:left" />







3. 测试

```java
public class UtilsJDBC_DBCP {

    static DataSource dataSource =null;
    static {
        try {
            InputStream is = UtilsJDBC_DBCP.class.getClassLoader().getResourceAsStream("dbcpconfig.properties");//拿到流
            Properties properties = new Properties();
            properties.load(is);
            //创建数据源  工厂模式
            dataSource = BasicDataSourceFactory.createDataSource(properties);

        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    //1.获取连接
    public  static Connection getConnection() throws SQLException {
          return  dataSource.getConnection();
    }

    //2.释放连接
    public static void releaseConnection(Connection conn, Statement st, ResultSet res) {

        try {
            if(res!=null) res.close();
            if(st!=null) st.close();
            if(conn!=null) conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }

    }
}
```



### C3P0

> 导入jar包

 <img src="D:\Typora\md\picture\Mysql\image-20210518155845714.png" alt="image-20210518155845714" style="zoom:80%;float:left" />







```java
public class UtilsJDBC_C3P0 {

    static DataSource dataSource =null;
    static {
        try {
            /*代码版配置
           ComboPooledDataSource combo = new ComboPooledDataSource();
           combo.setDriverClass();
           combo.setUser();
           combo.setPassword();
           combo.setJdbcUrl();
           combo.setMaxPoolSize();
           combo.setMinPoolSize();
            * */

            //创建数据源  工厂模式
            dataSource = new ComboPooledDataSource("MySQL");//配置文件写法

        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    //1.获取连接
    public  static Connection getConnection() throws SQLException {
        return  dataSource.getConnection();
    }

    //2.释放连接
    public static void releaseConnection(Connection conn, Statement st, ResultSet res) {

        try {
            if(res!=null) res.close();
            if(st!=null) st.close();
            if(conn!=null) conn.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }

    }
}

```

 <img src="D:\Typora\md\picture\Mysql\image-20210518162102377.png" alt="image-20210518162102377" style="zoom:80%;float:left" />









```xml
<c3p0-config>
    <default-config>
        <property name="driverClass">com.mysql.jdbc.Driver</property>
        <property name="jdbcUrl">jdbc:mysql://localhost/std</property>
        <property name="user">root</property>
        <property name="password">root</property>

        <property name="initialPoolSize">10</property>
        <property name="maxIdleTime">30</property>
        <property name="maxPoolSize">100</property>
        <property name="minPoolSize">10</property>
        <property name="maxStatements">200</property>
    </default-config>

    <!-- This app is massive! -->
    <named-config name="MySQL">
        <property name="driverClass">com.mysql.jdbc.Driver</property>
        <property name="jdbcUrl">jdbc:mysql://localhost:3306/tb_jdbc?useSSL=false&amp;useUnicode=true&amp;characterEncoding=utf8</property>
        <property name="user">root</property>
        <property name="password">123456</property>


        <property name="acquireIncrement">5</property>
        <property name="initialPoolSize">10</property>
        <property name="minPoolSize">5</property>
        <property name="maxPoolSize">20</property>
    </named-config>
</c3p0-config>
```





 <img src="D:\Typora\md\picture\Mysql\image-20210518161914048.png" alt="image-20210518161914048" style="zoom:80%;float:left" />







