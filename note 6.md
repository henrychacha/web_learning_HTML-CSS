## 复习

- 标签分类：
    - 块级标签： 
    ```

        hr 分割线  
        div 区块、盒子
        p   段落
        h1-h6   标题   
        ol  有序列表    type="1/A/a/I/i"
        ul   无序列表    type="desc/circle/square"
        li   无序列表和有序列表的项目
        dl   定义列表
        dt   放名词或术语
        dd   放描述或者说明

    ```
        - 独占一行（多个块标签垂直方向排列）
        - 可以设置宽度和高度
        - text-align:center  有效
    - 行内标签: 
    ```
        span  : 无语义标签，给一段文字中的指定文本设置特殊样式
        i  :  样式斜体 
        em  :  斜体，并且强调
        b  : 样式加粗
        strong  : 加粗并且强调
        sub ：下标
        sup  ：上标
        del : 删除文本
    ```
        - 多个标签水平排列在一行
        - 不可以设置宽度和高度
        - text-align:center  无效

    - 行内块级标签  （img）
        - 多个行内块级标签水平排列在一行
        - 可以设置宽度和高度
        - text-align:center  无效
- 图片
```
    <img src="图片路径" alt="替换文本" width="200" height="200" style="width:200px;height:200px;">
```
- 相对路径
```
    src="./images/pic01.jpg"
    
    ./ : 当前目录,可以省略
    
    src="../images/pic01.jpg"

    ../ : 返回上一级目录
    ../../: 返回上两级目录

    src="/images/pic01.jpg"

    / : 开头的/ 代表根目录 

```
- 绝对路径
```
    src="C:/Users/A.../deskTop/XXX/1.jpg"
    src="http://www.baidu.com/XXX/2.jpg"
```


## 网页特殊符号

```
    &nbsp;    空格
    &gt;    大于符号    >
    &lt;    小于符号    <
    &amp;    &符本身    &
    &copy;   版权符     ©
    &reg;    注册商标   ®
```

## 链接 a  行内元素

- 1、本网站中的页面跳转
```
    <a href="相对路径" target="_blank" title="提示文字"> 链接文本 </a>
```
- 2、跳转到其他网站的页面 （友情链接）
```
    <a href="目标页面的网址" target="_blank"> 链接文本 </a>
```
- 3、锚点（锚记）链接 ：跳转到当前页面的指定位置
```
    <h3 id="f1"> ... </h3>
    <a href="#f1"> ... </a>
    跳转页面同时指定位置：
    <a href="./4、链接.html#floor2"> 跳转到链接页面的第2层</a>
```
- 属性说明：
    - href : 目标页面的地址
    - target : 在何处打开页面
        - _blank : 在新窗口中打开
        - _self : 默认值，当前窗口打开
    - title : 规定鼠标悬停在链接上的提示文本

- 图片链接

```
    <a href="http://www.ujiuye.com">
        <img src="http://www.ujiuye.com/statics/images/xibaopcimages/logo.png" alt="">
    </a>
```

## 语义化

- 1、什么是语义化？
    - 使用合理的标签去格式化不同的内容，比如标题应该使用 h 标签，段落用p标签，主要图片应当使用alt属性添加替换文本

- 2、语义化的好处？
    - 在没有css样式的情况下，页面也能表现出良好的结构
    - 语义化会使代码具有良好的可读性，便于团队开发和维护
    - 有利于用户体验 （比如 alt  、 title ）
    - 有利于搜索引擎优化（SEO） （良好的语义化可以和搜索引擎建立良好的沟通，有利于搜索引擎爬虫抓取更多有效信息，爬虫依赖于标签确定关键字的权重）

## 表格
### 1、表格相关标签
    - table  定义整个表格
    - tr  定义一行
    - td  定义表格的单元格（标准单元格）
    - th  定义表头单元格 （加粗居中）
    - caption  定义表格标题
    - thead  表格的头
    - tbody  表格的主体
    - tfoot  表格的底部
    > thead\tbody\tfoot 这些标签可以增强表格的语义化，对布局没有影响

    ```
        <table>
            <caption>学生成绩表</caption>
            <tr>
                <th>编号</th>
                <th>姓名</th>
                <th>分数</th>
            </tr>
            <tr>
                <td>01</td>
                <td>张三</td>
                <td>90</td>
            </tr>
        </table>
    ```
### 2、表格相关属性

    ```
        <table border="1" cellspacing="0" style="width: 300px;border-collapse:collapse;">
            ...
        </table>
    ```
- 1)、border 给表格整体添加边框（表格和单元格都有边框）
- 2)、border-collapse:collapse;  去除单元格之间的空白间距，并且把相邻边框合并成一个
- 3)、cellspacing="0"  ：去掉单元格之间的空白间距


### 3、合并单元格
- 合并列（横向合并）colspan = "2"
```
    <td colspan="2">  ... </td>
```
- 合并行（纵向合并）rowspan = "2"

```
    <td rowspan="2"> ... </td>
```

### 表格特点
 - 不设置表格宽度时，实际宽度由内容撑开
 - 如果给表格设置宽度width，表格的列宽会按照每一列当中内容最多的单元格的比例分配列宽，行高也是同理
 - 也可以通过给单元格设置 width和height调整整行或整列的宽度和高度
 ```
    <tr>
        <td width="80">4444</td>
        <td width="80">5</td>
        <td width="140">6</td>
    </tr>
    <tr>
        <td width="33.33%">4444</td>
        <td width="33.33%">5</td>
        <td width="33.33%">6</td>
    </tr>
 ```




