## 复习
- 盒模型
```
    内容：  width、height
    内边距 ： 
        padding:10px;  四个方向
        padding:10px 20px;  上下  左右
        padding:10px 20px 30px;  上  左右   下
        padding:10px 20px 30px 30px;  上  右   下   左
        padding-top
        padding-bottom
        padding-left
        padding-right
    边框:
        border:2px solid red;
        border-width:2px;
        border-style:solid/dashed/dotted/double
        border-color:red;
        border-top
        border-bottom
        border-left
        border-right
        border-top-width
        border-top-style
        border-top-color
    外边距: 
        margin:10px;  ....
        margin-top  ....
        margin:0 auto;  
        负值

    特殊问题：
        1、父子：父元素没有border/padding/float/position/overflow,子元素得margin-top会把父元素一块拉下来
        解决： 1、给父元素添加1px的上border或padding,子元素margin-top减去1px
            2、给父元素加padding-top 代替给子元素加margin-top的效果
        2、兄弟：上一个设置margin-bottom：60px,下一个设置margin-top：40px; 会发生合并，值以数值大的为准 （60px）

```
- 盒子类型转换
```
块级：
    默认宽度占满父级（内容+水平padding+水平border+水平margin）,高度由内容撑开
    可以设置宽高，可以设置所有盒模型属性
行内：
    默认宽高由内容撑开（line-height无法撑开背景）
    不能设置宽高及垂直方向的盒模型，水平盒模型属性可以设置
行内块：

    默认宽高由内容撑开
    可以设置宽高，可以设置所有盒模型属性 (margin:0 auto;无效)

display:block;  块级
display:inline;  行内
display:inline-block; 行内块
display:none;  隐藏


.box{
    font-size:0;
    line-height:0;
}
span{
    font-size:14px;
    line-height:40px;
    height:40px;
    display:inline-block;
}

<div class="box">
    <span>1</span>
    <span>2</span>
    <span>3</span>
</div>


居中：
    块元素本身在父级元素中居中：给块元素 margin:0 auto;
    块元素内部的内容（行内元素、行内块元素）居中，给块元素设置text-align:center;

```


## css三大特性

- 1、层叠性

    所谓层叠性，指的是浏览器处理样式冲突的一种能力
    样式不冲突不层叠
    样式冲突，以最后定义的为准（就近原则）
 
- 2、继承性
    > 继承表示子元素可以使用父元素的某些样式，比如文本、字体相关，只要给父级设置，子元素默认值和父级一样
    > 恰当使用继承，可以降低代码的复杂度
    - 以下属性默认继承：
    ``` 
        text-align
        text-indent
        text-decoration
        color
        font-size
        font-family
        font-style
        font-weight
        line-height 
        letter-spacing
        word-spacing
    ```
    - 其他属性通过inherit这个值可以实现手动继承
    ```
        width:inherit;
        border:inherit;
    ```
    > 注意： 块级元素width不是默认继承，背景颜色background-color默认是透明也不是继承
    > 注意： a标签的颜色和文本修饰默认不会继承，需要选中a标签才能修改

- 3、优先级
    > 行内样式优先级最高
    - 基本选择器的权值，权值越大，优先级越高
    ```
            选择器                权值
        *（通配符）                0  
        tagName（标签选择器）       1 
        .class（类选择器）\伪类     10
        #id (ID选择器)           100
        行内样式                 1000

    ```
    - 复合选择器的权值多数情况把组成这个复合选择器的基本选择器的权值相加 (特殊情况：群组选择器是单个计算不会叠加)
    - 选择器权值相同，后定义生效
    
    ```
        后代  .box div  (10 + 1 = 11)
        子代   .box>div  (10 + 1 = 11)
        群组   h1,.box  不会相加，单个计算 h1 1   .box 10
        交集   div.box  (1 + 10 = 11)

    ```
    - 特殊情况：!important 命令可以把样式优先级提升最高，比行内样式优先级更大，不推荐使用

## html表单
- 表单是网站用来收集用户信息的
- 1、表单域 form （块级）: 表示用来规定表单的一片区域，里面用来放各种表单元素
- 表单域属性： 
    - action: 用来规定表单的提交地址
    - method:用来规定表单的提交方式
        - get : 默认提交方式, 会把表单数据以键值对形式，多组用&拼接在一起，通过地址栏进行传递，安全性不好，因为地址栏可容纳的数据大小有限制的，所以可能造成数据丢失
        - post : 推荐使用的方法，安全性更好，理论上没有大小限制
```
    <form action="" method="" >
        ...
    </form>
```
- 2、表单元素：(行内块)
    - ①input标签
    ```
        <input type="text" name="username">   普通文本框
        <input type="password" name="psd">  密码框
        <input type="radio" name="gender" value="male">  单选按钮
        <input type="submit" value="注册">  提交按钮   
        <input type="checkbox" name="hobby" value="coding"> 复选框
        <input type="file" name="file">  文件域
        <input type="reset" value="清空表单">  重置按钮
        <input type="button" value="普通按钮"> 普通按钮
        <input type="image" src="图片路径"> 图片提交按钮
        <input type="hidden" name="hid"> 隐藏域,不显示但是可以携带数据
    ```
    - ② 下拉列表
    ```
        <select name="city">
            <option value="aa">AA</option>
            <option value="bb">BB</option>
            <option value="cc">CC</option>
        </select>
    ```    
    - ③ 文本域（多行文本）
    ```
        <textarea name="des" cols="30" rows="20"></textarea>
        - cols ： 规定输入文本列数
        - rows ： 规定输入文本的行数
    ```
- 3、表单元素属性说明
    - 1)、type用来定义输入框的不同类型
    - 2)、name属性用来规定表单字段名，如果不设置这个输入框的内容无法随表单一起提交到后台
        - 多个单选按钮想要有互斥效果，name属性值必须相同
    - 3)、value 用来给表单元素定义值
        - 单选按钮(radio)、复选框(checkbox)、下拉列表的选项(option)必须要设置value属性，表示选项所代表的值
        - 提交按钮(submit)、重置按钮(reset)、普通按钮(button)设置value属性表示修改按钮上的文字
        - 文本框(text)、密码框(password)、隐藏域(hidden)，用value设置默认值
        - 文件域flie和textarea不能设置value
    - 4)、maxlength="10" 用于规定输入框允许输入的最大字符个数
    - 5)、disabled="disabled"  设置表单元素为禁用状态, 不能编辑，也不能被提交
    - 6)、readonly="readonly"  设置表单元素为只读状态, 不能编辑，可以被提交
    - 7)、checked="checked"  设置单选按钮和复选框默认选中
    - 8)、selected="selected"  设置下拉列表的选项默认选中
    - 9)、size="2"  规定下拉表默认显示项目的个数
