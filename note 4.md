## 复习

- 标签分类： 
    块级：h1-h6 、 p 、 div 、 ul 、dl 、dt 、dd 、 ol 、li 、 hr
    行内： span 、  i 、em 、 b 、strong 、 sub 、sup 、del  、 a
    行内块级:  img

- 链接： 
```
    <a href="目标页面的相对路径" target="_self"> </a>
    <a href="目标页面网址" target="_blank">  </a>

    锚点链接：
    <h3 id="f1"> ... </h3>
    <a href="#f1"> ... </a>

    <a href="页面的路径#f1"> ... </a> 

```

- 表格：
```
    <table border="1" style="width:800px;border-collapse:collapse;" cellsapcing="0">
        <caption> 表格标题 </caption>
        <thead>  
            <tr>
                <th colspan="3">  </th>
            </tr>
            <tr>
                <th>表头1</th>
                <th>表头2</th>
                <th>表头3</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td> </td>
                <td> </td>
                <td> </td>
            </tr>
            <tr>
                <td> </td>
                <td> </td>
                <td> </td>
            </tr>
        </tbody>

        <tfoot>
            <tr>
                <td> </td>                
                <td> </td>                
                <td> </td>                
            </tr>
        </tfoot>
    </table>


    - 合并行（纵向）： rowspan = "3"
    - 合并列（横向）： colspan = "2"

    - 列宽分配规律： 按照每一列里面内容最多的单元格的比例分配 ，行高同理
    - 可以通过给单元格设置宽度来改变列宽
```

特殊字符

```
    &nbsp;  空白
    &gt;   >
    &lt;   <
    &amp;  &
    &copy;  ©
    &reg;   ®
```

- 语义化
```
    什么是语义化？
    用合理的标签去格式化文档内容,比如 标题用h标签，段落用p标签，重要图片添加  alt 
    好处？
    - 没有css也能表现出良好的结构
    - 具有良好的可读性，有利于团队开发维护
    - 有利于用户体验  
    - 有利于搜索引擎优化
```


## CSS
- Cascading Style Sheets   层叠样式表
- 是用来规定网页样式的语言

### css三种引入方式
- 1、行内样式 ： 在标签上添加style属性，通过style属性添加各种样式
  - 不符合w3c建议的结构和表现相分离的原则，结构不清晰
  - 会产生大量代码冗余，代码的复用率和可维护性都不好
  - 项目中不推荐使用
```
  <div style="width:100px;height:100px;background-color:red;"></div>
```

- 2、内嵌式 : 在head标签末尾添加一个style标签，在style标签之间写入css语法

```
    <head>
        <style>
            p{
                width:100px;
                height:100px;
                background-color:red;
            }
        
        </style>
    </head>
```











