## 媒体查询

- css2媒体类型： 
    all ： 所有
    screen : 屏幕
    print ：打印机
    ...

- css2媒体类型区分语法(不推荐)：

```
     <link rel="stylesheet" href="./css/screen.css" media="screen">
     <link rel="stylesheet" href="./css/print.css" media="print">

```

- css3媒体查询：
 
> 参数说明：
    width:视口宽度等于某个值
    device-width: 设备的宽度(设置了viewport , 等同于第一个参数)
    min-width: 视口的最小值，规定大于某个值的范围
    max-width: 视口的最大值，规定小于某个值的范围

```
        /* 视口宽度（等同于设备宽度）等于320px */
        @media screen and (width:320px){ 
            .box{
                background-color: yellow;
            }
        }
        /* 视口宽度大于等于414px */
        @media screen and (min-width: 414px){
            .box{
                border: 2px solid black;
            }
        }    
        /* 视口宽度小于等于768px */
        @media screen and (max-width: 768px){
            .box{
                border-right: 10px solid limegreen;
            }
        }
        /* 视口宽度大于等于360px并且小于等于414px */
        @media screen and (min-width: 360px) and (max-width: 414px){
            .box{
                border-bottom: 10px solid hotpink;
            }
        }

```


## 媒体查询 + rem

```
    html{
        font-size: 100px;
    }

    @media screen and (width:375px){
        html{
            font-size: 50px;  /* 375*100/750  */
        }
    }

    @media screen and (width:320px){
        html{
            font-size: 42.66666px;  /* 320*100/750*/
        }
    }
    
    @media screen and (width:360px){
        html{
            font-size: 48px;  /*  360*100/750  */
        }
    }

```

## vw适配(了解)
- 1、vw单位
vw 即Viewport's width的简写，是css3规范中的视口单位，相对于视口的宽度，视口被均分为100单位的vw。
相关单位了解：
除此之外还有vh单位 即Viewport's height，相对于视口的高度，视口高度被均分为100单位的vh。
vmax相对于视口的宽度或高度中较大的那个。其中最大的那个被均分为100单位的vmax。
vmin相对于视口的宽度或高度中较小的那个。其中最小的那个被均分为100单位的vmin。

- 2、vw单位布局
确定基准值以常见的750px宽度的设计稿为例，那么根据vw单位的原理100vw = 750px，即1vw = 7.5px，我们可以根据设计图中的px直接转换成对应的vw值进行布局，当然也可以直接写px，借助插件插件自动计算成需要的vw。因为vw是相对于视口宽度的单位，当视口宽度发生变化，则元素大小随即发生变化。


- 3、rem+vw
确定基准值以常见的750px宽度的设计稿为例，结合以上，那么根据vw单位和rem的单位原理（参照本章节之前内容在此不在缀述）。
在750px的设计稿下，如果使用vw单位换算，可以理解为100vw,对应750px,那么1px就是0.1333333vw。
如果使用rem，预设1rem = 100px,通过上面的计算结果1px是0.13333333vw,那么100px就是13.333333vw了。由此实现单位rem与vw之间的换算。
设置html{font-size:13.33333333vw}
然后我们就可以在布局写rem单位了, 由于倍率是100,除以100,直接小数点向左移动2位,1rem是100px,那么10px就是0.1rem，不需要借助插件转换计算也可以直观的进行布局了。

## 移动端特殊处理
> 1、小字体处理
不同浏览器的最小字体不同，有的是10px，有的是12px。
解决办法：设置字体时，不要小于12px,如果一定要小于12px，使用transform:sacle()进行缩放。
```
     @media screen and (max-width:320px){
            .box p{
                width: 2.5rem;
                transform-origin: left center;
                transform: scale(0.95);
            }
     }
```
> 2、动画定义3D启用硬件加速
element {
    -webkit-transform:translate3d(0,0,0)
    transform: translate3d(0,0,0);
}
注意：3D变形会消耗更多的内存与功耗。

> 3、圆角bug：部分Android手机圆角失效

element{
    background-clip: padding-box;
}
> 4、Input 的placeholder会出现文本位置偏上的情况

在IOS和Android中显示不同。解决方法是：在保证input输入文本垂直居中的条件下，给placehoder设置padding-top，不要设置行高。

