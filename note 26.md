## 图片下方的空白间距
- 图片下方默认会出现 4px的空白（随着父级的字体大小有所不同）

- 解决方法1： 给图片的父级添加 font-size:0;line-height:0;
- 解决方法2： 给图片添加vertical-align属性，值不为baseline;
- 解决方法3： 把图片转换成块级元素  display:block;

## 元素可见性

- visibility:visible;  元素可见
- visibility:hidden;  元素不可见，隐藏，依然占位
- display:none;  隐藏元素，不显示也不占位

## 单行文本溢出显示省略号
```
        .p1{
            width: 200px;
            background-color: red;
            white-space: nowrap;/* 文本强制不换行 */
            text-overflow:ellipsis;  /* 文本溢出显示省略号 */
            overflow: hidden; /* 必须要结合盒子溢出隐藏 */
        }
```
## 多行文本溢出显示省略号
- 方法一：利用webkit内核的扩展属性（因为只有webkit内核支持，效果比较好，兼容性不好）
```
        .p2{
            width: 200px;
            background-color: royalblue;
            overflow: hidden; /* 必须要结合盒子溢出隐藏 */
            text-overflow: ellipsis;/* 文本溢出显示省略号 */
            display: -webkit-box;  /* 必须要结合的属性，讲元素设置为弹性盒模式 */
            -webkit-line-clamp: 4;  /*  必须要结合的属性，设置文本显示的行数 */
            -webkit-box-orient: vertical;  /*  必须要结合的属性，设置弹性盒对象的子元素，排列方式为垂直 */
        }
```
- 方法二： 利用伪元素模拟省略号，兼容性相对好，但是效果不太好
```
        .p3{
            position: relative;
            width: 240px;
            height: 90px;/* 盒子高度要设置为line-height的倍数  （表示要显示的行数） */
            background-color: gold;
            line-height: 30px;
            overflow: hidden;  /* 盒子溢出隐藏 */
        }
        .p3::after{
            position: absolute; /* 通过定位设置到父元素的右下角 */
            right:0;
            bottom: 0;
            content: '...';  /* 伪元素添加 ... 显示省略号 */
            /* background-color: gold; */
            padding-left: 20px;
            background: linear-gradient(to right,transparent,gold 60%) ;  /* 添加渐变色使文字逐渐隐藏*/
            <!-- 注意60%前不能加逗号,表示只有前60%是渐变，后面40%是纯色 -->
        }
```
## 标签的嵌套规则

- 1、块元素里面可以嵌套块元素、行内元素、行内块(特殊情况：一些特殊语义的块标签不能再嵌套块标签，比如：h1-h6 和  p标签里面不能再嵌套 div, 一些固定搭配的标签，不能随意嵌套其他的标签 比如：ul ,ol 直接子元素只能是li)
- 2、行内元素不能嵌套块级元素，可以嵌套行内和行内块元素( a标签里面可以套块元素，a标签里面不能再嵌套a标签 )





