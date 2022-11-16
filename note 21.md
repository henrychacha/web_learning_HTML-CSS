## 复习
```
css3新版本，css2.1基础上进行增补与修改
增加模块：选择器，边框属性，文本修饰，背景属性，多列布局，弹性盒布局，2D/3D变形，过渡，动画
渐进增强
优雅降级

浏览器私有前缀

    -webkit-
    -moz-
    -o-
    -ms-

选择器
    属性选择器   
        [attr]  
        [attr=val]  
        [attr~=val]    class="box red"   [class~=red]
        [attr^=val]
        [attr$=val]   
        [attr*=val]   class="box redBox"   [class*=red]
    结构伪类选择器
        :first-child   选择同级元素中的第一个  .box :first-child{   } 
        :last-child    选择同级元素中的最后一个  .box :last-child{   } 
        :nth-child(n)   选择同级元素中的第n个   :nth-child(2n)    :nth-child(2n+1)
        :nth-last-child(n)  选择同级元素中的倒数第n个

        :first-of-type   选择同级元素中同种类型中的第一个
        :last-of-type   选择同级元素中同种类型中的最后一个
        :nth-of-type(n)  选择同级元素中同种类型中的第n个
        :nth-last-of-type(n)  选择同级元素中同种类型中的倒数第n个

    状态伪类
        :enabled
        :disabled
        :checked
        ::selection

    圆角
        border-radius:10px;  四个角圆角半径为10px
        border-radius:10px 20px;  左上右下   右上左下
        border-radius:10px 20px 30px; 左上    右上左下   右下
        border-radius:10px 20px 30px 40px;  左上   右上  右下  左下

        border-top-left-radius
        border-top-right-radius
        border-bottom-left-radius
        border-bottom-right-radius
    阴影
        box-shadow:h-shadow  v-shadow  blur  spread color inset;
            - h-shadow  : 水平位置 0  不偏移  正--右   负 -- 左
            - v-shadow  : 垂直位置   0  不偏移  正--下   负 -- 上
            - blur  ： 模糊半径
            - spread  ： 扩展半径    负值缩小  正值放大  
            - color:阴影颜色
            - inset : 设置inset就是内阴影，否则外阴影

        box-shadow:0px 5px 10px #333,-5px 0 10px #f00,...;
    文字修饰(阴影)
        text-shadow: h-shadow  v-shadow blur color;
            - h-shadow  : 水平位置 0  不偏移  正--右   负 -- 左
            - v-shadow  : 垂直位置   0  不偏移  正--下   负 -- 上
            - blur  ： 模糊半径
            - color:阴影颜色

```


## 新增背景属性

css2：
    background-color
    background-image
    background-repeat
    background-postion


- 1、多背景

> background-image:url(),url()...;
    - 设置多个背景图片，顺序是写得越靠前，层级越高
> background-repeat:
    - 一个值表示多个图片重复属性一样
    - 多个值，分别设置每个图片的重复属性
> background-position:
    - 一组值表示多个图片定位属性一样
    - 多组值，分别设置每个图片的定位属性

```
    background-image: url("http://www.ujiuye.com/statics/images/xibaopcimages/logo.png"),url("http://xue.ujiuye.com/uploads_it/2002/QuanGuo/F2R26392822VQD0W.jpg");
    background-repeat: no-repeat,repeat;   /* 两个图片的重复属性不同 */
    background-repeat: no-repeat;  /* 两个图片的重复属性相同 */
    background-position: right top, center;   /* 两个图片的定位属性不同 */
    background-position: center;   /* 两个图片的定位属性相同 */

```
> 多背景简写:
```
    background:url(...) no-repeat center,url(...) repeat-x left bottom,...;

```
多背景的简写中不能添加颜色。颜色要单独用background-color来写。

- 2、背景尺寸

> background-size
    - length : 宽度（500px）  高度（300px）  , 一个值表示设置宽度，高度自动    
    - 百分比：参考盒子的尺寸， 宽度（50%）  高度（100%） , 一个值表示设置宽度，高度自动
    - cover : 覆盖 ,图片会等比例缩放，直到能够覆盖整个盒子，（而且图片的宽或者高与盒子一致）但是有可能图片无法完全显示
    - contain ： 包含 ，图片会等比例缩放，直到图片刚好被完全包含进来，（而且图片的宽或者高与盒子一致）但是有可能盒子没有完全覆盖
    - cover适用于当盒子变化时图片是否完全显示没有关系的情况，而contain适用于盒子变化时图片都要完全显示的情况。在处理移动端和响应式布局中常常用到

- 3、背景图片初始位置
> background-origin: 
    - border-box : 背景图片从边框区域开始显示，并且从边框开始计算定位
    - padding-box :默认值， 背景图片从内边距区域开始显示，并且从内边距开始计算定位
    - content-box: 背景图片从内容框区域开始显示，并且从内容框开始计算定位
- 4、背景裁切
> background-clip: 
    - border-box : 默认值，边框以外背景被裁切
    - padding-box : 内边距以外背景被裁切
    - content-box : 内容区以外背景被裁切

* 新增的背景属性不能用background属性简写

## 渐变
> 渐变不是一个颜色模式，专门用来修饰盒子背景
可以设置给：background、background-image
不能设置给：background-color


- 1、线性渐变
> linear-gradient(direction,color-start,color-stop,color-stop...)

- direction : 渐变方向
    - to bottom :默认值 ，从上到下渐变
    - to top : 从下到上
    - to right : 从左到右
    - to left   : 从右到左
    - to top right : 从左下到右上（也可以写成to right top）
    - to left bottom : 从右上到左下
    - angle度数    : 0deg 从下到上  45deng  左下到右上  ...
    ...
- color-start :起始颜色
- color-stop : 渐变停止的位置

```
   background: linear-gradient(to right,red,#ff0 20%,rgb(0,255,0) 50%,blue);
```

> 重复的线性渐变
> repeating-linear-gradient(direction,color-start,color-stop,color-stop);
> 最后一个颜色值不到百分之百，后面剩余的空间就会重复前面的渐变效果
```
    background: repeating-linear-gradient(to right,red,yellow 20%);
```

> 多组渐变
```
 background: linear-gradient(red,rgba(255,255,0,0.5)),linear-gradient(to right,blue,green),...;
```

- 2、径向渐变
> radial-gradient(圆心位置(cx cy)，半径（rx ry),color-start, color-stop...);
> 加上webkit私有前缀才能兼容半径和圆心的设置
- 圆心位置(cx cy): 水平和垂直坐标
    - 取值可以是 长度值（100px 100px）/百分比 (100% 50%)/关键词 (left top) 
- 半径（rx ry) : 水平和垂直半径长度
    - 取值可以是：长度值（100px 100px）/百分比 (100% 50%)
```
    background: -webkit-radial-gradient(0% 100%,100% 50%,red,yellow,green);
```
> 重复径向渐变
> repeating-radial-gradient(圆心位置(cx cy)，半径（rx ry),color-start, color-stop...)
> 如果最后一个颜色值不到100%，剩下的空间就会重复前面渐变

> 多组径向渐变
```
 background: radial-gradient(red,rgba(255,255,0,0.5)),radial-gradient(to right,blue,green),...;
```

## 用户界面
1、resize 是否允许用户缩放元素尺寸
> 需要配合overflow:auto/hidden/scroll属性，才能生效，不能是visible，否则会没有效果
- 取值：
```
    none : 不允许用户缩放
    both  : 水平和垂直都可以缩放
    vertical: 垂直缩放
    horizontal: 水平缩放
```
> 通常用来取消多行文本域用户可改变尺寸效果 `textarea{resize:none}`

2、box-sizing  
> 用来规定盒子的盒模型的计算方式（渲染模式）
- content-box（标准盒） : 默认值，盒子的实际占位宽 width + 左右padding + 左右border ,三者共同决定
- border-box（怪异盒）: 盒子的实际宽只由width属性决定，添加padding和border会压缩内容区宽度，而盒子整体大小不变
- input button本身就是怪异盒子


## 多列布局
> css3提供的一种布局方式，能够快速实现类似于报纸布局那样的多列效果
- 1、column-count: 设置多列列数
- 2、column-width: 设置每一列的列宽 ，不方便精准控制列宽和列数，比较少用
- 3、column-gap: 设置两列之间的间距
- 4、column-rule: 设置两列之间的分界线 ， 语法同边框

