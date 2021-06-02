[[我的工作台 - Gitee.com](https://gitee.com/ma-fu/dashboard/projects)]:

什么是CSS预处理器？

用一种专门的编程语言为CSS增加一些编程的特性将CSS作为一种目标生成文件，然后开发者就只要使用这种编程语言进行CSS编码工作。通俗的讲就是用一种专门的编程语言进行web页面样式设计在通过编译器转化为正常的CSS文件以便项目使用。

常见的CSS预处理器：

SASS:基于Ruby

LESS:基于NodeJS



JavaScript框架：

**JQuery**:熟知的JavaScript框架，优点是简化了DOM操作，缺点是DOM操作太频繁，影响前端性能：在前端眼里使用它仅仅是为了兼容IE6,7,8。

**Angular**:Google收购前的框架，其特点是将后台的MVC模式搬到了前端并增加了模块化开发概念。

**React**:Facebook出品，一款高性能的JS前端框架，特点是提出了新概念[虚拟DOM]用于减少真实DOM操作，提升了渲染效率，缺点是复杂需要额外学习一门语言JSX

**Vue**:一款渐进式JavaScript框架，逐步实现新特性，如实现模块化开发、路由、状态管理器等，其特点是综合了Angular模块化和React虚拟DOM的优点。

Axios:前端通信框架。因为Vue的边界很明确就是为了处理DOM并不具备通信能力，此时需要额外通信框架与服务器交互，当然也可以直接使用JQuery提供的AJAX通信功能。

UI框架：

Ant-Desigin:阿里巴巴出品，基于React的UI框架。

ElementUI,iview,ice:饿了么出品，基于Vue的UI框架。

Bootstrap:Twitter出品的用于前端开发的开源工具包。

AmazeUI:"妹子"UI，一款HTML5跨屏前端框架。

# 什么是JavaScript

JavaScript是一门世界上最流行的脚本语言。

10天~

**一个合格的后端人员必须精通JavaScript**

ECMAScript是JavaScript的一个标准

最新的版本已经到es6版本~

但是大部分浏览器还只停留在支持es代码上

开发环境~线上环境不统一，版本不一致



核心：关键字，变量，流程控制，对象，数组，结构，闭包。

# 快速入门

## 引入JavaScript

1.内部标签

```java
<script>
    // （注释加空格）····
</script>
```

2.外部引入

```java
 <script src="js/hello.js"></script>
```

script成对引入

## 语法入门

```javascript
    <!--  JavaScript严格区分大小写  -->
    <script>
        // （注释加空格）1.定义变量 变量类型 变量名=变量值
        let score = 66;
        let name="mafu";

        alert(name);
        // 跳转控制
        if (score>=60&&score<70) {
            alert("60-70");
        }else if (score>=70&&score<80) {
            alert("70-80");
        }else if(score>=80&&score<90){
            alert("80-90");
        }else {
            alert(score);
        }
    //    浏览器控制台输出  console.log() 打印变量  少用alert
    </script>
```

调试:

<img src="https://i.loli.net/2021/05/20/naJ6fXQA3B7KNtc.png" alt="QQ截图20210501165854" style="zoom:67%;float:left" />

## 数据类型

数值，文本，图形，音频，视频·····

**number**:

javascript不区分小数整数

整数  浮点数  科学计数 负数  NaN不是一个数  Infinity

**字符串**

'abc'  "abc"

**布尔值**

true false

**逻辑运算  比较运算**

== 等于 （类型不一样值一样也会判断为true）

**=== 绝对等于 （正常情况下使用===）**

须知：

NaN===NaN  与所有数值都不相等 只能通过isNaN()判断

浮点数问题：可能存在精度损失

```javascript
console.log((1/3)===(1-2/3));

console.log(Math.abs(1/3-(1-2/3))<0.0000001);
```

**null空和undefined未定义**

**数组**    **对象**

类型可以不同

数组用中括号，对象用大括号



定义对象   每个属性之间用逗号隔开最后一个不需要

```java
        let arr = [1, 2, 3, 4, 'hello', "str"];
        console.log(arr);
        // Person person=new Person(1,2,3,4,5);
        let  person={
            name:"mafu",
            age:2,
            tags:['1','abc','~']
        }
```

## 严格检查模式strict

严格检查模式预防JavaScript的随意性导致的问题

'use strict';必须写在第一行

```javascript
        'use strict';
        // 默认是全局变量
        let i;
        i=1;
        // es6中局部变量用let定义
```

# 数据类型详解

## 字符串类型

1.正常字符串使用单引号或者双引号，注意特殊字符用转义

```tex
\n 换行
\' 
\t tab
\u4e2d 中    \u#### Unicode字符

\X##    Ascall字符
```

2.多行字符串编写

piao键

```javascript
    <script>
        'use strict';
         // console.log('a\'');
         // console.log("a");
        let msg = `ma
                   sss
                   aaa
                   dd
                   ll`;
        console.log(msg);
    </script>
```

3.模板字符串

```javascript
        let msg="mafu";
        console.log(`你好呀！${msg}`);
```

4.字符串长度

5.字符串的可变性：不可变

<img src="https://i.loli.net/2021/05/20/1gDXlZIUiC3hFQV.png" alt="QQ截图20210502094536" style="zoom:67%;float:left;" />

大小写转换：console.log(st.toUpperCase())

6.indexOf('t')    chatAt(1)

7.subString(1,3) 

包头包尾

子字符串

<img src="https://i.loli.net/2021/05/20/sFGBMiKJ5RLTbkW.png" alt="QQ截图20210502095258" style="zoom: 80%;float:left" />

## 数组类型

Array可以包含任意的数据类型

```javascript
var arr=[1,2,3,4,5,6]
```

1.长度，

数组可变性：可变

注意：假如给arr.length赋值，数据大小就会发生变化，如果赋值变小则元素丢失

<img src="https://i.loli.net/2021/05/20/eEvM3J71CyO6Hwm.png" alt="QQ截图20210502100107" style="zoom:80%;float:left" />



<img src="https://i.loli.net/2021/05/20/5el8J9YEtH13ywU.png" alt="QQ截图20210502100424" style="zoom:80%;float:left" />

2.slice()  数组版的substing()  截取Array的一部分    arr.slice(1)

包头包尾

3.往尾部push，pop

```javascript
arr.push("a","b")
```

4.往头部unshift()   shift()

```javascript
arr.unshift("a","b");
```

5.arr.sort()    arr.reverse()

6.拼接arr.concat   注意：并没有修改原数组，只是返回新数组

```javascript
arr.concat([1,2,3])
```

7.拼接数组元素arr.join 使用特定字符连接

<img src="https://i.loli.net/2021/05/20/VEwp3aGtIFuH95J.png" alt="QQ截图20210502102319" style="zoom: 80%;float:left" />

8.多维数组   arr.fill()  arr.find()

arr=[[1,2,3],["a","b","c"],['A','B']]

数组：存、取。

方法可以自己实现

## 对象类型

若干个键值对

```javascript
var 对象名={
    属性名：属性值，
    属性名：属性值，
    属性名：属性值
}
```

js中对象，{......}表示对象，键值对描述属性 xxxxx:xxxxxx  多个属性,隔开，最后一个不用！

1.赋值

person.name="mf"

2.使用一个不存在的对象属性不报错

3.动态的删减添加属性

delete person.name

person.haha="hhhh"

<img src="https://i.loli.net/2021/05/20/dpz4lXUvnTEAKqu.png" alt="QQ截图20210502103658" style="zoom:80%;float:left" />

4.判断属性值是否在对象中 in

JS中所有的键都是字符串，值是任意对象！

```javascript
>person
<{age: 3, address: "www.com", haha: "hhhh"}
>person['age']
<3
>'age' in person
<true

//继承
>'toString' in person
<true
//自己本身具有的
>person.hasOwnProperty('toString')
<false
```

# 流程控制

## 分支与循环

if判断

for while循环 避免死循环

while弹窗病毒

```javascript
while(ture){
    alert("hahaha");
}
```

do while()  肯定会执行一次

forEach函数方法

```javascript
let arr=[1,2,3,42];
arr.forEach(function (value){
    console.log(value);
});
```

for in 遍历 注意是索引index  不建议使用

```javascript
for(let index in arr){
    if(arr.hasOwnProperty(index)){
        console.log("存在");
        console.log(arr[index]);
    }

}
```

for of 才是具体的值  

```javascript
for(let value of arr){
    if(arr.hasOwnProperty(value)){
        console.log("存在");
        console.log(arr[value]);
    }

}
```



# Map和Set

ES6新特性

注意：往Map和Set集合加入的是键值对所以需要**先用[]**先包裹起来

map.get()  map.set()   map.delete()

```javascript
//学生的名字，学生的名字
let map=new Map([['tom',90],['jam',88],['rose',77]]);
console.log(map.get('tom'));
map.set('admin',100);
```



Set无序不重复集合

set.add()  set.delete()  set.has()

```javascript
let set=new Set([3,1,1,1,1]);
set.add(1);  //添加
set.delete(1);  //删除
console.log(set.has(3)); //判断是否包含
```

## 迭代

用of遍历数组、遍历map，set：

```javascript
for(let value of arr){
    if(arr.hasOwnProperty(value)){
        console.log("存在");
        console.log(arr[value]);
    }
}
for (let value of map){
    console.log(value);
}
for (let value of set){
    console.log(value);
}
```

# 函数

## 函数定义

function

```javascript
        //函数定义方式一
        function abs(x){
            if(x>=0){
                return x;
            }else {
                return -x;
            }
        }
        //函数定义方式二
        let absII = function (x) {
            if (x >= 0) {
                return x;
            } else {
                return -x;
            }
        };
```

一旦执行return函数结束返回结果

如果没有执行return函数也会执行完返回结果undefined



函数调用：

JavaScript可以传递任意个参数，也可以不传递参数

参数进来是否存在问题？参数不存在如何规避？

```javascript
function abs(x){
    //手动抛出异常判断
    if(typeof x!='number'){
        throw 'not a number';
    }
}
```



**arguments**是一个JS免费赠送的关键字：可以拿到多个参数

代表传递进来的所以参数，是一个数组

```javascript
console.log("x=>"+x);
for( let  i=0;i<arguments.length;i++){
    console.log(arguments[i]);
}
```

问题：

Arguement会包含所有的参数，我们有时候会想用多余参数进行附加操作时的问题是需要排除已有的参数~



```react
rest
```

以前：

```javascript
function ab(a,b){
    console.log("a=>"+a);
    console.log("b=>"+b);
    if (arguments.length>2){
        for (let i=2;i<arguments.length;i++){

        }
    }
}
```

es6引入的新特性，获取除了已经定义的参数之外的所有参数

只需在后面增加一个伪参数...rest

```javascript
function ab(a,b,...rest){
    console.log("a=>"+a);
    console.log("b=>"+b);
    console.log(rest);
}
```

只能写在最后必须用...标识

## 变量作用域

var let const详解

在JavaScript中函数查找从自身函数开始~

```javascript
<script>
    'use strict';
    function  qj(){
        var x=1;
        function qj2(){
            var x = 'A';
            console.log('inner=>'+x);//outer1
        }
        console.log('outer=>'+x);
        qj2();
    }
    qj();
</script>
```

**自动提升**

说明：js执行引擎自动提升了y的声明但是不会提升变量y的赋值

养成规范：所以一般会将全部变量在开始的时候就全部申明。

```javascript
function qj3(){
    var x=1,
        y=x+1,
        z,i,a;//undefined
    //之后随意用
    z=1;
}
```



**全局变量**

全局对象window   注意只能是全局不能是局部

```javascript
var x=1;
alert(x);
alert(window.x);
```

JavaScript实际上只有一个全局作用域，任何变量（函数也可以视为变量）

**规范：**

由于所有的全局变量都会绑定到window，如果不同的js文件使用了相同的全局变量，冲突-》如何能够减少冲突？

```javascript
//唯一的全局变量
var mafu={};
//定义全局变量
mafu.name='mafu';
mafu.add=function (a,b){
    return a+b;
}
console.log(mafu.name);
```

把自己代码全部放入自己定义的唯一空间名字中，降低全局命名冲突的问题~

jQuery.

$()

**局部作用域let**

```javascript
function qj4(){
    for (var i = 0; i < 3; i++) {
        console.log(i);
    }
    console.log(i+1);//问题？i出了作用域还能用
}
```

es6中引出let关键字解决局部作用域冲突问题

```javascript
function qj4(){
    for (let i = 0; i < 3; i++) {
        console.log(i);
    }
    //Uncaught ReferenceError: i is not defined
    console.log(i+1);
}
```

规范：使用let去定义局部作用域变量

**常量const**

es6之前：只有用全部大写字母的变量就是常量，但还是可以改变值。

es6引入const



## 方法

把函数放在对象的里面，对象只有两个东西：属性和方法：

```javascript
<script>
    let person = {
        name: 'mafu',
        birth: '2020',
        //方法
        age:function (a,b){
            //今年-
            let now=new Date().getFullYear();
            console.log(now);
            return now-this.birth;
        }
    };
</script>
```



this.代表什么？拆开代码看

getAge()
NaN
person.age()
1

```javascript
    <script>
        function getAge(){
            //今年-
            let now=new Date().getFullYear();
            return now-this.birth;
        }
        let person = {
            name: 'mafu',
            birth: '2020',
            //方法,注意直接写函数名不用括号
            age:getAge
        }
    </script>
```

this是无法指向的，是默认指向调用它的那个对象



**apply**

在js中可以控制this指向

```javascript
getAge.apply(person,[]);//this指向person，参数为空（为空时用数组表示）
```



# 常用对象

内部对象

标准对象

判断对象类型  typeof  x



## Date

基本使用：

```javascript
      let now= new Date();//Sun May 02 2021 17:39:59 GMT+0800 (中国标准时间)
      now.getFullYear();//年份
      now.getMonth();//月 0~11
      now.getDate();//日
      now.getDay()//星期几
      now.getHours();
      now.getMinutes();
      now.getSeconds();

      now.getTime();//时间戳全时间统一 1970 1.1.0:0
      new Date(1619948577617);//时间戳换时间
```

转换：

```javascript
now=new Date(1619948577617)
Sun May 02 2021 17:42:57 GMT+0800 (中国标准时间)
now.toLocaleString()
"2021/5/2下午5:42:57"
```



## JSON

早期，所有数据传输习惯使用xml文件！

json是什么？

-  是一种轻量级的数据交换格式
- 简洁和清晰的**层次结构**使得 JSON 成为理想的数据交换语言
- 有效地提升网络传输效率

JavaScript中一切皆对象，任何支持js的类型都可以用json表示。

格式：

- 对象都用花括号{}
- 数组都用中括号[]
- 所有的键值对都使用:"key:value"

<img src="https://i.loli.net/2021/05/20/1E8hZUeqGSFQgLN.png" alt="QQ截图20210502182229" style="zoom:67%;float:left" />



JSON字符串和JS对象的转换：

```javascript
       let person={
           name:"mafu",
           age:13,
           sex:"man"
       }
       //对象转换为JSON字符串
       let  jsonPerson=JSON.stringify(person);
       //JSON字符串转换为对象
       let  obj=JSON.parse(jsonPerson);
```

很多人搞不清楚JSON字符串和JS对象的区别

```javascript
var obj={a:'hello',b:'hi'};
var json='{"a":"hello","b":"hi"}';
```



## Ajax

- 原生的js写法，xhr异步请求
- jQuery封装好的方法  $("#name").ajax("")
- axios 请求



# 面向对象编程

JavaScript、Java、C#....特点：面向对象



类：模板

对象：具体的实例

JavaScript有些区别：需要转换一下思维方式

**原型：**  原型对象简单理解为一个父类

```javascript
       "use strict";
       let person={
           name:"mafu",
           age:13,
           run:function (){
               console.log(this.name+"run……")
           }
       };
       let xiaoMing={
           name:"xiaoMing",
       };
       //指向原型  注意是两哥下划线
       xiaoMing.__proto__=person;
```







**class继承：**

以前:

```javascript
       function student(name){
           this.name=name;
       }
       //给student新增一个方法
       student.prototype.hello=function (){
           alert("hello");
       };
```

class关键字在es6引入

1.定义一个类，属性，方法

```javascript
       class student{
           constructor(name) {
               this.name=name;
           }
           hello(){
               alert("hello!");
           }
       }
       let xiaoMing=new student(`xiaoMing`);
```

2.继承

```javascript
       //继承  等价之前__proto__原型指向父类
       class middleStudent extends student{
            constructor(name,grade) {
                super(name);
                this.grade=grade;
            }
            myGrade(){
                alert("myGrade!");
            }
       }
       let xiaoMing=new middleStudent(`xiaoMing`,1);
```

本质还是父类

<img src="https://i.loli.net/2021/05/20/zp5tJFBmbWX9LTu.png" alt="QQ截图20210502191923" style="zoom:80%;float:left" />

> 原型链



# 操作Bom元素

> 浏览器介绍

JavaScript和浏览器的关系？

JavaScript诞生就是为了能够在浏览器中运行！

BOM：    浏览器对象模型

浏览器内核：

- IE 6~11
- Chorme
- Safari
- FireFox

三方浏览器：

- QQ浏览器

- 360浏览器

  

## window

window代表浏览器窗口。

```javascript
window.alert(1)
undefined
window.innerWidth
980
window.innerHeight
2257
window.outerHeight
602
window.outerWidth
261
```



## navigator

navigator封装了浏览器的信息,大多数时候不会使用这个navigator对象，因为会被人为修改！

```javascript
navigator.appVersion
"5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Mobile Safari/537.36 Edg/90.0.818.51"
navigator.userAgent
"Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Mobile Safari/537.36 Edg/90.0.818.51"
navigator.platform
"Win32"
```



## screen

代表屏幕尺寸

```javascript
screen.width
261
screen.height
602
```



## location

location代表当前页面的URL信息

```javascript
host: "www.bilibili.com"
hostname: "www.bilibili.com"
href: "https://www.bilibili.com/"
origin: "https://www.bilibili.com"
pathname: "/"
port: ""
protocol: "https:"
reload: ƒ reload()  //刷新网页
```

```javascript
//设置新的地址
location.assign("https://www.baidu.com/")
```



## Document

document代表当前页面，HTML DOM文档树

获取具体的文档树节点：

```html
  <dl id="app">
      <dt>java</dt>
      <dd>javascript</dd>
      <dd>javaSE</dd>
  </dl>
  <script>
      let dl = document.getElementById('app');
  </script>
```

document可以直接获取cookie

>document.cookie



劫持cookie原理

www.taobao.com

```html
<script stc="aa.js"></scripts>
<!--恶意人员获取你的cookie信息上传到他的服务器-->
```

服务器端可以设置cookie：httpOnly



## History（不建议使用）

```javascript
history.forword()//前进
history.back()//后退
```

代表浏览器的历史记录



# 操作Dom元素（重点）

DOM：文档对象模型

> 核心

浏览器网页就是一个Dom树形结构

<img src="https://i.loli.net/2021/05/20/BYemVzECOUPfwpj.png" alt="QQ截图20210502214200" style="zoom:50%;float:left;" />

- 更新：更新Dom节点
- 遍历Dom节点：得到Dom节点
- 删除
- 添加

要操作Dom节点就必须先拿到这个Dom节点



> 获取Dom节点

```html
    <div id="father">
        <h1>标签名</h1>
        <p id="p1">p1</p>
        <p class="p2">p2</p>
    </div>

    <script>
        //标签选择器
        let h1=document.getElementsByTagName('h1');

        let p1= document.getElementById('p1');
        let p2= document.getElementsByClassName('p2');
        let father= document.getElementById('father');
        //获取所有子节点
        let children=father.children;
        father.firstChild;
        father.lastChild;
    </script>
```

这是原生代码，之后我们尽量会使用jQuery()



> 更新Dom节点

```javascript
id1.innerText='345'//修改文本的值  属性使用字符串包裹
id1.innerHTML='<strong>123</strong>' //解析HTML   插入节点

//操作js
id1.style.color='red'  
id1.style.fontSize='38px'  //驼峰命名
```



> 删除节点

删除节点的步骤：先获取父节点，再通过父节点删除自己

```javascript
father.removeChild(p1)
```

```javascript
        let self=document.getElementById('p1');
        let father= self.parentElement;
        father.removeChild(self);
```

```javascript
father.removeChild(father.children[0])//注意是动态删除，时刻变化
```



> 插入节点

我们获得了某个Dom节点，假设这个Dom节点是空的，我们通过innerText，或innerHTML就可以增加一个元素，但是如果这个Dom节点已经存在元素了就不能这么干因为会覆盖元素！

**追加**

会改变追加元素的位置

```html
      <p id="js">javascript</p>
      <div id="list">
          <p id="se">javaSE</p>
          <p id="ee">javaEE</p>
          <p id="me">javaME</p>
      </div>
      <script>
          let js=document.getElementById('js');
          let list=document.getElementById('list');
          list.appendChild(js);//追加到后面
          
          //通过js创建新的节点
          let newP=document.createElement('p');//创建一个p标签
          newP.id='newP';
          newP.innerText='hello';
          list.append(newP);
          
          
          //创建一个style标签
          let myStyle=document.createElement('style');//创建了一个空style标签
          myScript.setAttribute('type','text/css');
          myStyle.innerHTML='body{background-color: aquamarine;}';//设置标签内容
          document.getElementsByTagName('head')[0].appendChild(myStyle);
      </script>
```



**insert插入到前面**

```javascript
          let ee=document.getElementById('ee');
          let js=document.getElementById('js');
          let list=document.getElementById('list');
          //要包含的节点 insertBefore(newNode,targetNode)
          list.insertBefore(js,ee);
```



# 操作表单（验证）

> 表单是什么  form  DOM树

- 文本框  text
- 下拉框  select
- 单选框   radio
- 多选框   checkbox
- 隐藏域  hidden
- 密码框  password
- ……

表单目的：提交信息



> 获得要提交的信息

```html
  <form method="post">
      <p>
          <span>用户名：</span><input type="text" id="username">
      </p>
      <p>
          <span>性别：</span>
          <input type="radio" name="sex" value="man" id="man_radio">男
          <input type="radio" name="sex" value="women" id="women_radio">女
      </p>
  </form>
  <script>
      let username=document.getElementById('username');//得到输入框的值，修改
      //对于单选框和多选框等固定值，.value只能取到当前的值
      //只能通过查看返回结果是为true
      let man_radio=document.getElementById('man_radio');
      let women_radio=document.getElementById('women_radio');
      if(man_radio.checked){

      }
      women_radio.checked=false;//清空

  </script>
```



> 提交表单并验证

初级html验证：required  placeholder

> MD5加密

导入MD5工具类

```html
 <script src="https://cdn.bootcss.com/blueimp-md5/2.10.0/js/md5.min.js"></script>
```

```javascript
         function check(){
            let username=document.getElementById('username');
            let password=document.getElementById('password');
            console.log(username.value);
            //MD5加密算法
             password.value=md5(password.value);
             console.log(password.value);

         }
```

在MD5基础上在进行隐藏



> 表单绑定提交事件,MD5加密密码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="https://cdn.bootcss.com/blueimp-md5/2.10.0/js/md5.min.js"></script>
</head>
<body>
<!--    表单绑定提交事件
      onsubmit绑定一个提交的函数  true false
      将结果返回表单 return接收
-->
    <form action="https://www.bilibili.com/" method="get" onsubmit="return check()">
        <p>
            <label>用户名:</label><input type="text" id="username" name="username">
        </p>
        <p>
            <label>密码:</label><input type="password" id="password">
        </p>
        <!-- 密码安全性另一种实现方式  通过隐藏域提交对输入无影响，否则会将密码变长使用户体验性变差-->
        <input type="hidden" id="md5-password" name="password">
        <!--绑定点击事件onclick-->
        <button type="submit">提交</button>
    </form>
    <script>
         function check(){
            let username=document.getElementById('username');
            let password=document.getElementById('password');
             let md5Password=document.getElementById('md5-password');
              //password.value=md5(password.value);
            md5Password.value=md5(password.value);

            //MD5加密算法
            //password.value=md5(password.value);

            //可以进行表单判定，true就是通过
             return true;//不提交
         }
    </script>
</body>
</html>
```



# jQuery

> jQuery和JavaScript的关系

jQuery是一个库，工具类，封装了大量的JavaScript函数

> 导入jQuery

1. 导入官方js
2. 导入在线cdn

```html
 <script src="http://code.jquery.com/jquery-2.1.1.min.js"></script>
```

## jQuery公式

> 公式：$(selector).action()

```html
   <a href="" id="test-jquery">点击</a>
   <script>
         /*
         以前方法：
         let id=document.getElementById('test-jquery');
         id.click()
         * */

        /*
         cdn方法：选择器就是css选择器
        * */

        $('#test-jquery').click(function (){
            alert('hello!');
        });
   </script>
```



## jQuery选择器

> 文档工具网站 (https://jquery.cuishifeng.cn/index.html)

```html
    <script>
        //原生js，选择器少，还不好记
        //标签选择器
        document.getElementsByTagName();
        //id选择器
        document.getElementById();
        //class类选择器
        document.getElementsByClassName();

        //jQuery  css中的选择器全部都能用
        $('p').click();//标签选择器
        $('#id1').click();//id选择器
        $('.class1').click();//class类选择器


    </script>
```



## jQuery事件

鼠标事件，键盘事件，其他事件

<img src="https://i.loli.net/2021/05/20/NjFZYgT3pXPueyw.png" alt="QQ截图20210503122418" style="zoom:67%;float:left" />

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="http://code.jquery.com/jquery-2.1.1.min.js"></script>
    <style>
        #divMove{
            width: 500px;
            height: 300px;
            border: 2px solid chartreuse;
        }
    </style>
</head>
<body>
<!--获取鼠标当前的一个坐标-->
   <label>mouse:</label>
   <span id="coordinate"></span>
   <div id="divMove">
       移动鼠标试一试
   </div>
   <script>
        //当网页元素加载完毕后响应事件
        $(function (){
            $('#divMove').mousemove(function (e){
                $('#coordinate').text('x:'+e.pageX+'  y:'+e.pageY);
            });
        });
   </script>
</body>
</html>
```



## jQuery操作Dom元素

```javascript
       $('#test-ul li[name=py]').text();//无参数是取值

       $('#test-ul li[name=py]').text('123');//有参数是设置

       $('#test-ul li[name=py]').html();//无参数是取值

       $('#test-ul li[name=py]').html('<strong>123</strong>');//有参数是设置
```

css操作：

```javascript
 $('#test-ul li[name=py]').css("color","red");
```

元素的显示和隐藏：本质：display：none

```javascript
       $('#test-ul li[name=py]').show();
       $('#test-ul li[name=py]').hide();
```



未来ajax()~

```javascript
$('form').ajax();
$.ajax({ url: "test.html", context: document.body, success: function(){
    $(this).addClass("done");
}});
```



# 总结



> 前端技巧

1. 如何巩固JS(看jQuery源码，看游戏源码)
2. 巩固HTML，CSS（扒网站）



Layer弹窗组件

Element-ui