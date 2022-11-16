## 复习

- 新增背景属性
- 多背景
    background-image:url(...),url(...);
    background-repeat: no-repeat, repeat;
    background-position: left bottom, right top;
    background:url() no-repeat left bottom,url() no-repeat right top;
- 背景尺寸
    background-size: 100px  200px / 50% 50% / contain /cover;
    contain : 包含 ，图片宽高比不变(等比例缩放)，图片刚好被包含进盒子，但是盒子可能不能能完全被覆盖
    cover ： 覆盖，图片宽高比不变(等比例缩放)，盒子刚好被图片完全覆盖，图片可能显示不全

- 背景图片起始位置
    background-origin: 
        - content-box: 内容框区域开始显示
        - padding-box: 默认值，背景图片从内边距开始显示
        - border-box ： 边框区域开始显示
- 背景裁切位置
    background-clip:
        - border-box :默认 ， 边框以外裁剪
        - padding-box : 内边距以外裁剪
        - content-box : 内容框以外裁剪

- 渐变
    background-image
    background

- 线性渐变
    linear-gradient(direction,color-start,color-stop 20%,color-step 50%);

    - direction: 方向  （to bottom, to top , to right ,to left ,to right bottom , 30deg ...）
    - color-start : 开始颜色
    - color-stop ：结束颜色

    repeating-linear-gradient(direction,color-start,color-stop 20%,color-step 50%)

- 径向渐变
    -webkit-radial-gradient(cx cy,rx ry,color-start,color-stop....);
        cx cy : 圆心位置 , left/center/right/50%/100px top/center/bottom/50%/100px;
        rx ry : 半径， 50%/100px   50%/100px 
    -webkit-repeating-radial-grandient(cx cy,rx ry,color-start,color-stop....)

background:linear-gradient(), radial-gradient()...;


- 用户界面
 - resize   是否允许用户缩放元素尺寸
    - none  不允许
    - both   宽高都可调整
    - vertical 可以改变高度
    - horizontal  可以改变宽度
    textarea{resize: none;}
    * 需要配合元素的overflow:hidden/auto/scroll属性使用，才能生效
 - box-sizing
    - border-box : 怪异盒 , 占位宽 由 width决定 ，添加padding和border会压缩内容区，并不会使盒子整体变大
    - content-box : 标准盒，占位宽  width + 左右padding + 左右 border

- 多列

column-count: 3;
column-width:200px;
column-gap: 20px;
column-rule: 1px solid red;



## 变形 transform
### 2D变形
* 所有变形都不会影响元素本身的占位
- 1、位移，保留占位（类似相对定位）
  - translate(x,y)    水平和垂直同时位移 
  - translateX()  水平位移,正往右，负往左
  - translateY()  垂直位移, 正往下，负往上
- 2、旋转
  - rotate(deg)  正顺时针，负逆时针   

- 3、缩放
  - scale(n) scale(n-x,n-y)  水平和垂直同时缩放  
  - scaleX(n)  水平缩放
  - scaleY(n)  垂直缩放
    - n 表示缩放的倍数，> 1 放大  0.X 缩小

- 4、倾斜（扭曲）
  - skew(x-deg,y-deg)  水平和垂直同时倾斜，只写一个值表示水平倾斜，垂直不倾斜
  - skewX(deg)  横向拉伸 ，正数往左边倒 ， 负数往右边倒
  - skewY(deg)   纵向拉伸，正数右侧往下 ， 负数左侧往下


### 3D变形

- 1、位移
  - translateZ()  Z轴位移，正方向位移靠近（放大）  负方向位移远离 （缩小）
  - translate3d(x,y,z)  三个轴同时位移  
- 2、旋转
  - rotateX()  绕X轴旋转，正顺时针（上往里倒，下往外翻），负逆时针 （下面往里，上面往外）
  - rotateY()   绕Y轴旋转， 正顺时针 （右边往里，左边往外），负逆时针（左边往外，右边往里）
  - rotateZ()   绕Z轴旋转,正顺时针，负逆时针
  - rotate3d(x-n,y-n,z-n,deg)  
    - n ： 代表三个轴的矢量，0 不转， 1 正方向旋转 ，-1  负方向旋转
    - deg : 旋转的度数
- 3、缩放 
  - scaleZ(n) Z轴缩放
  - scale3d(x,y,z)  三个轴同时缩放
 
## 3d环境设置

- 1、视距设置 perspective:600-2000px;
- 模拟视图和人眼的距离，让3d变形的元素呈现远小近大的效果，需要设置给父元素或者祖先元素

- 2、变形风格 

 transform-style: flat;  父元素3d变形时，子元素3d效果失效
 transform-style: preserve-3d;  保留子元素的3d效果

- 变形原点：

transform-origin: left/center/right/100px/50%   top/center/bottom/100px/50%;
  - 变形原点的设置，不是基于文档流的，也就是说，当你设置了position:relative并且移动了以后，原点会根据新的位置重新设置。
