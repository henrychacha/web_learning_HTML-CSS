## BFC?

### BFC概念？（是什么？）
> Block Formatting Context 块级格式化上下文
> Formatting Context，指的是页面中的一个渲染区域，并且拥有一套渲染规则，他决定子标签如何定位，以及与其他标签的相互关系和作用。
> BFC , 块级格式化上下文,指的是页面中的一个渲染区域，只有Block-level BOX （块级盒子）参与,该区域中拥有一套渲染规则来约束块级盒子的布局，且与外部无关。

（bfc是文本流中的一种盒子一种组成单元，html本身就是一个bfc，子元素属于父元素的bfc，除非子元素自己成为了一个bfc；建立一个bfc，相当于单独划出一个独立的单元，脱离文档流的定位和浮动都会划出一个bfc，行内块是一个bfc，overflow也会让元素变成bfc；bfc内部的子元素有特别的排列规律，他的块元素要垂直排，子元素的垂直边距由会折叠的margin决定，边距要与包含块边界写出，）

### 如何生成BFC?

> 以下情况是目前学到的能够生成BFC的情况: 
> 根元素  html
> float属性值不为 none
> overflow 属性值不为 visible 
> display 属性值为 inline-block
> position属性值为 absolute/fixed

### BFC的特性？

- ①、内部的块标签会在垂直方向一个接一个的放置
- *②、垂直方向的距离有margin决定，属于同一个BFC的两个相邻的标签外边距会发生重叠
- ③、每个标签的左外边距和包含块的左边界相接触，即使浮动标签也是如此
- *④、BFC区域不会与float的标签区域发生重叠
- *⑤、计算BFC的高度时，浮动子元素也参与计算
- ⑥、BFC就是页面中的一个隔离的独立容器，容器里的子标签不会影响到外部标签，反之，外部标签也不会影响bfc内部的标签。

### BFC解决的问题？
- 1、（垂直）外边距折叠
> 根据特性第②条，属于同一个BFC的两个相邻的标签外边距会发生重叠( 父子外边距重叠、兄弟关系边距重叠)
<!-- 父子元素都属于html中的元素，它们要满足bfc内部元素的外边距排列规则，也就是垂直方向上边距会折叠，所以给子元素设置外边距的。父元素和子元素如果单独看，它们都对垂直方向上的那个元素A有外边距，父元素一开始的外边距为0，子元素也为0，当给子元素设置外边距时，子元素的外边距作用的是元素A，而父元素的外边距作用的也是A，它们是相邻元素，它们的外边距重叠，也就是比较以后选择最大值，作为它们各自的外边距 -->
> 解决方法： 让标签处于不同的BFC区域中就不会重叠
```
    父子边距重叠： 给父元素设置生成BFC的属性
    兄弟边距重叠： 给其中任意一个添加一层BFC父级
```
- 2、实现自适应两栏或三栏布局 （根据特性④）
> 两栏布局，左侧固定宽度，右侧栏自适应（随浏览器尺寸变化缩小放大）
> 三栏布局，左右两栏固定宽度，中间栏自适应(随浏览器尺寸变化缩小放大)
```
     <!-- 两栏 :  
        .left  设置宽度，左浮动
        .right  宽度自动占满父级，设置overflow:hidden
    -->
    <div class="cols">
        <div class="left"></div>
        <div class="right"></div>
    </div>
    <!-- 
        三栏：
        标签顺序：先写左右栏，再写中间栏
        .left1  设置宽度，左浮动
        .right1  设置宽度，右浮动
        .center 宽度自动占满父级，设置overflow:hidden
     -->
    <div class="cols">
        <div class="left1"></div>
        <div class="right1"></div>
        <div class="center"></div> 
    </div>
```

- 3、防止文字环绕图片排列 （根据特性④）
> 浮动的元素会覆盖不浮动的元素，文字会环绕图片排列，把文字所在标签设置为BFC,可以避免文字环绕
- 4、清除浮动
> 根据第⑤条特性，计算BFC的高度时，浮动子元素也参与计算，所以可以通过bfc清除浮动，例如给浮动元素父级添加overflow:hidden;





## 布局方案

### 两栏自适应
- 方法一： BFC

```
     <!-- 两栏 :  
        .left  设置宽度，左浮动
        .right  宽度自动占满父级，设置overflow:hidden
    -->
    <div class="cols">
        <div class="left"></div>
        <div class="right"></div>
    </div>
```

- 方法二： 
 - .left 左侧栏固定宽，设置绝对定位 position:absolute;
 - .right 右侧栏宽度自动，给其添加padding-left:200px，并且添加子元素 .inner , 把右侧栏的内容放在.inner里面
```
        .left{
            position: absolute;
            left: 0;
            top:0;
            width: 200px;
            height: 300px;
            background-color: rgb(202, 150, 252);
        }
        .right{
            padding-left: 200px;
            <!-- 或者使用margin-left，这样就不需要添加inner才能使背景颜色 -->
        }
        .inner{
            background-color: coral;
            height: 300px;
        }

    <div class="cols">
        <div class="left"></div>
        <div class="right">
            <div class="inner">hello world</div>
        </div>
    </div>
```

### 三栏自适应

- 方法一：BFC

```
    <!-- 
        三栏：
        标签顺序：先写左右栏，再写中间栏
        .left1  设置宽度，左浮动
        .right1  设置宽度，右浮动
        .center 宽度自动占满父级，设置overflow:hidden
     -->
    <div class="cols">
        <div class="left1"></div>
        <div class="right1"></div>
        <div class="center"></div> 
    </div>
```
2021-07-22 补充：流体布局：

- 方法二：圣杯布局
 - 为了使主体内容优先加载，标签顺序 .main  .left .right
 - .main 宽度设置 100%  ，.left 宽度 200px  .right 宽度240px
 - .main ,.left ,.right 三栏都左浮动
 - .left添加margin-left:-100%; 拉到最左边 ，.right 添加margin-left:-240px; 拉到三栏的右边，.main被左右两边栏覆盖

 圣杯布局解决覆盖问题：

 - 给父级.container添加padding:0 240px 0 200px; 这个时候.mian 宽度正常，左右两栏同时被挤到中间
 - 给.left 添加position:relative;left:-200px; 往左移
 - 给.right 添加position:relative;right:-240px; 往右移
 
 

- 方法三：双飞翼布局

- 为了使主体内容优先加载，标签顺序 .main  .left .right
 - .main 宽度设置 100%  ，.left 宽度 200px  .right 宽度240px
 - .main ,.left ,.right 三栏都左浮动
 - .left添加margin-left:-100%; 拉到最左边 ，.right 添加margin-left:-240px; 拉到三栏的右边.main被左右两边栏覆盖

 双飞翼解决覆盖的问题：
 - 给.main添加一层子元素 .main-inner 
 - 给 .main-inner 添加外边距  margin:0 240px 0 200px;把主体内容都放在 .mian-inner里面
（(不能直接给.main添加外边距，因为这样会让left和right一开始设置的margin-left起作用，改变布局)
