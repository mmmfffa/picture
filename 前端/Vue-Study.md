

[我的工作台 - Gitee.com](https://gitee.com/ma-fu/dashboard/projects)

# 回顾SSM

<img src="https://i.loli.net/2021/05/20/jBaHwNdMniFfzuh.png" alt="思维导图1" style="zoom: 67%;float:left" />

# 前端核心分析

## Vue概述

Vue：前端体系，前后端分离

Vue.js是一套构建用户界面的渐进式[JavaScript](https://baike.baidu.com/item/JavaScript/321142)框架。与其他重量级框架不同的是，Vue采用自底向上增量开发的设计。Vue 的核心库只关注视图层，并且非常容易学习，非常容易与其它库或已有项目整合。另一方面，Vue 完全有能力驱动采用单文件组件和Vue生态系统支持的库开发的复杂单页应用。



视图层：HTML+CSS+JS  给用户看，刷新后台数据

网络通信：axios

页面跳转：Vue-router

状态管理：Vuex

VueUI：飞冰



ES6规范通过webpack打包成ES5支持



> 前端为主的MV*模式

- MVC(同步通信为主)：Model,View,Controller
- MVP(异步通信为主):   Model,View,Presenter
- MVVM(异步通信为主): Model,View,ViewModel



> NodeJS带来全栈时代

# 第一个Vue程序

MVVM

前后端数据通过ViewModel绑定，虚拟化Dom概念

> MVVM模式实现者

- Model：模型层，在这里表示JavaScript对象
- View：视图层，在这里表示DOM(HTMl)操作对象
- ViewModel：连接视图层和数据的中间组件，Vue.js就是MVVM中ViewModel层的实现者

在MVVM架构中是不允许数据和视图直接通信的只能通过ViewModel来通信，而ViewModel就是定义了一个Observer观察者。

- ViewModel能够观察数据的变化并对视图内容进行更新
- ViewModel能够监听到视图的变化，并能够通知数据发生改变

Vue.js的核心就是实现DOM监听和数据绑定



Vscode

Hubilder

Sublime

WebStrom



IDEA:插件 Vue



## MVVM

> 为什么要使用MVVM？

MVVM模式和MVC模式一样，主要目的是分离视图(View)和模式(Model)

有几大好处：

- 低耦合：视图可以独立于Model变化和修改，一个ViewModel可以绑定不同的View上，当View变化时候Model不变，当Model变化时View也可以不变。
- 可复用：你可以把一些视图逻辑放在一个ViewModel里面，让很多View重用这段视图逻辑。
- 独立开发：开发人员可以专注于业务逻辑和数据的开发(ViewModel)，设计人员可以专注于页面设计。
- 可测试：界面素来是比较难于测试的，而现在测试可以只针对ViewModel来写。



<img src="https://i.loli.net/2021/05/20/ROEbl6iVUpuhCqk.png" alt="QQ截图20210506100115" style="zoom: 80%;float:left" />



> 第一个Vue程序

```html
<body>
<!--  view层  模板-->
    <div id="app">
        {{message}}
    </div>
<!--  导入vue.js-->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
<!--   vm:对象  el:元素  data:数据  -->
        let vm=new Vue({
            el:"#app",
            //Model：data
            data:{
                message:"hello,Vue!"
            }
        });
    //ViewModel:通过vm.message动态双向绑定更新值
    </script>
</body>
```



## Vue基本语法

Vue常用7个属性：el,data,template,methods,render,computed,watch

> 导入Vue.js

```html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```



> V-bind

我们已经成功创建第一个Vue应用！看起来这跟渲染一个字符串模板非常相似，但是Vue在背后做了大量工作。现在数据和DOM已经被建立关联，所有东西都是响应式对的。我们在控制台操作对象属性，界面可以时实更新。

我们还可以使用v-bind来绑定元素特性！

```html
        <span v-bind:title="message">
            鼠标悬停几秒钟查看此处动态绑定的提示信息！
        </span>
```



v-bind等被称为指令。指令带有前缀v-，以表示他们是Vue提供的特殊属性。他们会在渲染DOM上引用特殊的响应式行为。此处的意思是：将这个节点的Title属性和Vue实例的message属性保持一致。



判断-循环

> v-if  ,v-else

```html
<div id="app">
    <h1 v-if="ok">Yes</h1>
    <h1 v-else>No</h1>
</div>
<script>
    let vm=new Vue({
        el:"#app",
        data:{
            ok: true
        }
    });
</script>
```



```html
<div id="app">
    <h1 v-if="type==='A'">A</h1>
    <h1 v-else-if="type==='B'">B</h1>
    <h1 v-else>C</h1>
</div>
<script>
    let vm=new Vue({
        el:"#app",
        data:{
            type:'A'
        }
    });
</script>
```



> 循环

```html
<div id="app">
    <ul>
        <li v-for="item in items">
            {{item.message}}
        </li>
    </ul>
</div>
<script>
    let vm=new Vue({
        el:"#app",
        data:{
        //数组用[]表示，对象用{}
            items:[
                {message:'mafu学Java'},
                {message:'mafu学Vue'}
            ]
        }
    });
</script>
```



> 事件  v-on

可以用v-on指令监听DOM事件，并在触发时运行一些JavaScript代码。

```html
<div id="app">
    <button v-on:click="sayHello">点击</button>
</div>
<script>
<!--    Vue有七大属性  有事件就有方法：method-->
    let vm=new Vue({
        el: "#app",
        data: {
            message:"mafu!"
        },
        methods: {//方法必须定义在Vue的Method属性中 v-on:事件 监听
            sayHello: function (){//this指向vm这个对象
                alert(this.message);
            }
        }
    });
</script>
```

# Vue双向绑定

## 什么是双向绑定？

Vue.js是一个MVVM框架，即数据双向绑定，即当数据发生变化时候，视图也发生变化，当视图发生变化时数据也同步变化，这也是Vue.js的精髓之处。

值得注意的是我们所说的数据双向绑定，一定是对于UI控件来说的，非UI控件不会涉及到数据双向绑定。单向数据绑定是使用状态管理工具的前提。如果我们输赢VueX，那么数据流也是单向的，这时就会和双向数据绑定冲突。

## 为什么要实现数据双向绑定？

在Vue.js中，如果使用VueX实际上数据还是单向的，之所以说数据是双向绑定，这是用的UI控件来说的，对于我们处理表单，Vue.js双向数据绑定用起来就非常舒服了。即两者并不排斥，在全局性数据流中使用单向，方便跟踪；局部性数据流使用双向，简单操作。



## v-model

> text框：

```html
<div id="app">
    输入的文本：<input type="text" v-model="message"> {{message}}
</div>
<script>
    <!--    Vue有七大属性  有事件就有方法：method-->
    let vm=new Vue({
        el: "#app",
        data: {
            message: "123"
        }
    });
</script>
```

> radio单选框：

```html
<div id="app">
<!--    输入的文本：<input type="text" v-model="message"> {{message}}-->
       <label>性别：</label>
       <input type="radio" name="sex" value="man" v-model="checked"> 男
       <input type="radio" name="sex" value="women" v-model="checked"> 女
       <p>
           选中了谁：{{checked}}
       </p>

</div>
<script>
    <!--    Vue有七大属性  有事件就有方法：method-->
    let vm=new Vue({
        el: "#app",
        data: {
            checked:false
        }
    });
</script>
```

> select下拉框:

```html
<div id="app">
     下拉框：
      <select v-model="selected">
          <option value="" disabled>--请选择--</option>
          <option>凤山</option>
          <option>英桥</option>
          <option>文地</option>
      </select>
      <p>
          选中：{{selected}}
      </p>
</div>
<script>
    <!--    Vue有七大属性  有事件就有方法：method-->
    let vm=new Vue({
        el: "#app",
        data: {
            selected:''
        }
    });
</script>
```

# Vue组件讲解

## 什么是组件

组件是可复用的Vue实例，说白了就是一组可以重复使用的模板，跟JSTL的自定义标签、Thymeleaf的th：fragment等框架有异曲同工之妙。通常一个应用会以一颗嵌套的组件树的形式来组织。

<img src="https://i.loli.net/2021/05/20/Cdcom86BjlRDz7G.png" alt="QQ截图20210506113426" style="zoom:67%;float:left" />

## 第一个Vue组件

注意：在实际开发中并不会使用一下方式开发组件，而是采用vue-cli创建.vue模板文件的开发方式，以下方法只是为让大家理解什么是组件。

使用Vue.component()方法注册组件，格式：

```javascript
    //定义一个Vue组件component
    Vue.component("mf",{
        template:'<li>hello</li>'
    });
```



> 组件绑定然后props接收参数

```html
<div id="app">
<!--    组件：传递给组件中的值：需要先绑定然后用props接收参数-->
       <mf v-for="item in items" v-bind:item="item"></mf>
</div>
<script>
    //定义一个Vue组件component
    Vue.component("mf",{
        props: ['item'],
        template:'<li>{{item}}</li>'
    });
    let vm=new Vue({
        el: "#app",
        data: {
            items: ["java","linux","c++"]
        }
    });
</script>
```

# Axios异步通信

网络通信：

- jQuery.ajax()
- Axios

## 什么是Axios

Axios是一个开源的可以用在浏览器端和NodeJS的异步通信框架，它的主要作用是实现AJAX异步通信，其功能特点如下：

- 从浏览器中创建XMLHttpRequests
- 从node.js创建http请求
- 支持PromiseAPI [JS中链式编程]
- 拦截请求和响应
- 转换请求数据和响应数据
- 取消请求
- 自动转换JSON数据
- 客户端支持防御XSRF(跨站请求伪造)



## 为什么实用Axios

由于Vue.js是一个视图层框架，并且作者严格遵守Soc(关注度分离原则)，所以Vue.js并不包含AJAX通信的功能，为了解决通信功能，作者单独开发了一个名为vue-resource的插件，不过在进入2.0版本后停止了对该插件的维护并推荐Axios框架。少用jQuery因为它操作Dom太频繁！



## 第一个Axios程序

> 导入Axios CDN

```html
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```



> Vue声明周期

Vue实例有一个完整的生命周期，就也是从开始创建，初始化数据，编译模板，挂载DOM，渲染，更新，渲染，卸载等一系列过程，我们称之为Vue的生命周期。通俗说就是Vue实例从创建到销毁的过程就是生命周期。

在整个Vue生命周期中，它提供了一系列的事件，可以让我们在事件触发时注册JS方法，可以让我们用自己注册的方法控制整个大局，在这些事件响应方法中的this直接指向的是Vue的实例。



```html
<!DOCTYPE html>
<!--suppress JSValidateTypes -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<!--  v-clock解决闪烁问题-->
    <style>
        [v-clock]{
            display: none;
        }
    </style>
</head>
<body>

        <div id="vue" v-clock>
            <div>{{info.name}}</div>
            <div>{{info.address.city}}</div>

            <a v-bind:href="info.url">kuangShengXue</a>
        </div>



        <!--导入JS文件-->
        <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
        <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
        <script>
            let vm=new Vue({
                el: '#vue',
                //data:属性 vm
                data(){
                    return{
                        //请求的返回参数格式必须和JSON字符串格式一样
                        info:{
                            name:null,
                            address:{
                                street:null,
                                city:null,
                                country:null
                            },
                            url:null
                        }
                    }
                },
                mounted(){//钩子函数 链式编程   es6新特性
                    axios.get('../data.json').then(response=>(this.info=response.data));
                }
            });
        </script>

</body>
</html>
```

# 计算属性

> 计算属性、内容分发、自定义事件

## 什么是计算属性

计算属性是Vue的特色：计算出来的结果保存在属性中。运行在内存：虚拟DOM

计算属性的重点突出在**属性**两个字上，首先它是个属性其次这个属性有计算的能力，这里的计算就是这个函数；简单点说，他就是一个能够将计算结果缓存起来的属性(将行为转化成了静态的属性)，仅此而已：可以想象为缓存！

```html
  <div id="app">
         <p>currentTime1:{{currentTime1()}}</p>
         <p>currentTime2:{{currentTime2}}</p>
    </div>

    <!--导入JS文件-->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        let vm=new Vue({
            el: '#app',
            data: {
                message:'hello,mf'
            },
            methods: {
                currentTime1:function (){
                    return Date.now();//返回一个时间戳
                }
            },
            computed: {//Vue特色：计算属性  methods和computed中的方法名不能重名，重名之后只会调用methods方法
                currentTime2:function (){
                    this.message;//只有this当中的属性变化时才会重新计算
                    return Date.now();//返回一个时间戳
                }
            }
        });
    </script>
```

<img src="https://i.loli.net/2021/05/20/P3yaY8z2914nRG7.png" alt="QQ截图20210506205334" style="zoom:67%;float:left" />



> 结论

调用方法时，每次都需要进行计算，既然有计算过程则必须产生系统开销，那如果这个结果不是经常变化呢？此时就可以考虑将这个结果缓存起来以节约系统开销。

# 插槽slot

> 内容分发

在Vue.js中我们使用<slot>元素作为承载分发内容的出口，作者成为插槽，可以应用在组合组件的场景中。

```html
<!--简写 v-bind: 简写为：  v-on:简写为@-->
    <div id="app">
        <todo></todo>
        <todo-title slot="todo-title" :title="title"></todo-title>
        <todo-items slot="todo-items" v-for="item in todoItems" :item="item"></todo-items>
    </div>
```



```html
<!--导入JS文件-->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        //后面加个反斜杠，表示换行
        //slot:插槽，插数据
        Vue.component('todo',{
            template: '<div>\
                          <slot name="todo-title"></slot>\
                          <ul>\
                             <slot name="todo-items"></slot>\
                          </ul>\
                        </div>'
        });
        Vue.component('todo-title',{
            props:['title'],
           template: '<div>{{title}}</div>'
        });
        Vue.component('todo-items',{
            props: ['item'],
            template: '<li>{{item}}</li>'
        });

        let vm=new Vue({
            el: '#app',
            data: {
                title: '神雕侠侣',
                todoItems: ['杨过','郭靖','黄蓉']
            }

        });
    </script>
```



# 自定义事件内容分发

> 自定义事件

通过写代码前分析发现，数据项在Vue的实例中，但删除操作要在组件中完成，那么组件如何才能删除vue实例中的数据呢？此时就涉及到参数传递与事件分发了，Vue为我们提供了自定义事件的功能很好的帮助我们解决了这个问题，使用this.$emit('自定义事件名',参数)

<img src="https://i.loli.net/2021/05/20/nMyYfG3FkCR1Ngj.png" alt="QQ截图20210507092834" style="zoom:80%;float:left" />

> 前端四要素

- 基础语法
- 条件判断if for
- 网络通信：axios
- 组件以及页面布局

Vue单页面应用

```html
<!--简写 v-bind: 简写为：  v-on:简写为@-->
    <div id="app">
        <todo></todo>
        <todo-title slot="todo-title" :title="title"></todo-title>
        <todo-items slot="todo-items" v-for="(item,index) in todoItems"
                    :item="item" :index="index" @remove="removeItem(index)" :key="index"></todo-items>
    </div>

    <!--导入JS文件-->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        //后面加个反斜杠，表示换行
        //slot:插槽，插数据
        Vue.component('todo',{
            template: '<div>\
                          <slot name="todo-title"></slot>\
                          <ul>\
                             <slot name="todo-items"></slot>\
                          </ul>\
                        </div>'
        });
        Vue.component('todo-title',{
            props:['title'],
           template: '<div>{{title}}</div>'
        });
        Vue.component('todo-items',{
            props: ['item','index'],
            //只能绑定当前组件的方法
            template: '<li>{{index}}===={{item}} <button @click="remove">delete</button></li>',
            methods: {
                remove: function (index){
                    //this.$emit自定义事件分发
                    this.$emit('remove',index);
                }
            }
        });

        let vm=new Vue({
            el: '#app',
            data: {
                title: '神雕侠侣',
                todoItems: ['杨过','郭靖','黄蓉']
            },
            methods: {
                //操作数组万能方法：splice
                removeItem: function (index){
                    console.log("删除了=》"+this.todoItems[index]);
                    this.todoItems.splice(index,1);//一次只移除一个元素
                }
            }
        });
    </script>
```

# Vue小结

> 核心

数据驱动，组件化

优点：借鉴了AngulaJS的模板化开发和React的虚拟Dom，虚拟Dom就是将Dom操作放到内存中运行；

> 常用属性

- v-if
- v-else-if
- v-else
- v-for
- v-on 绑定事件，简写@
- v-model 数据双向绑定
- v-bind 给组件绑定参数,简写:

> 组件化

- 组合组件slot插槽
- 组件内部绑定事件需要使用到this.$emit('事件名'，参数)
- 计算属性的特色，缓存计算数据

遵循SOC关注度分离原则，Vue是唇齿的视图框架并不包含比如AJAX之类的通信功能，为了解决同行问题，我们需要使用Axios框架做异步通信。

> 说明

Vue的开发都是基于NodeJS，实际开发采用vue-cli脚手架开发，vue-router做路由，vue-x做状态管理，vue UI界面我们一般使用ElemenUI(饿了么出品)，或者是ICE(阿里巴巴出品),来快速搭建前端项目。

# 第一个Vue-cli程序

## 什么是Vue-cli

vue-cli官方提供的一个脚手架，用于快速生成一个Vue的项目模板；

预先定义好的目录结构及基础代码，就好比我们在创建Maven项目时可以选择创建一个骨架项目，这个骨架项目就是脚手架，使我们的开发更加的快速。

> 主要的功能

- 统一的目录结构
- 本地调试
- 热部署
- 单元测试
- 集成打包上线

vue初始化一个webpack项目

```tex
vue init webpack myvue
```

一路选择No即可

> 初始化并运行

```tex
cd myvue
npm install
npm run dev
```

执行完后，目录多了很多依赖

# Webpack

## 什么是Webpack

本质上，webpack是一个现代JavaScript应用程序的静态模块打包器。当webpack处理应用程序时，它会递归地构建一个依赖关系图(dependency graph),其中包含应用程序的每个模块，然后将所有模块打包成一个或者多个bundle。

Webpack是当下最热门的前端资源模块化管理和打包工具，它可以将许多松散耦合的模块

按照依赖和规则打包成符合生产环境部署的前端资源。还可以将按需加载的模块进行代码分离，等到需要时再异步加载。通过loader转换，任何形式的资源都可以当做模块，比如CommonsJS，AMD，ES6，CSS，JSON，CoffeeScript，LESS；

现在越来越多的网站已经从网页模式进化到了WebAPP模式。它们运行在现代浏览器里，使用HTML5，CSS3，ES6等新技术来开发丰富的功能，网页已经不仅是完成浏览器的基本请求；WebAPP通常是一个SPA(单页面应用)，每一个视图通过异步加载的方式加载，这导致页面初始化和使用过程中会加载越来越多的JS代码，这给前端的开发流程和资源组织带来了巨大挑战。

前端开发和其他开发工作的主要区别，首先是前端基于多语言，多层次的编码和组织工作，其次前端产品的交付是基于浏览器的，这些资源是通过增量加载的方式运行到浏览器端，如何在开发环境中组织好这些碎片化的代码和资源，并且保证他们在浏览器端快速，优雅的加载和更新，就需要一个模块化系统，这个理想中的模块化是前端工程师探索的难题。

## CommonJS规范

服务器端的NodeJS遵循CommonJS规范，该规范核心思想是允许模块通过require方法来同步加载所需其他依赖模块，然后通过exports或者module.exports来导出需要暴露的接口。

> 优点

服务器端模块便于使用

NPM中已经有超过45万个可以使用的模块包

简单易用

> 缺点

同步的模块化加载方式不适合在浏览器环境中，同步意味着阻塞加载，浏览器资源是异步加载的；

不能非阻塞的并行加载多个模块。

> 实现

服务器端的NodeJS;

Browserify,浏览器端的CommonsJS实现，可以使用NPM的模块，但是编译打包后的文件体积较大；

modules-webmake,类似Browserify,但不如Browserify灵活；

wreq,Browserify的前身；

## AMD规范

Asynchronous Module Definition规范其实主要是一个主要接口define(id?,dependences?,factory);它要在声明模块的时候指定所有的依赖dependencies,并且还要当做形参传到factory中，对于依赖的模块提前执行。

> 优点

适合在浏览器环境中异步加载模块；

可以并行加载多个模块。

> 缺点

提高了开发成本，代码的阅读和书写比较困难，模块定义方式语义不畅；

不符合通用的模块化思维方式，是一种妥协的实现。

> 实现

RequireJS

curl

## CMD规范

Commons Module Definition规范和AMD很相似，尽量保持简单，并与CommonJS和NodeJS和Modules规范保持了很大的兼容性。

> 优点

依赖就近，延迟执行

可以很容易在NodeJS中运行

> 缺点

依赖SPM打包，模板的加载逻辑偏重

> 实现

Sea.js

Coolie

## ES6规范

EcmaScript6标准增加JavaScript语言层面的模块体系定义。ES6模块的设计思想，是尽量静态化，使编译时就能确定模块的依赖关系，以及输入和输出的变量。CommonsJS和AMD模块，都只能在运行时确定这些东西。

> 优点

容易进行静态分析

面向未来的EcmaScript标准

> 缺点

原生浏览器端还没有实现该标准

全新的命令，，新版的NodeJS才支持

> 实现

Babel



> 大家期望的模块系统

可以兼容多种模块风格，尽量可以利用已有的代码，不仅仅只是JavaScript模块化，还有CSS，图片，字体的等资源也需要模块化。



## Webpack安装

Webpack是一款模块加载器打包工具，它能吧各种资源，如JS，JSX,ES6,SASS,LESS,图片等都作为模块来处理和使用。

安装：

```tex
npm install webpack -g
npm install webpack-cli -g
```

测试：

```tex
webpack -v
webpack-cli -v
```

## 配置

创建webpack.config,js配置文件

- entry:入口文件，指定WebPack用哪个文件作为项目的入口；
- output:输出，指定WebPack把处理完的文件放置到指定路径；
- module:模块，用于处理各种类型的文件；
- plugins:插件，如热更新，代码重用等；
- resolve:设置路径指向；
- watch：监听，用于设置文件改动后直接打包。

# 使用webpack

1. 创建项目；
2. 创建modules目录，用于放置JS模块等资源文件；
3. 在modules下创建模块文件，如hello.js,用难于编写JS模块相关代码；
4. 在modules下创建一个名为main.js的入口文件，用于打包时设置entry属性；
5. 在项目目录下创建webpack.config.js配置文件，使用webpack命令打包；

> 项目结构图

<img src="https://i.loli.net/2021/05/20/iCNQDwaIM985gYq.png" alt="1" style="zoom:67%;float:left" />

只需要最后在html文件中引入打包好的bundles.js:

```html
<!--前端的模块化开发-->
<script src="dist/js/bundle.js"></script>
```

# vue-router路由

> 说明

Vue Router是Vue.js官方的路由管理器，它和Vue.js的核心深度集成，让构建单页面应用变得易如反掌。

包含的功能：

- 嵌套的路由/视图表
- 模块化的，基于组件的路由配置
- 路由参数，查询，通配符
- 基于Vue.js过度系统的视图过度效果
- 细粒度的导航控制
- 带有自动激活的CSS class的连接
- HTML5 历史模式或hash模式，在IE9中自动降级
- 自定义的滚动条行为

> 安装

在当前项目下

```tex
npm install vue-router --save-dev
```

报错就用cnpm



> 测试

1. 删除没用的东西
2. components目录下存放我们自己编写的组件
3. 定义一个Content.vue组件

```vue
<template>
   <h1>内容页</h1>
</template>

<script>
export default {
  name: "content"
}
</script>

<style scoped>

</style>

```

4. 安装路由，在src目录下，新建一个文件夹:router，专门存放路由。main.js入口导入路由

```js
import Vue from 'vue';
import VueRouter from "vue-router";
import content from "../components/content";
import Main from "../components/Main";
//安装路由
Vue.use(VueRouter);

//配置导出路由
export default new VueRouter({
  routes: [
    {
      //路由路径
      path: '/content',
      name: 'content',
      //跳转的组件
      component: content
    },
    {
      //路由路径
      path: '/Main',
      name: 'Main',
      //跳转的组件
      component: Main
    }
  ]
});

```

5. 配置路由

```js
import Vue from 'vue';
import App from './App';
import router from './router';//自动扫描里面的路由配置


Vue.config.productionTip = false

new Vue({
  el: '#app',
  //配置路由
  router,
  components: { App },
  template: '<App/>'
})

```

6. APP.vue中使用路由

```vue
<template>
  <div id="app">
     <h1>Vue-Router</h1>
     <router-link to="/Main">首页</router-link>
     <router-link to="/content">内容页</router-link>
     <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App',
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

```

# vue+elementUI

## 创建工程

1. 管理员模式命令行下创建hello-vue工程，vue init webpack hello-vue
2. 安装依赖，我们需要安装vue-router,element-ui,sass-loader,node-sass四个插件

```tex
cd 目录
npm install vue-router --save-dev
npm i element-ui -S
npm  install
cnpm install sass-loader node-sass --save-dev
npm run dev
```

> npm命令解释

- npm install moduleName:安装到模块目录下
- npm install -g moduleName：-g 的意思是将模块安装到全局，具体安装到磁盘的那个位子，要看npm config prefix的位置
- npm install -save  moduleNmae:--save的意思是将模块安装到项目目录下，并在package文件的dependencies节点写入依赖，-S为该命令的缩写
- npm install -save-dev moduleName:-save-dev的意思是将模块安装到项目目录下，并在package文件的devDependencies节点写入依赖，-D为该命令的缩写

打开local host测试成功！

## 创建登录页面

将没有用的初始化东西删掉！

在源码目录下创建如下结构

- assets:存放资源文件
- Components:存放Vue功能组件
- views：存放视图组件
- router：存放vue-router配置

Main.vue

```vue
<template>
   <h1>首页</h1>
</template>

<script>
export default {
  name: "Main"
}
</script>

<style scoped>

</style>

```

Login.vue

从ElementUI复制模板

```vue
<template>
  <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
    <el-form-item label="密码" prop="pass">
      <el-input type="password" v-model="ruleForm.pass" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="确认密码" prop="checkPass">
      <el-input type="password" v-model="ruleForm.checkPass" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="年龄" prop="age">
      <el-input v-model.number="ruleForm.age"></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
      <el-button @click="resetForm('ruleForm')">重置</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  name: "Login",
  data() {
    let checkAge = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('年龄不能为空'));
      }
      setTimeout(() => {
        if (!Number.isInteger(value)) {
          callback(new Error('请输入数字值'));
        } else {
          if (value < 18) {
            callback(new Error('必须年满18岁'));
          } else {
            callback();
          }
        }
      }, 1000);
    };
    let validatePass = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('请输入密码'));
      } else {
        if (this.ruleForm.checkPass !== '') {
          this.$refs.ruleForm.validateField('checkPass');
        }
        callback();
      }
    };
    let validatePass2 = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('请再次输入密码'));
      } else if (value !== this.ruleForm.pass) {
        callback(new Error('两次输入密码不一致!'));
      } else {
        callback();
      }
    };
    return {
      ruleForm: {
        pass: '',
        checkPass: '',
        age: ''
      },
      rules: {
        pass: [
          { validator: validatePass, trigger: 'blur' }
        ],
        checkPass: [
          { validator: validatePass2, trigger: 'blur' }
        ],
        age: [
          { validator: checkAge, trigger: 'blur' }
        ]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          // alert('submit!');
          this.$router.push('Main');
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
}
</script>

<style scoped>

</style>

```

路由配置index.js

```js
import Vue from 'vue';
import VueRouter from "vue-router";

import Main from "../views/Main";
import Login from "../views/Login";
Vue.use(VueRouter);
export default new VueRouter({
    routes:[
      {
        path: '/Main',
        name: Main,
        component: Main
      },
      {
        path: '/Login',
        name: Login,
        component: Login
      }
    ]
});

```

入口main.js

```js
import Vue from 'vue';
import App from './App';
import router from './router';
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';

Vue.config.productionTip = false
Vue.use(router);
Vue.use(ElementUI);
new Vue({
   el: '#app',
   router,
   render: h => h(App)//ElementUI
})

```

App.vue

```vue
<template>
  <div id="app">
     <router-view></router-view>
  </div>
</template>

<script>


export default {
  name: 'App',

}
</script>
```



# 嵌套路由

嵌套路由又称子路由，通常由多层嵌套的组件组合而成。同样地，URL中各段动态路径也按某种结构对应嵌套各层组件；

```js
{
        path: '/Main',
        name: Main,
        component: Main,//嵌套路由
        children: [
          {
            path: '/user/Profile',
            name: userProfile,
            component: userProfile
          },
          {
            path: '/user/List',
            name: userList,
            component: userList
          }
        ]
      },
```

Main.vue

```vue
<template>
  <el-row class="tac">
    <el-col :span="12">
      <h5>默认颜色</h5>
      <el-menu

        default-active="2"
        class="el-menu-vertical-demo"
        @open="handleOpen"
        @close="handleClose">

        <el-submenu index="1">

          <template #title>
            <i class="el-icon-location"></i>
            <span>导航一</span>
          </template>

          <el-menu-item-group>
            <template #title>分组一</template>
            <el-menu-item index="1-1">选项1</el-menu-item>
            <el-menu-item index="1-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="1-3">选项3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="1-4">
            <template #title>选项4</template>
            <el-menu-item index="1-4-1">选项1</el-menu-item>
          </el-submenu>

        </el-submenu>

        <el-menu-item index="2">
          <i class="el-icon-menu"></i>
          <template #title>导航二</template>
        </el-menu-item>
        <el-menu-item index="3" disabled>
          <i class="el-icon-document"></i>
          <template #title>导航三</template>
        </el-menu-item>
        <el-menu-item index="4">
          <i class="el-icon-setting"></i>
          <template #title>导航四</template>
        </el-menu-item>
      </el-menu>
    </el-col>
    <el-col :span="12">
      <h5>自定义颜色</h5>
      <el-menu
        :uniqueOpened="true"
        default-active="2"
        class="el-menu-vertical-demo"
        @open="handleOpen"
        @close="handleClose"
        background-color="#545c64"
        text-color="#fff"
        active-text-color="#ffd04b">
        <el-submenu index="1">
          <template #title>
            <i class="el-icon-location"></i>
            <span>导航一</span>
          </template>
          <el-menu-item-group>
            <template #title>分组一</template>
            <el-menu-item index="1-1">选项1</el-menu-item>
            <el-menu-item index="1-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="1-3">选项3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="1-4">
            <template #title>选项4</template>
            <el-menu-item index="1-4-1">选项1</el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-menu-item index="2">
          <i class="el-icon-menu"></i>
          <template #title>导航二</template>
        </el-menu-item>
        <el-menu-item index="3" disabled>
          <i class="el-icon-document"></i>
          <template #title>导航三</template>
        </el-menu-item>
        <el-menu-item index="4">
          <i class="el-icon-setting"></i>
          <template #title>导航四</template>
        </el-menu-item>
        <el-submenu index="5">
          <template #title>
            <i class="el-icon-location"></i>
            <span>导航一</span>
          </template>
          <el-menu-item-group>
            <template #title>分组一</template>
            <el-menu-item index="5-1">选项1</el-menu-item>
            <el-menu-item index="5-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="5-3">选项3</el-menu-item>
          </el-menu-item-group>
        </el-submenu>
      </el-menu>
    </el-col>
  </el-row>
</template>

<script>
export default {
  name: "Main",
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    }
  }
}
</script>

<style>

</style>

```

# 参数传递及重定向

## 参数传递

```vue
<!--name：传组件名 params：传递参数，需要绑定对象：v-bind-->
<router-link v-bind:to="{name: 'UserProfile', params: {id: 1}}">个人信息</router-link>
```

注意路由配置时候需要增加props占位符：

```js
        children: [
          {
            path: '/user/Profile/:id',
            name: 'userProfile',//name需要添加引号因为是字符串
            component: userProfile,
            props:true
          },
          {
            path: '/user/List',
            name: userList,
            component: userList
          }
        ]
```

前端展示：

```vue
<template>
  <div>
    <h1>个人信息</h1>
<!--    组件在没有添加props属性的情况下-->
    {{ $route.params.id }}
<!--    组件添加props属性的情况-->
    {{id}}

  </div>
</template>

<script>
export default {
  name: "userProfile",
  props:['id']
}

</script>

<style scoped>

</style>

```

## 重定向

重定向的意思大家都明白，但 Vue 中的重定向是作用在路径不同但组件相同的情况下，比如：
 在router下面index.js的配置。

```js
          {
            path: '/goHome',
            redirect: '/Main'
          }
```

```vue
              <el-menu-item index="1-3">
                <router-link to="/goHome">回到首页</router-link>
              </el-menu-item>
```

# 404和路由钩子

## 回顾

首页显示用户名：

Login.vue

```vue
 this.$router.push('/Main/'+this.ruleForm.username);
```

index.js

```js
        path: '/Main/:username',
        name: Main,
        component: Main,//嵌套路由
        props: true,
```

Main.vue

```vue
export default {
  name: "Main",
  props: ['username']
}
```

```vue
      <el-container>
        <el-header style="text-align: right;font-size: 12px">
          <el-dropdown>
            <i class="el-icon-setting" style="margin-right: 15px"></i>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>个人信息</el-dropdown-item>
              <el-dropdown-item>退出登录</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <span>{{username}}</span>
        </el-header>

        <el-main>
          <router-view></router-view>
        </el-main>

      </el-container>
```

## 路由模式

> 两种

- hash：路径带#符号，
- history：路径不带#符号

index.js

```vue
mode: 'history',
```

## 404

NotFound.vue

index.js

```js
      {
        path: '*',
        name: 'NotFound',
        component: NotFound
      }
```

## 路由钩子和异步请求

beforeRouteEnter：在进入路由之前执行

beforeRouteLeave ：在离开路由之前执行

```vue
<script>
export default {
  name: "userProfile",
  props:['id'],
  //拦截器  chain
  beforeRouteEnter:(to, from, next)=>{
     console.log("进入路由前");
     next();
  },
  beforeRouteLeave:(to, from, next) =>{
     console.log("进入路由后");
     next();
  }
}

</script>
```

> 参数说明

to:路由将要跳转的路径信息

from:路径跳转前的路径信息

next:路由的控制参数

​      next() 跳入下一个页面

​      next('/path') 改变路由的跳转方向，使其调到另一个路由

​      next(false)  返回原来的页面

​       next((vm)=>{}) 仅在beforeRouteEnter中可用，vm是组件实例

> 在钩子函数中使用异步请求

1. 安装Axios

```tex
npm install --save axios vue-axios
或
//cnpm有可能安装失败，少用(失败时多装几次)
cnpm install axios -s
```

2. main.js引用Axios

```tex
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)
```

3. Profile.vue

```vue

<script>
export default {
  name: "userProfile",
  props:['id'],
  //拦截器  chain
  beforeRouteEnter:(to, from, next)=>{
     console.log("进入路由前");
     next(vm => {
       vm.getData();//进入之前执行此方法
     });
  },
  beforeRouteLeave:(to, from, next) =>{
     console.log("进入路由后");
     next();
  },
  methods: {
    getData:function (){
       this.axios({
         method:"get",
         url:"http://localhost:8080/static/mock/data.json"
       }).then(function (response){
         console.log(response);
    });
    }
  }

}

</script>
```

