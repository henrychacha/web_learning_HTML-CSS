## 复习

- 关键帧动画： 自动运行，动画多个节点，可以反复运行
- 过渡动画：用伪类触发，动画只有两个状态，触发一次运行一次
```
    transition: property duration timing-fucntion delay;
    transition:width 1s linear,height 1s linear;
```

- 盒子阴影： box-shadow: x-shadow y-shadow blur spread color inset;
- 文字阴影:  text-shadow: x-shadow y-shadow blur color;

```
    box-shadow: 0px 0px 10px #333,5px 0px 20px #ff0000,...;
```

## 三角和箭头

- 1、小三角： 
> 实现思路：把盒子宽高设置为0,保留一个边框的颜色，其他边框设置为透明
```
        .box{
            width: 0px;
            height: 0px;
            border: 50px solid;
            border-color: turquoise transparent transparent;
        }
```

- 2、小箭头：
> 实现思路：实现两个三角，通过定位让两个三角部分重叠，上一层三角颜色设置成和背景相同的颜色
```
        <div class="arrow1"></div>

        .arrow1{
            position: relative;
            width: 0px;
            height: 0;
            border: 50px solid;
            border-color: turquoise transparent transparent;
            margin-top: 10px;
        }
        .arrow1::after{
            position: absolute;
            left: -50px;
            top: -55px;
            content: '';
            width: 0px;
            height: 0px;
            border: 50px solid;
            border-color: #fff transparent transparent;
        }
```


## 透明兼容

- 1、rgba() 模式颜色： 可以给文字和背景设置颜色(IE低版本不兼容)
 > 给元素设置背景透明时，不会影响里面的内容

- 2、opacity:0-1;  0完全透明，1不透明，0.X半透明(IE低版本不兼容)
 > 元素整体透明，元素本身以及里面的内容全部透明

- 3、filter:alpha(opacity=50)  IE低版本浏览器专用透明滤镜，效果等同于opacity属性，0代表完全透明，100代表不透明

## 居中技巧

- 方法一： 父级的尺寸未知，子元素的尺寸已知

```
    .outer{
        position:relative;  /*父元素相对定位*/
    }
    .inner{
        width:300px;
        height:200px;
        position:absolute;  /* 子元素绝对定位*/
        left:50%;   /* left:50%;  盒子偏右*/
        top:50%;    /* top:50%;  盒子偏下*/
        margin-left:-150px;   /* margin-left设置为子元素宽度的一半（负值），往左移*/
        margin-top:-100px;  /* margin-left设置为子元素高度的一半（负值），往上移*/
    }
```

- 方法二： 父级的尺寸和子元素的尺寸都可以未知

```
    .outer{
        position:relative;  /*父元素相对定位*/
    }
    .inner{
        position:absolute;
        left:0;
        right:0;
        top:0;
        bottom:0;
        margin:auto;
        width:300px;
        height:200px;
    }
```

## 字体图标使用

地址：https://www.iconfont.cn/


