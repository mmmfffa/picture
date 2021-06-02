# 初识Html

[[源码地址](https://gitee.com/ma-fu/dashboard/projects)]:



- 什么是Html
- 网页基本标签
- 图像，超链接，网页布局
- 列表，表格，媒体元素
- 表单及表单应用
- 表单初级验证

## W3C标准

**结构化**标准语言：HTML,XML

**表现**标准语言：CSS

**行为**标准：DOM,ECMAScript

# 网页基本信息

## 标签

meta:描述标签符，关键词用来描述网站的一些信息，一般用来做SEO

**网页基本标签**

- 标题标签 h
- 段落标签 p
- 换行标签 br(间距小)
- 水平线标签 hr
- 字体样式标签  粗体strong  斜体em
- 注释和特殊符号  转义标签  空格&nbsp >&gt <&lt &copy版权

**图像标签**

快捷键：img然后打tab键

```jsp
<img src="path" alt="text" title="text" width="x" height="y">
```

**链接标签**

target:表示窗口在哪里打开  _blank页面跳转  _self在自己页面打开

```html
<!--文本超链接，图像超链接-->
<a href="path" target="目标窗口的位置">链接文本或图像</a>
```

 点击图像跳转

```html
<a href="path" target="目标窗口的位置">
    <img src="path" alt="text" title="text" width="x" height="y">
</a>
```

**锚链接**

- 需要一个锚标记（使用name作为标记）
- 跳转到标记   #

功能性链接

- 邮件链接：mailto
- QQ链接

## 行内元素和块元素

块元素：无论内容多少只占一行  p  、 h

行内元素：内容撑开宽度   a,jstrong,em   不会另起一行

## 列表

- 有序列表
- 无序列表
- 定义列表

```html
<!-- 有序列表 试卷-->
<ol>
    <li>Mybatis</li>
</ol>
<hr>
<!-- 无序列表 导航侧边栏-->
<ul>
    <li>Mybatis</li>
</ul>
<hr>
<!-- 定义列表 用于网站底部-->
<dl>
    <dt>列表名称1</dt>
    <dd>类表内容</dd>
</dl>
```

## 表格

单元格

跨行

跨列

```html
    <!-- table
         行tr
         th
         列td
         跨列colspan
         跨行rowspan
     -->
<table border="1px">
    <tr>
        <td colspan="3">1-1</td>
    </tr>
    <tr>
       <td rowspan="2">2-1</td>
       <td>2-2</td>
       <td>2-3</td>
   </tr>
   <tr>
      
       <td>3-2</td>
       <td>3-3</td>
   </tr>
</table>
```

## 媒体元素

视频元素 video    mp4

音频元素 audio    mp3

进度条，自动播放

```html
    <!-- 音频和视频 -->
<!-- <video src="../resource/video/1.mp4" controls autoplay ></video> -->
<audio src="../resource/audio/1.mp3" controls autoplay></audio>
```

## 页面结构分析

| 元素名  | 描述               |
| ------- | ------------------ |
| header  | 标题头             |
| footer  | 标记脚步区域的内容 |
| section | 一块独立区域       |
| article | 独立的文章内容     |
| aside   | 侧边栏             |
| nav     | 导航栏             |

## iframe内联框架

```html
<iframe src="path" name="mainFrame">
    
</iframe>


 <iframe src="" name="hello" frameborder="0" width="1000" height="800"></iframe>
   <a href="https://www.baidu.com/" target="hello">点击跳转</a>
```

## 表单语法（重点）



| 属性      | 说明                                                         |
| --------- | ------------------------------------------------------------ |
| type      | 指定的元素类型。text,password,多选框checkbox,单选框radio,submit,reset,file,hidden,imag,button |
| name      | 表单元素名称                                                 |
| value     | 元素的初始值                                                 |
| size      | 指定表单元素的初始宽度。text和password以字符为单位，其他以像素为单位 |
| maxlength | text和password时指输入最大字符数                             |
| checked   | radio和checkbox指按钮是否被选中                              |

所有的input标签都需要一个name属性

### 表单post和get

```html
    <h1>注册</h1>
    
    <!-- action:可以是请求，网站，地址 -->
    <!-- post安全，传大文件，get高效 -->
    <form action="hello.html" method="GET">
        <p>名字：<input type="text" name="name" size="30" value="mafu好好！" maxlength="8"></p>
        <p>密码：<input type="password" name="password"></p>
        <p>性别：
            <input type="radio" value="boy" name="sex" checked>男
            <input type="radio" value="girl" name="sex">女
        </p>
        <p>
            <input type="submit" name="submit" value="submit" >
            <input type="reset" name="reset" value="reset">
        </p>
    </form>
```

### 按钮

```html
        <!-- 
            type="button"  普通按钮
            type="image"   图片按钮
            type="submit"  提交按钮
            type="reset"   重置按钮
        -->       
       <p>按钮：
            <input type="button" name="btn1" value="点击变长">
        </p>
        <p>图片按钮：
            <!-- <input type="image" src="../resource/image/1.jpg"> -->
        </p>
        <p>
            <input type="submit" name="submit" value="submit" >
            <input type="reset" name="reset" value="reset">
        </p>
```

### 单选框和多选框和下拉框

```html
        <p>性别：
            <input type="radio" value="boy" name="sex" checked>男
            <input type="radio" value="girl" name="sex">女
        </p>
        <p>爱好：
            <input type="checkbox" value="sleep" name="hobby">睡觉
            <input type="checkbox" value="code" name="hobby" checked>代码
            <input type="checkbox" value="game" name="hobby">游戏
        </p>
        <p>下拉框:
            <select name="列表名称">
                <option value="china">中国</option>
                <option value="en">音国</option>
                <option value="us">没国</option>
                <option value="eth" selected>瑞士</option>
                <option value="ying">中家国</option>
            </select>
        </p>
```

### 文本域和文件域

```html
        <p>文本域：
            <textarea name="textarea" cols="30" rows="10">文本内容</textarea>
        </p>

        <p>文件域：
            <input type="file" name="files">
            <input type="button" name="upload" value="上传文件">
        </p>
```

### 验证

```html
       <!-- 邮件验证 -->
       <p>邮件验证：
          <input type="email" name="email">
       </p>
       <!-- url验证 -->
        <p>url验证：
            <input type="url" name="email">
        </p>
        <!-- 数字验证 -->
        <p>数字验证：
            <input type="number" name="number" max="100" min="10">
        </p>
```

### 滑块和搜索框

```html
 <!-- 滑块 -->
        <p>滑块：
            <input type="range" name="voice" max="100" min="10" step="1">
        </p>
        
        <!-- 搜索框 -->
        <p>搜索框：
            <input type="search" name="search">
        </p>

        <p>
            <input type="submit" name="submit" value="submit" >
            <input type="reset" name="reset" value="reset" step="10">
        </p>
```

## 表单应用

- 隐藏域  hidden
- 只读  readonly
- 禁用  disable
- 增强鼠标的可用性 label 

```html
        <p>增强鼠标可用性：
            <label for="mark">点击试试</label>
            <input type="text" name="label"  id="mark">
        </p>
```

## 表单初级验证

作用：减轻服务器压力，数据安全

常用方式

- placeholder 提示信息
- required  元素不能为空
- pattern 正则表达式（常用正则表达式）

# 总结