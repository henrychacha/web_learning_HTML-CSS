## 复习
- 浏览器
```
    IE —— trident
    firefox - gecko
    safari - webkit
    opera - presto - webkit - blink
    chrome - webkt - bink
```

- 三层结构
```
结构层
表现层
行为层
```
- html 基础

html定义： 超文本标记语言
html文档：后缀名.html，网页
语法： 
    双标签：
    `<关键词> ... </关键词>`
    单标签：空标签
    `<关键字>`

属性：
    `<关键字 class=“值” > ... </关键词>

元素：
    标签以及标签之间的内容这个整体称之为元素

注释：
    <！-- 注释 -- >

文档结构：
```
<!doctype html>
<html>
    <head>
        <meta charset="utf-e">
        <title> ... </title>
    </head>
    <body>
    主体
    </body>
</html>
````

- 常用标签
    - div `<div style="width:200px;height:200px; background-color:red;">` 区块
     - 使用div标签把一连串内容分区
    - hi-h6 标题
        - h1：一个页面只能使用一次，用于logo和名称
        - 注意：不要通过h1-h6标题标签去对普通内容实现加粗效果，之后可以通过样式进行调整
        - p 段落标签，写一段文字时用到。两个p标签之间有边距


## 一、常用标签

- 1、斜体
    - i : 样式斜体，没有特殊语义
    ```
    <i> 斜体文字 </i>

    - em : 样式斜体，并且有强调语义，可以进行搜索引擎优化
    ```
        <em> 斜体文字 </em>
- 2、加粗
    - b :
    ```
    <b> 样式文字 </b>
    ```
    - strong: 样式加粗，有强调语义
    ```
    <strong> 样式文字 </strong>
- 3、span: 无语义标签
    - 放在一段文字中不会影响整体的布局，通常用来给一段文字中的某几个文字添加特殊样式
    ```
        <span style="color:blue;"> ... </span>

- 4、br 换行标签，单标签（很多个空格智慧显示一个空格）
    ```
        <br>

    ```
- 5、hr 分割线，语义代表主题结束，单标签
    ```
        <hr>
    ```
* 文字居中
```
    <h1 style="text-align:center;">...</h1>
    <p style="text-align:center;">,,,</p>
```
- 6、sup 上标文本
```
    <sup>...</sup>
```
- 7、sub 下标文本
```
    <sub>...</sub>
```
- 8、del 删除文本
```
    <del>...</del>
```

## 二、列表
### 1、有序列表
- 有序列表用来定义一些顺序重要的内容
- 默认给每个项目添加序号
- 通过type属性可以修改编号的类型：“1、A、a、I、i”
- ol和li属于固定父子标签，ol的直接子元素只能是li
```
    <ol type=“a”>
        <li>张三</li>
        <li>李四</li>
        <li>王五</li>
    </ol>
````
### 2、无序列表
- 无序列表用来定义一些顺序不重要的内容
- 默认添加列表项符号
- 可以通过type属性改变列表项符号的类型‘desc，circle，square’
- ul和li属于固定父子标签。
```
    <ul type=“circle”>
        <li>tom</li>
        <li>jack</li>
        <li>rose</li>
    </ul>
```
### 3、定义列表
- 一般用于解释一些专有名词或者术语说明
- dt：放专有名词或者属于
- dd：放解释说明，一个dt可以用多个dd去进行描述，dd的内容默认有缩进
```
    <dl>
        <dt>html</dt>
        <dd>超文本标记语言</dd>
        <dd>是用来描述网页的一种语言</dd>
        <dt>css</dt>
        <dd>层叠样式表</dd>
        <dd>是用来定义网页的样式的语言</dd>
    </dl>
```

## 三、标签分类
- 块级标签
    - 每一个标签都会独占一行，新添加一个块标签，会另起一行
    - 多个标签垂直排列
    - 所有的块标签都可以设置宽高和大小，style=”width：200px；height：300px；background-color：green“
```
div
h1-h6
p
dl dt dd
ul li
ol li
hr
```
- 行内标签
    - 多个行内标签从左到右在一行显示，如果标签间有空间，则会产生一个空格
    - 不可以设置宽高，不能设置text-align，如果要把一个元素居中，需要把它放在块标签中
```
span
i em
b strong
sub
sup
del

```
 - br比较特殊，专门用于换行，不能设置其他样式，所以我们分类时候不考虑它

 ## 四、图片
 - 常见的图片格式：jpg、gif、png   

 ```
    <img src="图片路径”>
```
- src： 用来定义图片的路径
- alt:  规定图片无法正常显示时的替换文本
- width：
- height：
- 有的标签可以直接写width和height，有些必须要在style里写宽高，img标签中两种都可以
- 宽高可以只写一个，然后另一个以保持比例不变的方式自动设定。width=“200”，px可写可不写，style标签中的width和height中的宽高要px
- 图片和文字内容差不多，不能够自己居中，需要在外面包一个块标签，给块级标签设置style=“text-align：center”

## 路径

- 1、相对路径
```
    src="../images/pic01.jpg"
    ./  当前目录查找，可以省略不写
    ../ 返回上一级目录
    ../../ 返回上两级目录
    /  代表根目录，不要随便使用
```
- 2、绝对路径
    - 本地磁盘绝对路径
```
    <img s="c>
    - 复制网页图片的地址
