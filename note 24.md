## 复习
- 兼容问题
- 1、ie钟图片出现边框
```
    img{
        border:none;
    }
```
- 2、背景简写兼容

```
    background:url() no-repeat center;

```
- 3、透明度兼容

- 4、其他更低版本兼容
- ie6以下小高度容器  （font-size:0;line-height:0;overflow:hidden）
- ie6中li浮动产生双边距 （_display:inline）
- ie7以下子元素相对定位，父元素overflow:hidden;失效  （父元素也添加相对定位）
- ie7以下块元素转行内块，不在一行显示  （*display:inline;*zoom:1;）
- ie7以下li子元素中有两个以上浮动，li之间出现空白间距  （li{vertical-align:top}）

- csshack
- 条件hack
```
<!--[if gt ie 8]>


<![endif]-->

- gt  大于
- gte  大于等于
- lt   小于
- lte  小于等于

```
- 属性
color:black;
_color:red;/*ie6识别*/
*color:yellow;  /*ie7以下识别*/
color:grren\0;  /*ie8以上*/

- 选择符
*html .box{  /* ie6 以下*/

}
*+html .box{  /*ie7*/

}


## 滑动门技术
> 为了使特殊形状得背景能够自适应元素中文本内容得多少，出现滑动门技术。 比如微信导航。
主要使利用背景定位和padding撑开盒子宽度。
> 具体实现：先给a标签，给a背景图定到左边，给a添加合适得padding-left，再往a当中添加span标签，给span标签设置同样得背景定位在右边，给span添加padding-right  (a和span都要转换成块级)



## 网页tdk设置
- title设置： 网页的标题，尽量强调重点的内容，首页一般写整个网站的标题和整体概述，其他页面概括本页面的主题，（注意：每个页面的标题不要相同）
- description 设置： 网页描述，需要高度概括网页内容，切忌过分堆砌，不能太长，每个页面不能相同 （不是必须设置，根据具体页面要求）
- keywords 设置：网页关键字，列举出几个页面的重要的关键字

```
    <title>XX商城-手机,电脑...</title>
    <meta name="description" content="....">
    <meta name="keywords" content="...">
```
- 网站icon设置
- 生成icon图标  http://www.bitbug.net/
```
    <link rel="shortcut icon" type="image/x-icon" href="favicon.ico">
```

## 重置样式
- input textarea这些表单标签默认不会继承父级字体样式
- h标签不会默认继承父级字体大小
- input有一个outline属性，默认点击时会产生蓝色的阴影。可以设置outline：none;  取消这个边框。

## 命名参考
- 驼峰命名法和连字符命名法


## tips
- 文档流中的文字，表单和图片是一个序列，浮动不会脱离文档流。
