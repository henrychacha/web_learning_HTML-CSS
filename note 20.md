## 复习

- 字体 font
```
font-size:12px;
font-weight:100-300/400-500/600-900/normal/bold;
font-style:normal/italic;
line-height:30px/2;
font-family:"宋体","";

font: italic bold 12px/2 "宋体"; 
font: 12px "宋体";
```  

- 文本
```
color
text-align:left/center/right
text-decoration: none/underline/overline/line-through;
text-indent:2em;

```
- 其他
```
letter-spacing:10px;  "1 2 3 a b c 汉 字"
word-spacing:10px;  "world    hello    ujiuye   汉字   "
```
- 颜色和单位

```
    px  
    em 
    rem    
    百分比

    英文单词
    十六进制  #000   #fff   #333  #666   #999
    rgb(0-255,0-255,0-255)  rgb(255,255,255)  rgb(0,0,0)
    rgba(0-255,0-255,0-255,0-1)
```

## 1、复合选择器  
- 1）、后代选择器
> 语法： selector selector selector...
> 基本选择器之间用“空格”分隔
``` 
    .box div{  /* 选择.box标签后代当中所有div标签*/

    }
```
- 2）、子代选择器
> 语法：selector>selector>selector...
> 基本选择器之间用“大于号”分隔
```
    .box>div{  /* 选择.box标签直接子代中所有div标签 */

    }
```
- 3）、并集选择器（群组选择器）
> 语法:selector,selector,selector...
> 基本选择器之间用“逗号”分隔
``` 
    #box,.red,h3,#box p{  
        /*把一下几个选择器匹配的元素同时选中*/
        #box
        .red
        h3
        #box p

    }
```
- 4）、交集选择器
> 语法:selector1selector2...
> 多个选择器之间不添加其他符号
```
    div.red{ ... }   /* 选择标签名为div并且类名中包含red这个单词的标签   */
```

## 2、状态伪类（链接）
- :link  链接未访问状态
- :visited  链接访问过后
- :hover   链接悬停状态
- :active  链接的激活状态（鼠标按下）

```
        a:link{
           color: aqua; 
        }
        a:visited{
            color: brown;
        }
        a:hover{
            color:yellow;
        }
        a:active{
            color: pink;
        }

```

- :hover不仅可以表示链接的悬停，其他的标签也可以使用
- hover跟在谁后面就是悬停在谁上面，谁靠近中括号，改变的就是谁

```
    .box:hover{  }   鼠标悬停在.box上，改变.box自身的样式  
    .box :hover{   }   鼠标悬停在.box的后代上，改变该后代的样式,
    .box span:hover{   }  鼠标悬停在.box的后代中的span上，改变span样式
    .box:hover span{   }   鼠标悬停在.box上，改变后代中span的样式
    .box:hover span,.box:hover a{ }鼠标悬停在box上，span和a都变
    .box:hover *{  } 鼠标悬停在.box上，后代都变
```

## 盒模型
> 在css中把每个标签可以看作是一个盒子，这个盒子有四层结构，分别是内容、内边距、边框、外边距。
- 1、第一层是内容（content）, 内容的尺寸由width(宽)和height(高)共同决定
- 2、第二层是内边距(padding),内边距也可以叫（内补丁或者内填充），是指盒子的边缘和内容之间的距离，这段距离会显示背景，但是不会显示内容
```
    padding-top:10px; 上内边距
    padding-bottom:10px; 下内边距
    padding-left:10px; 左内边距
    padding-right:10px; 右内边距
```
- 3、第三层是边框(border),边框是指盒子边缘的线条
    > 边框简写属性 border:border-width border-style border-color
    border-width:边框宽度
    border-style:边框风格
        - solid 实线
        - dashed 虚线
        - dotted  点线
        - double  双实线
    border-color：边框颜色
```
    border:30px solid black;
    border-top:5px solid yellow;  /* 上边框 */
    border-bottom: 3px dashed green;   /* 下边框 */
    border-left: 2px dotted blue;   /* 左边框 */
    border-right: 5px double pink;   /* 右边框 */

    border-right: 0;   /*去掉边框两种写法*/
    border-left: none;
```

- 4、第四层是外边距（margin）,是指盒子和相邻元素或者父元素之间的距离
```
    margin-top:10px;  上外边距
    margin-bottom:10px;  下外边距
    margin-left:10px;  左外边距
    margin-right:10px;  右外边距

    margin:0 auto;  块元素水平居中
```
 


