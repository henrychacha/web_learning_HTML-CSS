## 复习
CSS : Cascading style sheets  层叠样式表

- 三种引入方式
    - 行内 ：
        ```
            <div style="width:100px;height:100px;">
        ```
    - 内嵌
        ```
            <style>
                css语法：
                选择器{
                    样式声明1;  属性名:值;
                    样式声明2;   
                }
            </style>
        ```
    - 外链
        ```
            <link rel="stylesheet" href="./style.css">
        ```

- 选择器：
- 基本选择器
```
    *       通配符   所有标签   *{margin:0;padding:0;}
    tagName (div/p/h1)   标签选择器   

        <div class="red size100 ..." id="box1"></div>
        <div class="red size200 ..." id="box2"></div>

    .className        类选择器  
    #id     ID选择器   

```
## 文字相关属性
### 1、 text系列

- 1）text-align 文本对齐方式 

    - left  左对齐
    - right  右对齐
    - center  居中对齐
- 2）text-indent:2em 首行缩进
    em : 代表一个字的大小
- 3）text-decoration  文字修饰  
    - none   去掉修饰
    - underline  添加下划线
    - overline  添加上划线
    - line-through  添加删除线
- 4） color : 文本颜色

### 2、 font 系列

- 1）、font-size 字体大小  
- 2）、font-weight 字体加粗
        - 100-300  细
        - 400-500  正常
        - 600-900  加粗
        - normal   正常
        - bold     加粗
- 3）、font-style  字体风格
        - normal   正常
        - italic   斜体
- 4）、font-family  字体系列（族类）
        - 可以设置一个字体或多个字体
        - 多个字体用逗号分隔，浏览器会显示第一个能够识别的字体
    ```

    font-family: Helvetica Neue,Helvetica,Arial,"宋体",Hiragino Sans GB,Heiti SC,WenQuanYi Micro Hei,sans-serif;

    ```
- 5）、line-height  字体行高
    - 取值可以为具体的长度  30px
    - 也可以为font-size的倍数   比如2  代表font-size的两倍
    - 单行文本垂直居中可以设置line-height为盒子的高度

- 6）、font 字体简写属性
  ```
    font: font-style font-weight  font-size/line-height font-family;
    font: italic bold 20px/2 "宋体";
  ```
  > 字体简写属性，顺序不能随意更改
  > 可以省略不需要设置的属性, 至少保留font-size和font-family

### 3、其他

- 1）、letter-spacing  设置字符间距：英文字母、中文汉字
    ```
        p{
            letter-spacing:10px;
        }
    ```
- 2）、word-spacing  设置单词的间距
    ```
        p{
            word-spacing:10px;
        }
    ```
  
### 4、长度单位和颜色表示法
#### 单位
- 1）、px  像素
- 2）、em   相对单位，代表的是当前元素的font-size值  
- 3）、%    百分比   
- 4）、rem   1rem 等于页面的根元素的font-size值，也就是html标签的font-size

#### 颜色表示法
- 1）、英文单词  
- 2）、十六进制颜色表示法   #000000  #RRGGBB
    ```
        #ffffff   白色
        #000000   黑色
        #333333   灰色
        #666666   灰色
        #999999   灰色
    ```
- 3）、rgb()模式
    ```
    rgb(0-255,0-255,0-255)
    r : red 红色
    g : green 绿色
    b : blue  蓝色
    ```
- 4）、rgba()模式
    ```
    rgba(0-255,0-255,0-255,0-1);
    r : red 红色
    g : green 绿色
    b : blue  蓝色
    a : alpha 透明度 0-1  0表示完全透明  1表示不透明  0.X 半透明

    ```
