## 复习

```
    float:left;
    float:right;
    float:none;

 浮动产生的问题？怎么解决？

 浮动元素脱离文档流之后，无法撑开父级高度
 - 清除浮动：
    - 1、父级 height 
    - 2、父级 overflow:hidden 
    - 3、额外标签法 浮动元素后添加不浮动的标签设置clear:both
    - 4、伪元素
    .clearfix::after{
        content:'';
        display:block;
        clear:both;
    }  
    .clearfix{
        *zoom:1;
    }
- overflow:hidden;  超出隐藏
- overflow:visible;  超出显示
- overflow:scroll;  始终显示滚动条
- overflow:auto;  自动，超出显示滚动条，不超出不显示滚动条

::after{
    content:''
    display:block;
}
::before{
}

背景系列：background: red url() no-repeat center;
    颜色 : background-color:red/transparent;
    图片 : background-image:url();
    重复 : background-repeat:repeat/repeat-x/repeat-y/no-repeat;
    定位 : background-position: left/center/right/100px/50%   top/center/bottom/100px/50%;

```

## 定位position
> 布局方法：文档流、浮动、层布局（定位）
> 三种定位：相对定位、绝对定位、固定定位
### 1、相对定位
> 语法：position:relative;
> 特点：相对定位不脱离文档流，在文档中原本的位置依然为其保留
> 偏移参考位置： 元素本身在文档流内原本的位置

### 2、绝对定位
> 语法：position:absolute;
> 特点：绝对定位的元素会脱离文档流，在文档中原本的位置不保留
> 偏移参考位置(定位父级)： 离绝对定位元素最近的一个带有position属性的祖先元素，如果不存在这样的元素就是参考body定位

### 3、固定定位
> 语法：position:fixed;
> 特点：固定定位的元素会脱离文档流，在文档流中原本的位置不保留
> 偏移参考位置: 浏览器的可视区

## 定位偏移属性

- left:距离参考位置左边缘偏移，正数向右偏移，负数向左偏移
- right: 距离参考位置右边缘的偏移，正数向左偏移，负数向右偏移
- top:距离参考位置上边缘偏移，正数向下偏移，负数向上偏移
- bottom: 距离参考位置下边缘偏移，正数向上偏移，负数向下偏移

> left和right通常使用一个，如果同时使用left生效
> top和bottom通常使用一个，如果同时使用top生效

* 脱离文档流的元素不会自动占满一行，宽度默认是由内容撑开