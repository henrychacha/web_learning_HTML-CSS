## 移动端浏览器及内核

- 主流手机浏览器： 苹果、百度、qq、uc、360...
- 内核：大部分的核心都是webkit内核，不需要过多考虑新技术的兼容性（html5+css3都可以用）

## viewport（视口）设置

- 布局视口： 认为是html宽度，移动端一般是默认设置为一些固定的值（980或者1024），比屏幕宽度要大
- 视觉视口： 用户看到的网页区域，相当于屏幕的宽度
- 理想视口：布局视口对用户不友好，没有考虑到手机尺寸，所以苹果公司引入理想视口概念，那些基于理想视口而设计的网站，不需要用户手动缩放，也不需要出现横向滚动条，网站的所有内容都可以正常的呈现给用户( 把布局视口进行设置，让它和视觉视口相匹配)

1、设置viewport

```
    <meta name="viewport" content="width=device-width, initial-scale=1.0,user-scalable=no,maximum-scale=1.0,minimum-scale=1.0">

    <meta name="viewport" content="width=device-width, initial-scale=1.0,user-scalable=no"> 
```
- `width=device-width`: 让布局视口和视觉视口相匹配（html宽度 等于 设备的宽度）
- `initial-scale=1.0` : 页面初始的缩放值，为数字，可以是小数,一般设置为1.0
- `user-scalable=no`: 是否允许用户进行缩放，'no'为不允许，'yes'为允许
- `maximum-scale=1.0`: 用户可放大的最大值
- `minimum-scale=1.0`: 用户可缩小的最小值

##  rem 布局

通过js动态计算一个最新的rem值：
```
<script>
        // 1、先获取设备的宽度（等同于html的宽度）
        var deviceWidth = document.documentElement.clientWidth; //html宽度
       // 2、计算出一个最新的rem的值
        if(deviceWidth>750){
            deviceWidth = 750;
        }
        var r  = deviceWidth*100/750;  // 750指的是设计稿宽度，根据实际拿到的设计稿尺寸去修改

        // 3、把计算出来的最新的rem值设置给html的font-size
        document.documentElement.style.fontSize = r + 'px';
</script>
```
使用方法：
在设计稿上量取的像素值，除以100，得到x，所有的值都写为xrem。图片，背景图片都需要设置rem尺寸值。
