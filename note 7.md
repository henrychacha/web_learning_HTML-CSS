## 复习

小三角、小箭头
```
<!-- 小三角 -->
    .cart{
        width:0px;
        height:0px;
        border:50px solid;
        border-color:transparent transparent red;
    }
<!-- 箭头 -->
    .cart{
        width:0px;
        height:0px;
        border:50px solid;
        border-color:transparent transparent red;
    }
    .cart::after{
        content:'';
        position:absolute;
        bottom:XX;
        left:-50px
        width:0px;
        height:0px;
        border:50px solid;
        border-color:transparent transparent #fff;
    }

```
字体图标

透明兼容
```
  background:rgba(0,0,0,0.5)     背景透明 不影响里面得内容   IE低版本不兼容
  opacity:0.5;    元素整体透明，元素本身及内容全部透明   IE低版本不兼容
  IE专属滤镜  filter: alpha(opacity=50)   元素整体透明，元素本身及内容全部透明 

```


居中技巧

```
    方法1：父元素尺寸未知，子元素尺寸已知

    .parent{
        position:relative;
    }
    .child{
        position:absolute;
        left:50%;
        top:50%;
        margin-left:-150px;
        maring-top:-100px;
        width:300px;
        height:200px;
    }

    方法2: 父元素和子元素尺寸未知
    .parent{
        position:relative;
    }
    .child{
        position:absolute;
        left:0;
        right:0;
        top:0;
        bottom:0;
        margin:auto;
    }

```


## 浮动和定位对比
- 文档流：指的是元素按照本身的属性进行排列，块元素从上往下垂直排列，行内元素从左往右
- 浮动： 
    - 通常用来实现水平得多列布局（左右、左中右、四列、五列）
    - 所有元素（块级、行内、行内块）都可浮动
    - float:left/right; 会使元素脱离文档流
    - 浮动的元素会脱离文档流,不脱离文本流（文字、图片、表单元素不会被浮动元素覆盖）
- 定位（层布局）： 
    - 通常用来实现元素之间固定的位置关系，或者有覆盖关系的
    - 所有元素（块级、行内、行内块）都可定位
    - position:absolute/fixed;会使元素脱离文档流
    - 定位的元素既脱离文档流，又脱离文本流

- 脱离文档流的元素特点： 
    - 不再区分行内和块级
    - 默认宽高都是由内容撑开
    - 能设置宽高，所有盒模型属性

## css精灵图（雪碧图）
> 英文叫法 CSS sprites , 解释为 “css贴图定位”或“css
图像拼合”。原理就是把一些小图片拼在一张图片上，通过背景引入，用背景定位调整显示的图标。
适合一些小图标，不适合大图背景。

- 优点：
   - 1、减少网页http请求次数，提高页面的性能
   - 2、减少图片命名困扰
   - 3、更换风格方便
- 缺点：
   - 1、必须要规定好容器的尺寸，背景定位的值也必须精确计算，相对比较麻烦



