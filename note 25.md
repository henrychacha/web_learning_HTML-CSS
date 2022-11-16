## 常见兼容问题处理
### 1、ie中图片边框问题
> ie中图片放在a标签中会显示边框
- 解决方法：
```
    img{
        border:none;
    }
```
### 2、ie8以下背景简写属性语法兼容
> 背景简写属性的每个值之间应该添加空格，如果出现如下遗漏空格的情况，标准浏览器时可以正常显示，但是再ie8及以下浏览器就不能显示图片
```
    background: url("...")no-repeat center;
```
- 解决方法：按照标准语法，在多个值之间添加空格
```
    background: url("...") no-repeat center;
```
### 3、透明度兼容
- rgba()  透明颜色   ie低版本不支持
- opacity:0.5;   标准浏览器支持，ie低版本不支持
- filter:alpha(opacity=50) ie支持


### 4、ie低版本的兼容问题（了解）
> ① ie6及以下浏览器，定义小高度的盒子失效
- 解决方法：
```
    .box{
        height:1px;
        font-size: 0;
        line-height: 0;
        overflow: hidden;
    }
```
> ② ie6浏览器中，标签浮动产生双倍外边距。
- 解决方法：给浮动元素添加 _display:inline;
```
    li{
        float:left;
        margin-left:10px;
        _display:inline;    /* 针对ie6有效 */
    }
```
> ③ ie7及以下浏览器，子元素设置相对定位，父元素的overflow:hidden;失效
- 解决方法：给父元素也添加position:relative; 
```
        .parent{
            position: relative;
            overflow: hidden;
        }
        .child{
            position: relative;
            left: 150px;
        }
```
> ④ ie7及以下浏览器，块元素转行内块，不在一行显示
- 解决方法： 
```
    div{
        display:inline-block;
        *display:inline;
        *zoom:1;
    }
```
> ⑤ ie7及以下浏览器，li中出现两个及以上子元素浮动时，li之间出现空白问题
- 解决方法：给li添加vertical-align:top;

```
    li{
        vertical-align:top;
    }
```

# 补充
> 如果需要从服务器环境中打开页面，可以安装插件  live server , 打开页面选择 open with live Server


## css Hack技术
-  css Hack是通过一些特殊方式去处理不同浏览器之间的兼容问题，某些情况使用css Hack处理兼容能事半功倍。滥用css Hack会影响页面性能，并且维护困难，所以应当避免大量使用css Hack技术。

### 1、条件Hack
- ie从10及以上的版本都不支持 条件hack，所以以下代码在ie9及以下才会显示
```
    <!--[if ie]>
        <p>这个段落只有ie会显示</p>
    <![endif]-->
```

- 关键字：

> 大于 gt   大于等于  gte
```
    <!--[if gt ie 8]>
        <p>这个段落只有ie8以上会显示</p>
    <![endif]-->
```
> 小于 lt    小于等于  lte

```
    <!--[if lt ie 8]>
        <p>这个段落只有ie8以下会显示</p>
    <![endif]-->

```
> 等于 

```
    <!--[if ie 8]>
        <p>这个段落只有ie8会显示</p>
    <![endif]-->
```


### 2、属性级hack
> 属性级hack就是给css的属性添加特殊符号来处理不同版本浏览器的兼容

```
    _ : ie6及以下版本浏览器识别
    * ：ie7及以下版本浏览器识别
    \0: ie8及以上浏览器识别

    .box{
        background-color: red;  /*所有浏览器识别*/
        _background-color:yellow;
        *background-color:lightblue;
        background-color: hotpink\0;
    }
```

### 3、选择符级hack
*html   选择ie6及以下浏览器
*+html  只选择ie7浏览器 

``` 
      .box{
           background-color: red;
       }
      *html .box{
            background-color: yellow;
      }
      *+html .box{
            background-color: lightblue;
      }
```



* 补充ps操作

ctrl+T  ： 自由变换工具，改变图层大小

## 静态大banner图优化
- 从重要内容使用img标签，修饰的图案使用背景图片这个原则，需要把中间部分切成图片 ，两边剩余的部分作为大背景图
- 中间部分可以再划分成几个小切片，为了防止网络情况不好大图请求超时


