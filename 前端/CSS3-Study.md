# CSS概述

## CSS开篇

| 前端三要素 |      |
| ---------- | ---- |
| HTML       | 结构 |
| CSS        | 表现 |
| JavaScipt  | 交互 |

1. CSS是什么

​       Cascading Style Sheet 层叠样式表；

​       字体，颜色，边距，亮度，背景图片，图片定位，网页浮动.....

2. 怎么用(快速入门)

3. **CSS选择器（重点+难点）**

    美化网页（文字，阴影，超链接，列表，渐变）

4. 盒子模型

5. 浮动

6. 定位

7. 网页动画（特效）

## CSS发展史

CSS1.0

CSS2.0  DIV（块）+CSS ,    HTML与CSS结构分离的思想，网页变得简单，利于SEO(搜索引擎优化)

CSS2.1  浮动，定位

CSS3.0 圆角，阴影，动画......浏览器兼容器

## 快速入门

```css
        <style> 可以写CSS代码 
        h1是选择器
        语法：
        选择器{
            声明1;
            声明2;
            声明3;
        }

        建议使用规范：css单独写然后用link标签导入
```

CSS优势：

1. 内容和表现分离
2. 网页结构表现统一，可以实现复用
3. 样式十分丰富
4. 建议使用独立于html的css文件
5. 利用SEO，容易被搜索引擎收录

## CSS三种导入方式

优先级：**就近原则**

1. 行内样式：在标签元素中，编写一个style属性，编写样式即可

   2.内部样式

   3.外部样式

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!-- 2.内部样式 -->
    <style>
        h1{
            color: goldenrod;
        }
    </style>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <!-- 1. 行内样式：在标签元素中，编写一个style属性，编写样式即可 -->
    <h1 style="color: aqua;">我是标题</h1>
</body>
</html>
```

```css
/* 3.外部样式 */
h1{
    color: rgb(113, 32, 218);
}

```

拓展：外部样式的两种写法

- 链接式（推荐使用）

   html

  ```html
  <link rel="stylesheet" href="css/style.css">
  ```

- 导入式

  是CSS2.1  特有的

  ```css
  <style>
      @import url("css/style.css");
  </style>
  ```

  

# 选择器

  作用：选择页面上的某一个或者某一类元素

## 基本选择器

- 标签选择器  ：选择一类标签 标签{}

- 类 选择器 class ：选择所有class属性一致的标签，跨标签，.类名{}

- id选择器： 全局唯一！ #id名{}

  

## 层次选择器

1.后代选择器   在某个元素后面，祖爷爷，爷爷，爸爸，儿子

```html
        /* 后代选择器 */
        body{
            background: rebeccapurple;
        }
```

2.子选择器   一代，儿子

```html
        /* 子选择器 */
        body>p{
            background-color: blue;
        }
```

3.相邻兄弟选择器   同辈

```html
        /* 兄弟选择器 :只有一个邻居，对下不对上*/
        .active+p{
            background: yellow;
        }
```

4.通用选择器

```html
        /* 通用选择器:当前选中元素的向下兄弟选择器 */
        .active~p{
            background: green;
        }
```

## 结构伪类选择器

伪类：条件

```css
ul li:first-child
-- 按顺序
p:nth-child(1)
-- 按类型
p:nth-of-type(2)
a:hover
```

简单

```html
/* 避免使用class和id选择器：ul的第一个子元素 和最后一个子元素*/
 /* nth-child()有可能会被父元素阻碍，比如第一个是h1就失效 */
      ul li:first-child{
          background: red;
      }
      ul li:last-child{
          background: gold;
      }
       /* 只选择p1 :定位到父元素选择当前的第一个元素并且是当前元素才会生效*/
       p:nth-child(1){
           background: gold;
       }
       /* 选择父元素里面第二个为p的元素 */
       p:nth-of-type(2){
           background: brown;
       }
```

## 属性选择器

class+id结合版  高级

```css
<style>
        /* 类选择器+后代选择器 
           float先让它浮动起来
           display让它变成块元素
           margin外边距盒子模型
           font可以设置字体样式:必填(实体，宽高，字体)
        */
         .demo a{
            float: left;
            display: block;
            width: 50px;
            height: 30px;
            border-radius: 10px;
            background: greenyellow;
            text-align: center;
            text-decoration: none;
            color: red;
            margin: 8px;
            font: bold 20px/30px Arial;
         }
         /* 属性名，属性名=属性值(正则)
            存在id属性的元素 
            正则表达式：
            =是绝对等于
            *=是通配包含这个元素
            ^=是以这个元素开头
            $=是以这个元素结尾
            属性选择器语法：a[]{} 这比id选择器更加高级
         */
         /* a[id]{
             background: yellow;
         } */
         /* a[id=first]{
             background: rgb(85, 85, 245);
         } */
         /* class中有links的元素  class有多个所以带“”*/
         /* a[class*="links"]{
             background: yellow;
         } */
         /* 选中href中以http开头的元素 */
         a[href^=http]{
             background: yellow;
         }
         a[href$=doc]{
             background: rgb(219, 184, 140);
         }
    </style>
```

```css
<p class="demo">
        <a href="http://www.baidu.com" class="links item first" id="first">1</a>
        <a href="http://www.csdn.com" class="links item active" target="_blank" title="2">2</a>
        <a href="images/123.html" class="links item">3</a>
        <a href="images/123.png" class="links item">4</a>
        <a href="images/123.jpg" class="links item">5</a>
        <a href="abc">6</a>
        <a href="/123.pdf">7</a>
        <a href="/abc.pdf">8</a>
        <a href="abc.doc" class="links item last">9</a>
    </p>
```

![QQ截图20210425152215](https://i.loli.net/2021/05/20/MmZRjsJ3gpND9T7.png)

# 美化网页元素

## 为什么要美化

1. 有效传递页面信息
2. 美化网页，页面漂亮吸引用户
3. 凸显页面主题
4. 提高用户体验



span标签：重点要突出的字  约定俗成的

## 字体样式

```css
 <!-- 
        font-family:字体(可以设置多种字体)
        font-size:字体大小
        font-weight:字体粗细
        color:字体颜色
     -->
    <style>
        body{
            font-family:"Arial", 楷体;
            color: brown;
        }
        h1{
            font-size: 50px;
        }
        .p1{
            font-weight: bold;
        }
    </style>
```

```css
    <!-- 字体：风格，粗细，大小  字体样式-->
    <style>
        p{
            font:oblique lighter 16px 楷体;
        }
    </style>
```

## 文本样式

1. 颜色  color rgb rgba   opacity透明度
2. 文本对齐方式  text-align=center水平中
3. 首行缩进  text-indent
4. 行高  line-height  单行文字上下居中 line-height=height
5. 下划线  text-decoration
6. 文本图片上下对齐：vertical-align-middle

```css
<!-- 
        颜色：单词/rgb
        rgba透明度 0~1
        text-align文本居中
        text-indent首行缩进em字
        line-height字体行高(一行的行高，达到居中效果)
     -->
    <style>
       h1{
           color: rgba(241, 77, 77,0.8);
           text-align: center;
       }
       .p1{
           text-indent: 2em;
       }
       .p2{
           background: rgb(173, 247, 64);
           height: 100px;
           /* line-height: 300px; */
           
       }
       .l1{
           /* text-decoration: underline; */
           text-decoration: line-through;
       }
    
    </style>
```

```css
    <!-- 水平对齐  上中下
        参照物，a,b
     -->
    <style>
        img,span{
           vertical-align: middle;
        }
    </style>
```

## 超链接伪类

```css
    <style>
        a{
            text-decoration: none;
            color: black;
        }
        /* 鼠标悬浮颜色 */
        /* 达到悬浮放大的效果 */
        a:hover{
            color: greenyellow;
            font-size: 30px;
        }
        /* 被激活的时候即鼠标没有释放的时候 */
        a:active{
             color: red;
             
        }
        /* 点完之后的颜色 */
        a:visited{
            color: aqua;
        }
        /* text-shadow:阴影颜色，水平偏移，垂直偏移，阴影半径 */
        #price{
            text-shadow: blue 10px 10px 1px;
        }
    </style>
```

## 列表

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <div id="nav">
        <h2 class="title">全部商品分类</h2>
        <ul>
            <li><a href="#">a1</a>&nbsp;<a href="#">a2</a>&nbsp;<a href="#">a3</a></li>
            <li><a href="#">b1</a>&nbsp;<a href="#">b2</a>&nbsp;<a href="#">b3</a></li>
            <li><a href="#">c1</a>&nbsp;<a href="#">c2</a>&nbsp;<a href="#">c3</a></li>
            <li><a href="#">d1</a>&nbsp;<a href="#">d2</a>&nbsp;<a href="#">d3</a></li>
        </ul>
    </div>

</body>
</html>
```



```css
#nav{
    width: 300px;
    background: rgb(165, 165, 162);
}
.title{
    font-size: 18px;
    font-weight: bold;
    text-indent: 1em;
    line-height: 38px;
    background: greenyellow;
}
/*  list-style: 列表的圆点或者数字样式
    circle:空心圆
    decimal:数字
*/
/* ul{
    background: rgb(165, 165, 162);
} */
ul li{
    height: 30px;
    list-style:none;
    text-indent: 1em;
}
a{
    font-size: 14px;
    color: black;
    text-decoration: none;
}
a:hover{
    color: red;
    text-decoration: underline;
}
```

## 背景

导入css

```css
<link rel="stylesheet" href="css/style.css">
```

背景颜色

背景图片

```css
    <div id="nav">
        <h2 class="title">全部商品分类</h2>
        <ul>
            <li><a href="#">a1</a>&nbsp;<a href="#">a2</a>&nbsp;<a href="#">a3</a></li>
            <li><a href="#">b1</a>&nbsp;<a href="#">b2</a>&nbsp;<a href="#">b3</a></li>
            <li><a href="#">c1</a>&nbsp;<a href="#">c2</a>&nbsp;<a href="#">c3</a></li>
            <li><a href="#">d1</a>&nbsp;<a href="#">d2</a>&nbsp;<a href="#">d3</a></li>
        </ul>
    </div>

```

```css
#nav{
    width: 300px;
    background: rgb(165, 165, 162);
}
/* 
    设置图片：
    background-image: url("../images/arrow-right.png"); 背景图片的url路径
    background-size:auto 18px;  背景图片的大小限制
    background-repeat: no-repeat;  无平铺
    background-position: 246px 11px; 背景图片的坐标
 */
.title{
    font-size: 18px;
    font-weight: bold;
    text-indent: 1em;
    line-height: 38px;
    /* 背景统一设置：背景颜色，图片url，图片坐标，无平铺 */
    background: greenyellow url("../images/arrow-right.png") 246px 11px no-repeat;
    /* 背景图片的大小设置 */
    background-size:auto 18px;
    /* background-image: ;
    
    background-repeat: ;
    background-position: ; */
}
/*  list-style: 列表的圆点或者数字样式
    circle:空心圆
    decimal:数字
*/
/* ul{
    background: rgb(165, 165, 162);
} */
ul li{
    height: 30px;
    list-style:none;
    text-indent: 1em;
    background-image: url("../images/arrow-down.png");
    background-size:auto 18px;
    background-repeat: no-repeat;
    background-position: 204px 3px;
}
a{
    font-size: 14px;
    color: black;
    text-decoration: none;
}
a:hover{
    color: red;
    text-decoration: underline;
}
```

<img src="https://i.loli.net/2021/05/20/ScxAd6lV7fOaKkJ.png" alt="QQ截图20210429093136" style="float:left" />

## 渐变

[Grabient](https://www.grabient.com/)

```css
background-color: #4158D0;
background-image: linear-gradient(43deg, #4158D0 0%, #C850C0 46%, #FFCC70 100%);
```

# 盒子模型

<img src="https://i.loli.net/2021/05/20/rJO815kpthl4FXx.png" style="float:left"/>

margin:外边距

border:边框

padding:内边距



盒子的计算方式：盒子到底多大？

（50*50）  margin+border+padding+内容宽度

## 边框border

1. 边框的粗细

2. 边框的样式
3. 边框的颜色

```css
    <div id="box">
        <h2>京东会员</h2>
        <form action="#" method="POST">
            <div>
                <span>用户名</span>
                <input type="text" name="nick" placeholder="邮箱\用户名\已验证手机">
            </div>
            <div>
                <span>密码</span>
                <input type="password" name="psw">
            </div>
        </form>
    </div>
```



```css
 <style>
        /* body总有一个默认的外边距magin:0 */
        /* 初始化 */
        /* h1,ul,li,a,body{
            margin: 0;
            text-decoration: none;
            padding: 0;
        } */
        #box{
           width: 300px;
           height: 167px;
           /* 边框：粗细，样式实虚线，颜色 */
           border: 2px solid red;
        }
        h2{
            background: rgb(252, 102, 102);
            line-height: 38px;
            color: white;
        }
        form{
            background: rgb(147, 224, 147);
        }
        /* 注意box是id还是class,id是唯一的此时可以定位否则不可定位 */
        div:nth-of-type(1){
           border: 2px solid blueviolet;
        }
        /* 实线solid 虚线dashed */
        div:nth-of-type(2){
           border: 2px dashed darkcyan;
        }
    </style>
```

## 内外边距margin

```css
<!-- 外边距的妙用：居中 -->
    <style>
        #box{
           width: 300px;
           /* 边框：粗细，样式实虚线，颜色 */
           border: 2px solid red;
           /* magin:顺时针 上 右  下 左 （4个参数）
              magin:上下，左右  （2个参数）
           */
           margin: 0 auto;
        }
        h2{
            background: rgb(252, 102, 102);
            line-height: 38px;
            color: white;
            margin: 0px 1px 2px 3px;
        }
        form{
            background: rgb(147, 224, 147);
        }
        input{
            border: 2px solid rebeccapurple;
        }
        div:nth-of-type(1){
            padding: 10px;
        }
    </style>
```

## 圆角边框

```css
    <style>
        div{
            width: 100px;
            height: 100px;
            border: 10px solid royalblue;
            border-radius: 100px;
        }
    </style>
```

<img src="https://i.loli.net/2021/05/20/ceVIm49yASkBDod.png" style="float:left"/>

圆：径宽=长度

用途:调整头像....

<img src="https://i.loli.net/2021/05/20/wpP26xJiSAX5QlR.png" style="float:left"/>

## 阴影

头像发光

<img src="https://i.loli.net/2021/05/20/Mdp69noikAPuce4.png" style="float: left; zoom: 50%;"/>

```css
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        /* 水平偏移，上下偏移，阴影半径，阴影颜色 */
        #div-shadow{
            width: 100px;
            height: 100px;
            border: 10px solid red;
            margin-bottom: 100px;
            box-shadow: 10px 3px 4px rgb(155, 240, 155);
        }
        img{
            margin: 0px 220px;
            border-radius: 30px;
            box-shadow: 10px 10px 100px yellow;
        }
    </style>
</head>
<body>
    <div id="div-shadow"></div>
    <img src="image/QQ截图20210425162248.png" alt="">
    
</body>
```

居中

```css
    <div id="div-shadow"></div>
    <img src="image/QQ截图20210425162248.png" alt="">

    <div style="display: block;text-align: center;">a</div>
```



# 浮动

## 标准文档流

块级元素：h1~h6 p div 列表

行内元素：span a imag strong

可以将数着的uli变为横着的 ul li 初始化为 display:inline-block

## display

```css
    <style>
       div{
          width: 100px;
          height: 100px;
          border: 2px solid red;
          /* 加了之后就不独占一行了 */
          display:none;
       }
       span{
          width: 100px;
          height: 100px;
          border: 2px solid red;
          /* 默认行内元素的width和height不起作用 */
          /* display变为块元素 */
          /* inline-block:既是行内元素也是块元素
             none:消失
           */
          display:inline-block;
       }
    </style>
```



行内元素浮动玩法：

display也是一种实现行内元素排列的方式，但是很多情况下都是使用**float**

## float

更多情况下用float实现：

1. 左右浮动

```css
div{
    margin: 10px;
    padding: 5px;
}
#father{
    border: 2px solid red;
}
.layer01{
    border: 2px solid greenyellow;
    display: inline-block;
    float: left;
}
.layer02{
    border: 2px solid orange;
    display: inline-block;
    float: left;
}
.layer03{
    border: 2px solid blueviolet;
    display: inline-block;
    float: left;
    clear: both;
}
.layer04{
    border: 2px dashed blue;
    font-size: 12px;
    line-height: 23px;
    display: inline-block;
    float: left;
    /* 既然浮动效果也要块局元素效果，清除浮动 */
    clear: both;
}
```

## 父级边框塌陷的问题

左右两侧不允许有浮动

clear:both

解决方案：

1.增加父级元素高度

```css
#father{

  border: 2px solid red;

  height: 800px;

}
```

2.标准解法  增加一个空的div清除左右两侧浮动

```css
<div class="clear"></div>

.clear{
    clear: both;
    margin: 0;
    padding: 0;
}
```

3.overflow

在父级元素中增加一个溢出隐藏

```css
#father{
    border: 2px solid red;
    overflow: hidden;
}
```



```css
        #overflow{
            width: 200px;
            height: 300px;
            border: 2px solid rebeccapurple;
            /* 溢出部分隐藏 */
            overflow: hidden;
        }
```

4.父类添加一个伪类 :after

市面上最认可的解决方案

```css
#father:after{
    content: '';
    display: block;
    clear: both;
}
```

小结：

1.浮动元素后面增加空div

  简单 ，代码中避免空div

2.设置父元素固定高度

  不好

3.overflow

 简单，下拉的情况下避免

4.伪类after

  推荐使用

## 对比

- display

方向不好控制

- float

向左向右可以控制，浮动起来会脱离父级文档流需要解决塌陷问题。

# 定位

## 相对定位

postition:relative

相对原来的位置进行指定的偏移，注意没有脱离文档流，原来的位置会被保留

```css
    <!-- 相对定位：
        相对自己原来的位置偏移
     -->
    <style>
        body{
            padding: 20px;
        }
        div{
            margin: 10px;
            padding: 5px;
            font-size: 18px;
            line-height: 38px;
        }
        #father{
          border: 2px solid red;
          padding: 0;
        }
        #first{
            border: 2px dashed rebeccapurple;
            background: rgb(172, 112, 231);
            /* 相对定位上下左右 */
            position: relative;
            top: -20px;
            left: 20px;
        }
        #secord{
            border: 2px dashed royalblue;
            background: rgb(109, 138, 228);
        }
        #third{
            border: 2px dashed gold;
            background: rgb(240, 222, 125);
        }
    </style>
```

```css
    <div id="father">
        <div id="first">第一个盒子</div>
        <div id="secord">第二个盒子</div>
        <div id="third">第三个盒子</div>
    </div>
```

## 绝对定位

定位：基于xxx定位，上下左右~

1.基于没有父级元素定位的前提下，相对于浏览器定位

2.假设父级元素有定位则相对父级元素定位

3.在父级元素范围内移动

绝对定位的话，不在标准文档流，原来的位置不会被保留

```css
    <style>
        div{
            margin: 10px;
            padding: 5px;
            font-size: 18px;
            line-height: 38px;
        }
        #father{
          border: 2px solid red;
          position: relative;
        }
        #first{
            border: 2px dashed rebeccapurple;
            background: rgb(172, 112, 231);
        }
        #secord{
            border: 2px dashed royalblue;
            background: rgb(109, 138, 228);
            position: absolute;
            right: 30px;
        }
        #third{
            border: 2px dashed gold;
            background: rgb(240, 222, 125);
        }
    </style>
```



## 固定定位fixed

```css
    <style>
        body{
            height: 1000px;
        }
        div:nth-of-type(1){
            width: 100px;
            height: 100px;
            background: red;
            /* 相对浏览器决定定位 */
            position: absolute;
            right: 0;
            bottom: 0;
        }
        /* 很多到导航栏就是采用固定定位的 */
        div:nth-of-type(2){
            width: 50px;
            height: 50px;
            background: yellow;
            position: fixed;
            right: 0;
            bottom: 0;
        }
    </style>
```

<img src="https://i.loli.net/2021/05/20/BdWaK25sFTY8eu7.png" style="float:left;zoom:60%"/>





## z-index

立体感觉

<img src="https://i.loli.net/2021/05/20/3htdIvozqbLZjHp.png" style="float:left;zoom:60%"/>

```css
#content{
    width: 300px;
    margin: 0;
    padding: 0;
    overflow: hidden;
    font-size: 12px;
    line-height: 25px;
    border: 2px solid rgb(74, 74, 212);
}
ul,li{
    margin: 0;
    padding: 0;
    list-style: none;
}
/* 父级元素相对定位 */
#content ul{
    position: relative;
}
.tipText,.tipBg{
    position: absolute;
    width: 300px;
    height: 25px;
    top: 191px;

}
.tipText{
    color: aliceblue;
    /* 设置层级 */
    /* z-index: 999; */
}
.tipBg{
    background: rgb(243, 224, 116);
    opacity: 0.4;
}
```

```css
    <div id="content">
        <ul>
            <li><img src="images/1.jpg" alt="" style="zoom: 20%;"></li>
            <li class="tipText">刘西瓜</li>
            <li class="tipBg"></li>
            <li>时间:2021.4.29</li>
            <li>地点：湖南大学</li>
        </ul>
    </div>
```

# CSS总结

<img src="https://i.loli.net/2021/05/20/IojWTdlGk3amtsD.png" alt="QQ截图20210430093203" style="zoom: 67%; float: left;" />

































































