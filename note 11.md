## 复习

相对定位：
    position:relative;
    不脱离文档流，原本的位置保留
    位移参考位置：元素在文档流中原本的位置

绝对定位：
    position:absolute;
    脱离文档流，不占位
    定位父级：离绝对定位元素最近的带有position:relative/absolute/fixed;属性的祖先元素,如果不存在就是body
固定定位：
    position:fixed;
    脱离文档流，不占位
    位移参考位置：浏览器可视区

偏移属性：
    left : 正右 ， 负左
    right ： 正左，负右
    top ： 正下 , 负上
    bottom ： 正上， 负下
## 定位补充

- 静态定位：position:static; 没有定位，偏移属性失效（left/right/top/bottom），并且层级(z-index)也失效
- 定位元素的层级设置： 设置了定位的元素可以通过z-index属性调整层级关系，默认值都是0，数字越大层级越高，数字相同，层级跟标签的顺序有关，标签越靠后层级越高


## 圆角
- 简写属性：
```
    border-radius:10px;  四个角圆角半径统一
    border-radius:10px 20px;  左上和右下   右上和左下
    border-radius:10px 20px 30px;  左上   右上和左下   右下
    border-radius:10px 20px 30px 40px;  左上   右上   右下  左下  
```
- 分解属性
```
    border-top-left-radius: 20px;
    border-top-right-radius: 40px;
    border-bottom-left-radius: 60px;
    border-bottom-right-radius: 80px;
```

## 变形 transform

1、旋转
-  transform:rotate(30deg);  正数顺时针，负数逆时针
2、缩放
-  transform:scale(n);  水平和垂直同时缩放 n 取值 0-1之间缩小 , n>1 就是放大
-  transform:scale(n-x,n-y);  n-x：水平方向的缩放值,n-y垂直缩放值

## 关键帧动画 
1、定义动画的关键帧
```
    @keyframes 动画名称{
        0%{  

        }
        25%{

        }
        50%{

        }
        75%{

        }
        100%{ 

        }
    }
```

2、调用动画

- animation: animation-name animation-duration animation-iteration-count  animation-timing-function  animation-delay  animation-direction;
 - animation-name: 调用的动画名称
 - animation-duration:整个动画过程需要的时间 s(秒)/ms(毫秒)
 - animation-iteration-count:动画执行的次数 n/infinite（无限次）
 - animation-timing-function: 动画速度曲线
     - ease  慢-快-慢（默认）
     - linear 匀速
     - ease-in 慢-快
     - ease-out 快-慢
     - ease-in-out 慢-快-慢
     - cubic-bezier(.08,.73,.42,.93) 贝塞尔曲线 https://cubic-bezier.com/
 - animation-delay: 动画延迟时间 s/ms
 - animation-direction: 动画的方向 alternate(轮流反向)
 - animation-fill-mode: 动画结束位置 forwards(停在终点)
 



