## 复习
1、html5最新标准
浏览器支持情况：ie9+部分支持 ， 标准浏览器新版本支持
语法变化： 
    标签可以不闭合
    属性值可以不叫引号
    属性名和属性值相同，省略属性值
    引入样式link可以不加type
增加的模块： 语义化标签、智能表单、多媒体（音视频）、canvas绘图，svg矢量图，web存储，地理定位...
删除一些标签


2、语义化标签

结构化：
header 
footer 
main  兼容不好
nav  
article
aside
section
hgroup 
figure  
figcaption 

其他：
time   `<time datetime="2020/4/2">XX节日</time> <time>2020/4/2</time>`
mark

3、兼容处理

引入html5shiv.js
<!--[if lt ie 9]>
  <script src="http://....html5shiv.js">
<![endif]-->

4、表单新元素

 color
 number
 range
 tel
 email
 search
 date
 time  
 datetime 
 datetime-local 
 week
 month
 url
```


<input type="text" list="list1">
<datalist id="list1">
    <option value="aa">AA</option>
    <option value="aa">AA</option>
    <option value="aa">AA</option>
    <option value="aa">AA</option>
</datalist>

```
5、新增属性
list
min、max、step
required
pattern 
placeholder
autofocus
autocomplete = "on/off"
form 
multiple

6、音频
```
    <audio src="" controls loop muted></audio>
```
7、视频
```
    <video src=""  controls loop muted width="" height="" poster=""></video>
```



## 音视频资源 source标签
> 为音频和视频提供多种格式的资源文件，浏览器会识别第一个能够支持的视频格式进行播放

```
    <audio controls>
        <source src="../0401/videoAudio/nada.wav" type="audio/wav">
        <source src="../0401/videoAudio/butterfly.ogg" type="audio/oggg">
        <source src="../0401/videoAudio/hanmai.mp3" type="audio/mp3">
        您的浏览器不支持音频
    </audio>
```

## 删除的标签(了解) 不建议使用
```
    font
    basefont
    center
    big 无语义
    s 无语义
    u 无语义
    strike 删除线
    dir 目录列表
```

## CSS3

1、简介
是CSS的最新版本，在CSS2.1基础上进行增补与修改。

2、CSS3新增模块  （记住）
选择器、边框属性、背景属性、文本效果、2D/3D转换、动画、多列、弹性盒布局、用户界面

3、浏览器兼容情况：  ie9+、标准浏览器新版本

4、渐进增强、优雅降级
- 渐进增强： 针对低版本的浏览器构建页面，保证最基本的功能，然后再针对高版本的浏览器进行效果和交互的优化，从而达到一个良好的用户体验
- 优雅降级：一开始就实现一个良好的体验和完整的功能，再针对低版本浏览器做兼容处理

5、浏览器私有前缀
> 浏览器私有前缀是浏览器厂商为了表示对一些css3属性提前支持，但是属性尚未成为标准，如果属性成为标准之后，就不需要再加前缀
```
    -webkit-  : 老版本chrome、safari
    -moz- : 火狐浏览器
    -o-:  欧鹏浏览器
    -ms- : IE浏览器
```

> 自动添加私有前缀的插件  Autoprefixer
> 用法：   编写.css 文件，然后 F1 -- > Autoprefixer:run

## 新增选择器
- 整个中括号的权值是10
### 属性选择器
（不只有class是一种属性，style，type，width都是属性）
- css2的属性选择器
  - 1、[attr] : 选择带有attr属性的标签（可以用引号包起来：["attr"]
  - 2、[attr=val]: 选择attr属性值等于val的标签 
  - 3、[attr~=val]: 选择attr属性值词列表中包含val单词的标签（有多个属性词，就必须用这个才可以修改样式）
- css3的属性选择器
  - 1、[attr^=val]: 选择attr属性值以val开头的标签  
  - 2、[attr$=val]: 选择attr属性值以val结尾的标签
  - 3、[attr*=val]: 选择attr属性值里面包含val字符的标签

### 结构伪类选择器
  - 1、:first-child: 选择同级元素中的第一个  （span:first-child 表示是span而且是第一个子元素，而不是表示，是span而且是有span标签的第一个子元素） 
  - 2、:last-child : 选择同级元素中的最后一个
  - 3、:nth-child(n): 选择同级元素中的第n个
    - :nth-child(2n) : 选择同级元素中第偶数个元素
    - :nth-child(2n+1) : 选择同级元素中第奇数个元素
  - 4、:nth-last-child(n) : 选择同级元素中的倒数第n个

  - 5、:first-of-type : 选择同级同种类型标签中的第一个
  - 6、:last-of-type:  选择同级同种类型标签中的最后一个
  - 7、:nth-of-type(n) :   选择同级同种类型标签中的第n个
  - 8、:nth-last-of-type(n): 选择同级同种类型标签中的倒数第n个


### 表单状态伪类选择器

 - :enabled     选择可用状态的表单元素
 - :disabled    选择禁用状态的表单元素
 - :checked    选中状态的单选和复选框
 - ::selection   选择用户选中的元素部分内容（比如说手动选中一行字）


- 以上选择器的权值都是10
