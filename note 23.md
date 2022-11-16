## BFC?
- BFC (block fomatting context)块级格式化上下文，是页面中的一个渲染区域，有一套规则规定块级元素如何布局，和其他元素中间的关系。

- 生成BFC?
 - html 根元素
 - float:left/right;
 - display:inline-blcok;
 - overflow:auto/hidden/scroll; 
 - position:absolute/fixed;

- 规则？
 - 块元素垂直方向的距离由margin决定，处于同一个BFC区域的相邻元素的bfc会发生重叠。  
 - bfc区域不会和浮动元素重叠
 - 计算bfc高度，浮动子元素也会参与计算
 - 块元素垂直排列
 - bfc中的子元素左外边距和包含块的左边界相接触，即使浮动也是如此。
 - bfc独立，内部不会影响外部,外部也不影响内部

- 解决的问题？
 - 外边距折叠（塌陷）  （父子、兄弟） 
 - 实现两栏或三栏自适应布局，防止文字环绕图片
 - 清除浮动

## 两栏

```
bfc方式
左侧固定宽度，绝对定位，右侧自动宽度+margin-left
```

## 三栏

```
bfc方式 ：  .left .right .center
圣杯和双飞翼

结构： .mian .left .right
.mian { width:100%; float:left;}
.left{width:200px;float:left;margin-left:-100%;}
.right{width:300px;float:left;margin-left:-300px;}

圣杯：
   父级.container{ padding:200px 0 300px 0}; 
   .left{
       position:relative; left:-200px;
   }
    .right{
       position:relative; right:-300px;
   }


双飞翼：
    给.mian 添加子元素.mian-inner{
        margin:200px 0 300px 0;
    }

```


## 等高布局
- 多列布局，其中一列变高，其他几列等高变化
### 方法一：利用内外边距相抵消的原理，给每一列设置 padding-bottom:10000px;把背景撑开，同时给每一列添加margin-bottom: -10000px; 抵消padding的占位。
- 优点： 机构简单，兼容性比较好，缺点是伪等高, 需要合理控制marign-bottom和padding-bottom

### 方法二：
- 生成套娃式的三个盒子abc，最里面的盒子c包含左中右三个兄弟盒子，他们设置左浮动。而给abc设置背景色，给bc设置左外边距。
- 要给盒子c设置伪元素去除浮动塌陷。这里不可以使用overflow：hidden来占位，因为这样会除了可以生成bfc来包含浮动元素以外，还会因为隐藏溢出元素而让left和center失效