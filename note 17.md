## 复习

###  复合选择器
```
  后代： .box p{ ... }   .box .red{    }  .box *{    }
  子代：  .box>p{ ... }
  并集（群组）：  h3,.box,p,.box div{ ... }
  交集： div.red{ ...  }
```
###  状态伪类选择器
```
   a:link{ ... } 
   a:visited{ ... }
   a:hover{ ... }
   a:active{ ... }

   a{  ... }
   a:hover{ ... }
   .box{ ... }
   .box :hover{ ... }
   .box:hover span{ ... }
```

###  盒模型
```
    四层：内容content+内边距padding+边框border+ margin外边距
    content:  width  、 height
    padding:  盒子边缘和内容之间的距离，会显示背景颜色
        padding-top:20px;
        padding-bottom:20px;
        padding-left:20px;
        padding-right:20px;
    border: 边框
        border:2px solid black;
        border-top:2px solid black;
        border-bottom:2px solid black;
        border-left:2px solid black;
        border-right:2px solid black;
        border-top:none/0;
    margin: 外边距
        margin-left:20px;
        margin-right:30px;
        margin-top:30px;
        margin-bottom:30px;
```

### 盒模型属性补充：
```
    内边距：
        padding:10px;   上下左右四个方向内边距相同
        padding:10px 20px;  上下     左右
        padding:10px 20px 30px;  上   左右   下
        padding:10px 20px 30px 40px;  上   右  下   左
    边框：
        border-width:2px;   设置边框宽度
        border-style:solid;  设置边框风格  solid 实线  dashed 虚线  dotted 点线  double 双实线
        border-color:red;  设置边框颜色

        border-top-width: 2px;  设置上边框的宽度
        border-top-style: solid;  设置上边框的风格
        border-top-color: yellow;  设置上边框的颜色

        bottom、left、right三个方向和top同理
    外边距：
        margin:10px;   上下左右四个方向外边距相同
        margin:10px 20px;  上下     左右
        margin:10px 20px 30px;  上   左右   下
        margin:10px 20px 30px 40px;  上   右  下   左

        margin:0 auto;  水平居中

   * margin可以设置负值，可以通过负值减少元素的占位，比如margin-top为负值（-50px），元素垂直方向会往上移动，并且减少50px的占位       
```

## 垂直外边距合并问题
### 1、垂直方向margin-top传递问题
- 当父元素没有padding\border\float\position\overflow时，给子元素设置margin-top会把父元素一块儿带下来
- 解决: 
   - 1、给父元素添加1px的上padding或者border,子元素margin-top少1px
   - 2、可以用父元素的padding-top实现同样式的效果

### 2、相邻元素的外边距合并
- 两个同级的标签，上一个设置margin-bottom:40px,下一个设置margin-top:60px，最后两者之间的外边距会合并为数值较大的那个值(60px)，不是数值相加(100px)


## 标签分类
- 1、块级标签 （div,p,h1-h6,ul,li,ol,dl,dt,dd,hr）
    - 排列：从上往下独占一行
    - 默认宽度占满父级,高度由内容撑开
    > 占满父级表示 盒子实际内容的宽度 + 左右padding + 左右border + 左右的外边距 = 父级宽度100% 
    - 可以设置宽高,可以设置所有的盒模型属性

- 2、行内标签 (span,a,i,em,b,strong,sub,sup,del)
    - 排列：从左到右
    - 默认宽度和高度都是由内容撑开
    - 不可以设置宽高, 水平方向盒模型属性（padding、border、margin）可以正常设置，垂直方向盒模型不能设置

- 3、行内块级 (img) 
    - 排列：从左到右 
    - 默认宽度和高度都是由内容撑开
    - 可以设置宽高,可以设置所有的盒模型属性 (margin:0 auto;无效)

## 居中
> 1、块元素中的行内元素或者行内块居中，给外部的这个块元素设置text-align:center;
> 2、块元素在父级元素中水平居中，给这个块元素设置margin:0 auto;


## 盒子类型转换

- display:block;  设置成块级标签
- display:inline;  设置成行内标签
- display:inline-block;  设置成行内块级标签
- display:none;  隐藏元素,页面上不显示也不占位

    
## 行内块之间的空白距离和下方多出的空白

- 解决方案：
    - 给父元素设置font-size:0;line-height:0;  
    - 给子元素重新设置font-size和line-height

