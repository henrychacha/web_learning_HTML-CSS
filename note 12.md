## 复习

- 变形  transform 

- 2D
位移
    translate(x,y)
    translateX()
    translateY()
旋转
    rotate()  
缩放
    scale(n)  scale(n-x,n-y) 
    scaleX(n)
    scaleY(n)
倾斜    
    skew(x,y)  skew(x)
    skewX()
    skewY()

- 3D （增加）
位移：
    translateZ()
    translate3d(x,y,z)
旋转：
    rotateX()
    rotateY()
    rotateZ()
    rotate3d(x-n,y-n,z-n,deg)

缩放：
    scaleZ()
    scale3d(x,y,z)

- 视距设置；perspective:600-2000px;

- 变形风格：transform-style:flat/preserve-3d;

- 变形原点：

transform-origin: left/center/right/100px/50%   top/center/bottom/100px/50%;


## 弹性盒布局 （flex-box） 
> css3提供得一种新得布局方式
> 弹性盒布局得目的是提供一种更加有效得方式来规定弹性盒子内部子元素的排列方式，对齐方式，空白空间的分配。
> 当把元素设置为弹性容器之后，里面的子元素 float/display/vertical-align属性会失效,position属性还可以用
> 弹性容器改变的是直接子元素的排列方式/对齐方式，不会对子元素内部的元素产生影响
- 弹性盒是bfc
### 容器属性
1、设置弹性盒容器
> display:flex/inline-flex;
    - flex : 把元素设置为弹性容器，元素本身的属性为块级
    - inline-flex: 把元素设置为弹性容器，元素本身的属性为行内
2、设置主轴方向
> 主轴方向决定项目的排列方式
> flex-direction:row|row-reverse|column|column-reverse;
    - row :默认， 从左到右
    - row-reverse: 从右到左
    - column: 从上到下
    - column-reverse: 从下到上
3、设置项目在主轴上的对齐方式
> 具体效果和主轴的方向有关，这里以主轴方向默认从左到右为例
> justify-content:flex-start|flex-end
    - flex-start ：默认， 主轴的开始位置对齐（左对齐）
    - flex-end : 主轴的结束我位置对齐  （右对齐）
    - center : 主轴中间对齐
    - space-between: 在每两个项目之间留出相同的空白，主轴的开始和结束没有空白
    - space-around: 在每个项目两边留出相同的空白，两个项目之间就是双倍空白
    - space-evenly: 主轴开始和结束以及每一个项目之间都是相同的空白
4、设置项目在交叉轴上的对齐方式
> 以主轴从左到右，交叉轴从上到下
> align-items: stretch|flex-start|flex-end|center|baseline;
    - stretch :默认， 拉伸，当项目没有设置固定高，会进行拉伸占满容器高度
    - flex-start : 交叉轴的开始位置对齐（顶部对齐）
    - flex-end : 交叉轴的结束位置对齐（底部对齐）
    - center : 交叉轴的中间对齐
    - baseline: 基线对齐

5、项目换行
> flex-wrap:no-wrap|wrap|wrap-reverse;
    - no-wrap: 默认，不换行，项目被压缩
    - wrap: 换行
    - wrap-reverse : 换行，颠倒行的顺序

6、多行在交叉轴上的对齐方式
> align-content:stretch|flex-start|flex-end|center|space-around|space-between;
    - stretch :默认，拉伸，当项目没有设置固定高，拉伸占满整个容器，比如有两行，每一行高度占容器的1/2，如果项目设置了固定高，项目在每一行的空间上顶部对齐
    - flex-start ： 多行在交叉轴的开始对齐（顶部）
    - flex-end ： 多行在交叉轴的结束对齐（底部）
    - center : 交叉轴中间对齐
    - space-around : 每一行前后留出相同的空白
    - space-between ： 每两行之间留出相同的空白

### 项目属性

1、规定项目的排序
> order:number;
> 默认值都是0，数字越大排序越靠后,数字相同,按照代码顺序排列

2、规定项目放大比例
> flex-grow:number;
    flex：1；
flex弹性盒子flex-grow 和flex的区别
> 默认项目的放大比例都是0 ，就是不放大，如果都是1就是等比放大，如果设置不同的数字，就按照数字比例等比放大

3、规定项目压缩比例（项目总宽度超出容器宽度，不换行）
> flex-shrink:number;
> 默认值是1，表示所有的项目等比缩小,0表示不缩小，设置不同数字，就按照数字比例等比缩下

4、规定指定项目的在交叉轴上的对齐方式
> align-self: 取值同容器的align-items属性



## css预处理
> css预处理就是定义了一种新的语言。基本思想是通过一种专门的编程语言，为css增加一些编程的特性，通过这种编程语言(预处理语言)编写css代码（这种语言不能直接运行在浏览器上），然后通过指定编译器编译成css文件，最后运用到网页中。
> 比较成熟的css预处理语言有less/sass(scss);
> 优点：使用预处理语言可以使css代码更加简洁，适应性更强，可读性和可维护性更好。

## less 
### 使用less
    - 编译less插件 -- Easy LESS 
    - 创建 less 文件  -- 编辑  -- 保存  -- 自动生成同名的  .css文件

### less语法

- 1、导入样式
    - 导入css文件
    ```
        @import "reset.css";
        如果导入的使.css文件，就是把这句代码直接复制进编译过后的css文件中
        编译后：
        @import "reset.css";
    ```
    - 导入less文件
     ```
        @import "reset.less"; 导入less文件，可以省略后缀名
        @import "reset"; 
        如果导入的使.less文件，把reset.less中的代码复制一份合并到目标文件中
        编译后：
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            list-style: none;
        }
        img {
            vertical-align: middle;
        }
    ```
- 2、注释
    - css注释
    ```
        /*
            这是css的注释，less中可以显示，并且会被编译进css文件中
        */
    ```
    - less注释

    ```
        // 这是less注释，只在less文件中显示，不会编译进css文件中
    ```

- 3、变量

> 变量类似于容器，可以用来存储一些值，后期可以通过变量名去反复调用变量里面的值，有利于页面后期更换风格（维护）
> 变量命名必须要加 @ 后面的变量名尽量使用有意义的单词和数字组合
```
    @变量名:值;

    @main-color:#00ff00;
    @sub-color:orange;
    @fs-lg:14px;

    .box{
        width:100px;
        height:100px;
        background-color:@main-color;
        color:@sub-color;
        font-size:@fs-lg;
    }

```

