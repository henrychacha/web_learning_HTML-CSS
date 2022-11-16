## 复习
- 弹性盒模型  (flex-box)
> css3提供得新的布局方式
> 目的是提供一种更加有效得方式去定义弹性容器内子元素得排列方式、对齐方式、空白分配

### 容器属性
1、display:flex/inline-flex;  设置为弹性容器
2、flex-direction:row/row-reverse/column/column-reverse;      主轴方向
3、justify-content: flex-start/flex-end/center/space-between/space-around/space-evenly;   项目在主轴上得对齐方式
4、align-items:stretch/flex-start/flex-end/center/baseline;    交叉轴得对齐方式
5、flex-wrap: no-wrap/wrap/wrap-reverse;   项目是否折行
6、align-content:stretch/flex-start/flex-end/center/space-between/space-around/space-evenly;   多行在交叉轴上对齐方式
### 项目属性
1、order:number;  默认 0 , 数字越大越靠后
2、flex-grow: number; 默认 0 不放大, 根据数字得大小决定放大比例
3、flex-shrink: number; 默认都是 1 等比缩小，根据数字大小决定缩小比例  数字越大压缩越多 
4、align-self : stretch/flex-start/flex-end/center/baseline;  设置之指定项目在交叉轴的对齐


## css预处理

## less  语法 + 编译器

### 1、导入样式

``` 
    @import "reset.css";   // 导入css样式表，编译过后把导入的语法原样编译进css文件中

    @import "reset.less"; // 导入less问件，编译过后把reset文件中的代码编译进目标css文件中
    @import "reset"; //导入less可以省略后缀名
```

### 2、注释

```
    /*
        css的标准注释，既可以显示在less中，也会编译进css文件中
    
    */

    //  less 的注释，只显示在less中，不会被编译进css文件中
```
### 3、变量

```
    @变量名:#fff;
    @main-color:#ff0000;
    @sub-color:#ffff00;
    @fs-lg:20px;
    ...

    .box{
        background-color:@main-color;
    }

```

### 4、混入
> 把一个类A混入到另一个类B中，使B类继承了类A里面的代码，并且可以传参

- 1)、不带参数的混入

> less:
```
    .size{
        width: 100px;
        height: 100px;
    }

    .box1{
        .size;
        background-color: red;
    }

```

> 编译后css：
```
    .size{
        width: 100px;
        height: 100px;
    }
    .box1{
        width: 100px;
        height: 100px;
        background-color: red;
    }
```
- 2）带参数的混入

> less:

```
    /* 混入的类名后面只要带了() 这个类本身就不会被编译进css文件中*/
    .size(@w,@h){    //混入的类内部需要几个可以变的值，就定义几个参数（形参）,形参的语法和变量相同，多个用逗号隔开
        width: @w;
        height: @h;
    }


    .box1{
        .size(100px,200px);  // 调用混入的类时，需要传入具体的数值（实参），一般和形参需要一一对应
    }
    .box2{
        .size(200px,300px);
    }
```
> 编译后css：

```  
    .box1{
        width:100px;
        height:200px;
    }
    .box2{
        width:200px;
        height:300px;
    }
```


- 3）带参数和默认值的混入

>  less
```
    .size1(@w:100px,@h:100px){ // 形参后面通过冒号添加默认值
        width: @w;
        height: @h;
    }

    .box5{
        .size1;  // 当调用类不传实参，使用默认值
    }
    .box6{
        .size1(200px,300px); //调用类传入了实参，就会覆盖默认值 
    }
    .box7{
        .size1(400px);  //实参个数比形参少，默认按照顺序匹配，没有匹配到实参的参数依然使用默认值 
    }
    .box8{
        .size1(@h:500px);  // 可以添加形参名称和值指定实参匹配那个参数
    }
```

> 编译后css

```
    .box5{
          width: 100px;
          height: 100px;
    }
    .box6 {
        width: 200px;
        height: 300px;
    }
    .box7 {
        width: 400px;
        height: 100px;
    }
    .box8 {
        width: 100px;
        height: 500px;
    }

```

- 4)、@arguments   参数集合
>less:
```
    .boxShadow(@h,@v,@blur,@s,@color){
        box-shadow: @h @v @blur @s @color;
    }

    .boxShadow(@h,@v,@blur,@s,@color){
        box-shadow: @arguments;  //和上面的代码等效
    }

    .box3{
        .boxShadow(0px,5px, 10px, 0px, #333)
    }
    .box4{
        .boxShadow(5px,0px, 20px, 0px, red)
    }

```
>编译后css：

```
    .box3 {
        box-shadow: 0px 5px 10px 0px #333;
    }
    .box4 {
        box-shadow: 5px 0px 20px 0px red;
    }
```

### 5、嵌套
> less：
```
    .header{
        height: 50px;
        background-color: #333;
        .left{
            float: left;
            ul{
                list-style: none;
                line-height: 50px;
                li{
                    float: left;
                    background-color: orange;
                    a{
                        color: #fff;
                        &:hover{  // 添加&符表示继承父级选择器 （不添加空格）
                            color:#f00;
                        }
                    }
                }
            }
        }
    }

```

> 编译后css：

```
    .header {
        height: 50px;
        background-color: #333;
    }
    .header .left {
        float: left;
    }
    .header .left ul {
        list-style: none;
        line-height: 50px;
    }
    .header .left ul li {
        float: left;
        background-color: orange;
    }
    .header .left ul li a {
        color: #fff;
    }
    .header .left ul li a:hover{
        color: #f00;
    }
```
### 6、继承

> 类似于简单的混入，把一个类继承到另一个类当中，但是混入是复制，会产生代码冗余，继承则不会

> less :
```
.size{
    width: 100px;
    height: 100px;
}
.box{
    &:extend(.size);
    background-color: red;
}

```

> 编译后css：

```
    .size,
    .box{
        width: 100px;
        height: 100px;
    }
    .box {
        background-color: red;
    }

```

### 7、计算

> less ：
```
    .box2{
        //多个数字参与运算，有一个值以上带单位
        width: 1000px/2;
        height: 20*10px;
        border-width: 20-18px;
        border-radius: 10+5px;
        margin: (10-5px)*20;  // 可以通过（）提升运算的优先级
    }
```

> 编译后css:

```
    .box2 {
        width: 500px;
        height: 200px;
        border-width: 2px;
        border-radius: 15px;
        margin: 100px;
    }
```


## calc函数
> css3中提供的运算函数，不兼容低版本浏览器
> 支持加减乘除运算，运算符两边需要添加空格
```
    width:calc(100% - 200px);
```