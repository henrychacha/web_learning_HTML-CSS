<!--
 * @Descripttion: your project
 * @version: 1.0
 * @Author: henrytam
 * @Date: 2020-03-13 16:47:44
 * @LastEditors: henrytam
 * @LastEditTime: 2021-07-21 20:30:07
-->

## 复习

- vertical-align 垂直对齐方式:baseline(基线)、middle、top、bottom;

- 图片和文字

```
    <p> 文字 <img src="..." style="vertical-align:middle"></p>
```

- 两个行内元素或者两个行内块或者行内和行内块

```
    span{
        vertical-align:middle;
    }
    <span>span1</span>
    <span>span2</span>
```

### 浮动

布局方式：文档流、浮动、层
文档流：元素按照本身的属性在页面排列，块从上往下，行内从左往右

1、左浮动 float:left;

- 左浮动的元素会尽可能往左走，直到碰到父元素或者相邻浮动元素的边缘停下来
- 脱离文档流，不占位
- 多个左浮动的元素从左到右依次排列

2、右浮动 float:right;

- 右浮动的元素会尽可能往右走，直到碰到父元素或者相邻浮动元素的边缘停下来
- 脱离文档流，不占位
- 多个右浮动的元素从右到左依次排列

3、取消浮动 float:none;

- 回到文档流占位

> 补充： 浮动的元素脱离文档流之后，可以覆盖文档流内的元素，但是文字和图片以及表单元素不会被覆盖，会围绕浮动元素排列

## 清除浮动

- 解决浮动元素脱离文档流之后无法撑开父级高度的问题
- 解决方案：
  - 1、给父元素设置 height 属性, 代码的扩展性不好（不方便维护）
  - 2、给父元素设置 overflow:hidden; 因为 overflow:hidden;本身的效果是会让元素溢出的部分隐藏掉，所以某些情况无法使用 overflow:hidden;
  - 3、额外标签法: 在所有浮动元素之后添加一个不浮动的元素，给其添加 clear:both 属性（clear:both 意思就是清除浮动）。 会增加结构中的冗余代码。
  - 4、通过伪元素的方式添加标签（和额外标签法原理相同），用法：在样式表中预先定义好.clearfix 类，遇到需要清除浮动的标签（所有浮动元素的父级），就给其添加上 clearfix 类名
  ```
       .clearfix::after{
           content: '';
           display: block;
           clear: both;
       }
       .clearfix{
           *zoom:1;
       }
  ```

## overflow 规定元素内容溢出显示方式

- overflow:visible; 溢出显示
- overflow:hidden; 溢出隐藏，多出的部分被直接截断
- overflow:scroll; 始终显示滚动条区域
- overflow:auto; 内容溢出显示滚动条，内容不溢出就不显示滚动条

## 伪元素

- ::after 在元素的末尾（内部）添加伪元素
- ::before 在元素的开头（内部）添加伪元素
  > 使用场景：一般用来给局部添加一些样式处理

## 背景属性

- 1、背景颜色
  background-color:#000;
  background-color:transparent; 透明

- 2、背景图片
  background-image:url("...");

- 3、背景重复
  background-repeat:
  - repeat 默认值，水平和垂直都铺满
  - repeat-x 水平重复
  - repeat-y 垂直重复
  - no-repeat 不重复
- 4、背景定位
  background-position: 水平 垂直;
  - left/center/right top/center/bottom
  - x-length y-length 通过具体的设置具体的长度值控制图片位置, x 轴数字 正数往右移，负数往左移， y 轴数字正数往下移，负数往上移
  - x-% y-% 通过百分比控制位置，x 轴 0%表示最左边，100%表示最右边，50%表示中间，y 轴 0%表示顶部，100%表示底部，50%表示中间
    > 背景定位属性值，如果只设置一个方向，表示另一个方向默认位 center
- 5、简写属性
  > background:color image repeat positon;
  > 简写属性里面的各个值得顺序可以调整，并且可以省略掉不需要设置的属性
  ```
    background:lightblue url("http://www.ujiuye.com/statics/images/xibaopcimages/logo.png") no-repeat center;
  ```

> 网页图片和背景图片区别

- 跟网页内容相关，比较重要的图片都要使用 img 标签添加，比如广告图、商品图、logo 图...
- 跟内容无关，作为网页的修饰性的一图案使用背景图片，比如纹理、修饰性的小图标...背景图片不能撑开元素的尺寸
