# HTML5
## 简介
- 1、HTML5是html的最新的标准（版本）
- 2、浏览器支持：ie9+对html5新特性部分支持，新的主流浏览器（chrome、火狐\safari）
- 3、向前向后兼容，语法变化：
 - 标签可以自动闭合
 - 属性值可以省略引号
 - 属性值和属性名相同，可以省略属性值
 - 引入样式表link标签可以省略type
- 4、*增加了语义化标签、智能表单、音频视频（多媒体）、canvas绘图、svg矢量图、地理定位、web存储
- 5、删除掉一些标签

## 新增语义化标签
### 结构化标签
- 1、header标签
> 定义整个网页的头或者是某个模块的头部，一般放顶部导航、logo、标题、搜索栏等
- 2、footer标签
> 定义整个网页的底部或者是某个模块的底部，一般放版权信息，联系方式，底部导航等。
- 3、main标签（ie不兼容，不建议用）
> 定义整个页面的主体部分，建议只使用一次
- 4、article标签
> 定义页面中独立的文章区域：博客，新闻，评论...
- 5、nav标签
> 定义各种导航：顶部导航，底部导航，侧导航，翻页导航，路径导航等
- 6、section标签
> 定义页面内容的分区或者文章的分节，一般section里面由标题和内容组成
- 7、aside标签
> 定义和主题内容相关性不大的内容，比如侧边栏广告，推荐，侧边栏导航等
- 8、hgroup标签
> 定义标题组，把主标题和副标题组合在一起
- 9、figure标签
> 定义文章或者模块中独立的图片、图表、照片等
> 一个figure可以包含多个图片
- 10、figcaption 标签
> 和figure搭配使用，为图片提供标题
> 一个figure只能包含一个figcaption标题

### 其他标签
1、time标签
> 定义时间，行内标签
```
    <p>今天是<time datetime="2020/4/1">愚人节</time></p>   //如果不是直接包含的时间字符串，需要用datetime属性给time标签定义具体的时间
    <p> 双十一开抢时间<time>2020/11/11 11:11:11</time></p>  // 如果time标签之间写的是具体的时间，就不需要加datetime属性
```
2、mark标签
> 定义带标记的文本(高亮显示)，行内标签

### 兼容处理
> 因为新的语义化标签在ie低版本中会解析错误，样式布局不能正常展示
- 解决方法：
- 方法一：
    1、通过js创建新增的标签
    ```
         document.createElement('header');
         document.createElement('footer');
         document.createElement('nav');
         ...
    ```
    2、把结构化标签转换成块级
    ```
        header,footer,nav...{
            display:block;
        }
    ```
- 方法二：
  > 引入html5shiv.js插件   https://www.bootcdn.cn/html5shiv/
```
    <!--[if ie]>
    <script src="https://cdn.bootcss.com/html5shiv/3.7.3/html5shiv-printshiv.js"></script>
    <![endif]-->
```


## 表单新特性
### 新增的表单元素
- 1、color类型 ：颜色选取框
- 2、datetime类型：日期输入框
- 3、datetime-local类型： 本地日期时间输入框(年/月/日 小时：分钟)，自带日历操作控件，可输入可选择，格式比较规范
- 4、date类型： 日期输入框（年/月/日），自带日历操作控件，可输入可选择，格式比较规范
- 5、month类型： 月份输入框（年/月），自带日历操作控件，可输入可选择，格式比较规范
- 6、week类型： 一年中的第n周，自带日历操作控件，可输入可选择，格式比较规范
- 7、time类型：输入时间（小时：分钟） ，可以输入和使用箭头加减
- 8、email类型：输入邮箱格式的字符串，内置了邮箱格式规则验证
- 9、number 类型：输入数字，无法输入数字以外的字符，在移动端自动调出数字键盘
- 10、tel类型： 输入电话, 没有规则验证，可以输入任意字符
- 11、url类型： 输入网址格式的字符串，内置了网址格式规则验证
- 12、search类型： 搜索输入框，自带快速清空内容的 “×” 号 
- 13、range类型： 获得一个数值，在一个范围内用滑块去操作

- 14、datalist标签：专门给输入框提供选项列表
 - list属性用来绑定对应的列表
```
        <input type="text" list="list1">
        <datalist id="list1">
            <option value="AA">aa</option>
            <option value="BB">bb</option>
            <option value="CC">cc</option>
        </datalist>
```
- 15、聚焦:使用label标签：点击label标签即可触发input
```
 <label for="user">姓名</label>
 <input type="text" name="username" id="user">
```
### 新增属性
- 1、list属性：用来给输入框绑定对应的列表
- 2、min、max属性：分别定义number或者range类型的最小值和最大值
- 3、step 属性：用来定义number或者range类型的加减步长 
```
    <input type="number" min="0" max="10" step="2">
```
- 4、required 属性 ： 把表单元素设置位必填项
```
    <input type="text" required>
```
- 5、pattern 属性：用来定义表单输入的内容的规则
```
    <input type="tel" pattern="1[356789][0-9]{9}" name="tel">
```
- 6、placeholder属性： 给输入框定义提示占位符，当输入内容时消失，输入框为空的时候显示
```
    <input type="text" placeholder="请输入。。。">
```
- 7、autofocus 属性: 设置表单元素自动获得焦点,一般只能设置一个自动获得焦点的元素
```
    <input type="text" autofocus>
```
- 8、autocomplete 属性：设置表单元素的自动补全功能，on表示开启，off表示关闭
```
    <input type="text" autocomplete="on">
```
- 9、form属性： 给表单元素定义所属的表单域（form），用于把表单元素放在form以外时指定随哪个表单域一起提交数据

```
    <input type="text" form="loginForm">
    <form id="loginForm">
    </form>
```
- 10、multiple属性： 设置文件域和下拉列表支持多选

```
    <input type="file" multiple>
    <select multiple>
    </select>
```

* 注意： 新表单类型和属性在ie中支持情况不好，并且目前没有比较好的解决方案，pc端项目避免使用，目前主要是流行在移动端

## 多媒体

### 1、音频 audio

```
    <audio src="./videoAudio/hanmai.mp3" controls loop></audio>
```
> 属性： 
 - src="资源路径"： 用来引入音频文件的地址
 - controls : 用来调出控制器（播放暂停、进度、音量）
 - loop : 用来设置音频为循环播放
 - muted: 规定音频默认静音

### 2、视频
```
    <video src="./videoAudio/movie.mp4" width="800" controls loop poster="./img/pic.png"></video>
```  
>属性：
 - src="资源路径"： 用来引入视频文件的地址
 - controls : 用来调出控制器（播放暂停、进度、音量、全屏，画中画）
 - loop : 用来设置视频为循环播放
 - muted: 规定视频默认静音
 - width: 规定视频宽度
 - height: 规定视频高度
 - poster: 规定视频没有播放时显示的广告图（海报）

 - 视频的默认宽高由视频本身的大小决定

音频和视频还有一个属性叫做autoplay，值也是autoplay。会有自动播放的效果。这个属性在不同的浏览器中的支持情况不一样