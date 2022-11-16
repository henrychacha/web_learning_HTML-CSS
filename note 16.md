## 复习
### css三大特性
层叠性: 样式冲突，层叠（就近原则），不冲突，不层叠
继承性: 
    自动继承： 文字
    ```
        text-align  text-indent  text-decoration color font-size  font-family font-weight font-style line-height letter-spacing  word-spacing 

        a标签 ： color  text-decoration  默认不会继承
        背景颜色和宽度不是默认继承
    ```
    手动继承： inherit 

优先级:
    行内样式           1000
    #id                100
    .class/:hover       10
    div                  1
    *                    0 

复合选择器
    .box div           10 + 1
    .box>.red          10 + 10
    div.box             1 + 10
    h2,.box,p          分别计算

权值越大优先级越高，权值相同遵循就近原则
color:red !important; 提升至最高优先级

## 表单
### 表单域(块)
- form： 区域，里面放表单元素
    - action: 规定表单提交地址
    - method: 规定表单提交方式
        - get : 地址栏传递，安全性不好，大小有限制
        - post : 相对安全，大小没有限制
### 表单元素（行内块）
- input
```
    <input type="text" name="user"> 
    <input type="password" name="psd"> 
    <input type="radio" name="gender" value="male"> 
    <input type="radio" name="gender" value="female"> 
    <input type="checkbox" name="" value=""> 
    <input type="submit" value="注册">
    <input type="reset">
    <input type="button">
    <input type="image" src="">
    <input type="file">
    <input type="hidden">
```
- select
```
    <select name="">
        <option value="aa">AA</option>
        <option></option>
        <option></option>
    </select>
```
- textarea
```
    <textarea cols="" rows="">XXXX</textarea>
```
- 属性：
```
    type 
    name:字段名
    value: 值
        - 单选、复选、下拉列表选项必须设置，代表选项的值
        - 设置按钮的文字
        - 文本框、密码、隐藏域，用来设置默认值
        - file、textarea 不能设置value
    disabled="disabled" 禁用 
    readonly="readonly" 只读
    checked="checked"  单选、复选 默认选中
    selected="selected"  下拉列表选项选中
    maxlength="10"  最大字符个数
    size="2"  设置下拉列表显示的选项个数

```

## 垂直对齐 vertical-align

- baseline  默认值，基线对齐
- middle  中线对齐
- top  顶部对齐
- bottom 底部对齐

- 1、图片和文字中线对齐，给图片设置vertical-align:middle;
```
    css:
        .box img{
            width:150px;
            vertical-align: middle;
        }

    html:

    <div class="box">
        文字pgP 
        <img src="https://dss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo_top-e3b63a0b1b.png" alt="">
    </div>

```
2、行内元素中线对齐，给两个行内元素都设置vertical-align:middle;
```
    css：
        .span1,.span2{
            background-color: red; 
            vertical-align: middle;
        }
        .span1{
            font-size: 30px;
        }
    html:
     <span class="span1">span1</span>
     <span class="span2">span2</span>
```
3、行内块元素中线对齐，给两个行内块都设置 vertical-align:middle; 
```
    css：
        .span3,.span4{
            display: inline-block;
            width: 100px;
            height: 100px;
            background-color: yellow;
            vertical-align: middle;
        }
    html:
     <span class="span3">span3</span>
     <span class="span4">span4 <br> span44</span>
```


## 浮动

- 布局方式：文档流、浮动布局、层布局（定位）
- 文档流布局： 表示标签按照本身特点在文档中排列，比如块元素从上往下一次排列、行内元素从左往右

- 1、float:left; 左浮动
> 左浮动的元素会尽可能往左走，直到碰到父级元素的左边缘，或者相邻浮动元素就停下来    
> 左浮动的元素会脱离文档流（标准流），不占位 
> 多个左浮动的元素从左到右依次排列 

- 2、float:right;右浮动
> 右浮动的元素会尽可能往右走，直到碰到父元素的右边缘，或者相邻浮动元素就停下来
> 右浮动的元素会脱离文档流，不占位
> 多个右浮动的元素从右到左依次排列

- 3、float:none;取消浮动
> 让元素回到文档流中正常布局

