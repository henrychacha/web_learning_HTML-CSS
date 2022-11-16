## 复习
- 圆角
```
    border-radius: 10px; 四个角统一的圆角半径
    border-radius:10px 20px;  左上右下  右上左下
    border-radius:10px 20px 30px;  左上  右上左下  右下
    border-radius:10px 20px 30px 40px;  左上  右上  右下  左下
    

    border-top-left-radius
    border-top-right-radius
    border-bottom-left-radius
    border-bottom-right-radius

```
- 变形 transform
 - 旋转 rotate(-30deg) 
 - 缩放 scale(0.5) scale(0.5,2)
 - transform:rotate(-30deg) scale(0.5,2);

- 关键帧动画
 - 定义动画（节点）
    ```
        @keyframes 动画名称{
            0%{ from

            }
            25%{

            }
            50%{

            }
            ...
            100%{ to

            }
        }
    ```
 - 调用
    ```
        animation: name duration timing-function iteration-count delay direction  fill-mode;

        animation-timing-function:linear/ease/ease-in/ease-out/ease-in-out/贝塞尔
        animation-iteration-count: n / infinite(无限)
        animation-direction:alternate; 轮流反向
        animation-fill-mode:forwards; 停在动画终点

        animation: myrotate 3s linear infinite;
        animation: move 3s linear infinite alternate;
        animation: move 3s linear forwards;
    ```

## 过渡动画

- 关键帧动画： 可以自动调用，动画可以设置多个节点（状态），可以多次（无限次）运行
- 过渡动画：不能自动执行，需要伪类触发，动画只有两个状态，触发一次运行一次，不会反复运行
- 过渡使用场景：一般用于元素正常状态和鼠标移入状态（:hover）属性变化时，出现平滑过渡效果
```
    transition:transition-property transition-duration transition-timing-function transition-delay;
    transition-property:过渡的属性名 ，all(所有变化的属性都过渡)
    transition-duration:过渡的时间  s/ms
    transition-timing-function: 过渡的速度曲线，取值同关键帧动画
    transition-delay：过渡延迟时间 s/ms

```
- 多个属性过渡
```
  transition: width 2s linear,height 4s ease,...;
```
- 示例
``` 
    情况1：
        .box{
            width: 100px;
            transition:all 0.5s linear;   <!-- 鼠标脱离时的过渡 -->
        }
        .box:hover{
            width: 200px;
            transition:all 2s linear;  <!-- 鼠标悬停时的过渡 -->
        }

    情况2：
        .box{
            width: 100px;
            <!-- 鼠标脱离时没有过渡效果 -->
        }
        .box:hover{
            width: 200px;
            transition:all 2s linear;  <!-- 鼠标悬停时的过渡 -->
        }
    情况3：
        .box{
            width: 100px;
            transition:all 0.5s linear;<!-- 鼠标悬停和脱离时都有过渡，并且效果相同 -->
        }
        .box:hover{
            width: 200px;
        } 
```

## 阴影

- 盒子阴影
```
    box-shadow:x-shadow y-shadow blur spread color inset;
     - x-shadow : 必需，水平阴影位置 ，正数向右偏移，负数向左偏移
     - y-shadow : 必需，垂直阴影位置 ，正数向下偏移，负数向上偏移
     - blur : 可选，阴影的模糊距离
     - spread: 可选，阴影的扩展尺寸
     - color: 可选，阴影的颜色
     - inset: 可选，不设置表示外阴影，设置inset表示内阴影 
    多组阴影：
    box-shadow:x-shadow y-shadow blur spread color inset,x-shadow y-shadow blur spread color inset, ... ;
```

- 文字阴影

```
    text-shadow:x-shadow y-shadow blur color;
    - x-shadow : 必需，水平阴影位置 ，正数向右偏移，负数向左偏移
    - y-shadow : 必需，垂直阴影位置 ，正数向下偏移，负数向上偏移
    - blur: 可选，阴影的模糊距离
    - color:可选，阴影的颜色 默认和文字颜色相同
    多组阴影：x-shadow y-shadow blur color,x-shadow y-shadow blur color,...;
```