---
title: CSS笔记
date: 2024-09-14
excerpt: "CSS笔记，会时常更新"
---

### 内联样式
```html
<p style="font-size: 20px; color: black;">内联样式</p>
```

### 内部样式
```html
<head>
    <style>
    p{
        font-size: 15px;
        color: bisque;
    }
    </style>
</head>
```

### 外部样式
```html
<head>
    <link rel="stylesheet" type="text/css" href="theme.css">
</head>
```

### 选择器
**全局选择器**
```css
<style>
    *{
        font-size: 30px;
        color: red;
    }
</style>
```
>优先级低

**元素选择器**
```css
<style>
    p{
        font-size: 15px;
        color: bisque;
    }
</style>
```
>选择所有同种类标签

**类选择器**
```css
<style>
    .hello{
        color: red;
    }
    .welcome{
        font-size: 20px;
    }
</style>

<p class="hello">hello</p>
<p class="hello welcome">welcome</p>
```

**ID选择器**
```css
<style>
    #hello{
        font-size: 20px;
        color: red;
    }
</style>

<p id="hello">你好</p>
```
>ID唯一，不能以数字开头

**合并选择器**
```css
<style>
    h3, #hello,.welcome {
        font-size: 30px;
        color: red;
    }
</style>

<h3>标题</h3>
<p id="hello">你好</p>
<p class="welcome">欢迎</p>
```

**选择器优先级**
- 内联样式: 内联样式的优先级最高，由`style`属性直接定义在HTML元素上
- ID选择器: 具有较高的优先级，使用`#id`形式
- 类选择器、属性选择器和伪类: 使用`.`、`[]`或`:pseudo-class`形式
- 元素选择器: 优先级最低，使用`元素名`或`:pseudo-element`形式
- 重要性: 使用`!important`声明可以提高优先级

### 字体属性
**颜色**
`color: #ff0000;` 16进制
`color: rgb(0, 0, 0);` 分别对应 红 绿 蓝;(255,255,255)白色
`color: rgba(0, 0, 0, 0);` 最后一个代表透明度，0为完全透明
**字体粗细**
`font-weight: ;` (100 ~ 900)
**字体样式**
`font-style: normal;`
`font-family: 'Microsoft YaHei';`

### 背景属性
`background-color: #59ff00;` 背景颜色
`background-image: url();` 背景图片
`background-repeat: no-repeat;` 背景图片不平铺(空出部分不继续展示) `repeat-x`水平方向可重复
`background-size: 1200px 200px;` 图片可能会被拉伸或压缩
`background-size: cover;` 保证图片比例不变充满容器，图片可能被切割
`background-size: contain;` 保证图片比例不变尽量充满容器，图片不被切割
`background-position: left;` 图片开始渲染的位置，可设置像素或百分比 `0% 0%`-最左边最上边

### 图片
`object-fit: cover;` 确保图片会覆盖整个容器，但可能会被裁剪以保持宽高比
`object-fit: contain;` 图片不会被裁剪，但这可能图片不会完全填满容器。

### 文本属性
`text-align: center;` 对齐方式
`text-decoration: underline;` 定义下划线 `overline`上划线 `line-through`删除线
`text-transform: ;` 定义大小写 `uppercase`全大写 `lowercase`全小写 `capitalize`首字母大写
`text-indent: 50px;` 首行缩进

### 表格属性
```css
<style>
    table,td{
        border: 1px solid #000000;
        border-collapse: collapse;
        width: 500px;
        height: 100px;
    }
    td{
        text-align: center;
        vertical-align: middle;
        background-color: #ffffff;
        color: #000000;
    }
</style>
```

### 关系选择器
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>关系选择器</title>
  <style>
    /*后代选择器  ul里面包含的li 所以修改了ul以及包含的li里面的内容  只要是后代都生效*/
    .list1 li{
      color: pink;
    }
    /*子代选择器 只是子生效，嵌套的孙子不生效*/
    .t2>a{
      color:sandybrown;
    }
    /*相邻兄弟选择器，只是选择下面的一个，多的就不选择了*/
    .t3+h1{
      color: #fa4d15;
    }
    /*通用兄弟选择器，选择面的全部兄弟平级的*/
    .t4 ~ p{
      color: red;
    }
  </style>
</head>
<body>
<!--后代选择器案例 只要是后代都生效-->
<ul>
  <li class="list1">
    列表1
    <ul>
      <li>孙子</li>
      <li>孙子</li>
    </ul>
  </li>
  <li>列表2</li>
</ul>
 
<!--子代选择器 只是往下递归1层 多于的不生效 用>号表示-->
<div class="t2">
  <a href="#">
    子
    <div>
      <a href="#">孙子</a>
    </div>
  </a>
</div>
 
<!--相邻兄弟选择器 只是相邻1层 多的就不生效了  用+号表示-->
<p class="t3">我是大哥</p>
<h1>我是二哥</h1>
<h1>我是三哥</h1>
 
<!--通用兄弟选择器，只要是平级的兄弟 都生效 用波浪号 ~表示-->
<h2 class="t4">我是大哥1</h2>
<p>我是二哥1标签</p>
<p>我是三个1标签</p>
</body>
</html>
```

### 盒子模型
<img src="https://github.com/Waffle-01/waffle-01.github.io/blob/main/source/images/box.png?raw=true" width=400px  object-fit: contain>

### 弹性盒子模型 (css3新特性)
`display: flex;`
`flex-direction: row;` 布局方向
`flex-wrap: wrap;` 环绕效果
`justify-content: flex-start;` 水平对齐
`flex-grow: 1;` 项目比例放大(`flex-grow`属性在子属性中) 

>默认弹性盒子内容横向摆放

### 浮动
<img src="https://github.com/Waffle-01/waffle-01.github.io/blob/main/source/images/float.png?raw=true" width = 600px object-fit: contain/>
>只有左右浮动

**浮动的副作用**
1.父元素的高度无法被撑开
2.浮动元素可能会重叠

>父元素设置高度
受影响元素添加clear属性 `clear: both;`
overflow清除浮动 父级容器添加`overflow: hidden;clear: both;`
伪对象方式 `.container::after{content: "";display: block;clear: both;}`

### 定位
**fixed**
元素的位置相对于浏览器窗口是固定位置
```css
<style>
  .box{
      position:fixed;
      top:30px;
      right:5px;
  }
</style>
```
**absoulte**
绝对定位的元素的位置相对于最近的已定位父元素
```css
<style>
  .box {
      position: absolute;
      top:50px;
      left:50px;
  }
</style>
```
**relative**
移动相对定位元素，但它原本所占的空间不会改变
```css
<style>
  .box{
      position: relative;
      top:50px;
      left:50px;
  }
</style>
```
>相对定位和绝对定位是相对于具有定位的父级元素进行位置调整，若父级不存在，则向上寻找

**z-index**
指定一个元素的堆叠顺序,拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面

### css3新特性
**圆角**
<img src="https://github.com/Waffle-01/waffle-01.github.io/blob/main/source/images/border-radius.png?raw=true" width = 600px object-fit: contain/>

该属性是一个 简写属性，将这四个属性 `border-top-left-radius` `border-top-right-radius` `border-bottom-right-radius` `border-bottom-left-radius` 简写为一个属性

>四个值：左上 右上 右下 左下
三个值：左上 右上+左下 右下
两个值：左上+右下 左下+右上

**阴影**
```css
/* x 偏移量 | y 偏移量 | 阴影颜色 */
box-shadow: 60px -16px teal;

/* x 偏移量 | y 偏移量 | 阴影模糊半径 | 阴影颜色 */
box-shadow: 10px 5px 5px black;

/* x 偏移量 | y 偏移量 | 阴影模糊半径 | 阴影扩散半径 | 阴影颜色 */
box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);

/* 插页 (阴影向内) | x 偏移量 | y 偏移量 | 阴影颜色 */
box-shadow: inset 5em 1em gold;

/* 任意数量的阴影，以逗号分隔 */
box-shadow:
  3px 3px red,
  -1em 0 0.4em olive;

/* 全局关键字 */
box-shadow: inherit;
box-shadow: initial;
box-shadow: unset;
```

### 动画
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container {
            height: 200px;
            width: 200px;
            background-color: aquamarine;
            border-radius: 50%;
            animation: test 3s linear 1s infinite normal;
            
        }
        @keyframes test{
            0%{
                background-color: aquamarine;
            }
            50%{
                background-color: bisque;
            }
            100%{
                background-color: red;
            }
        }
        .container:hover{
            animation-play-state: paused;
        }
    </style>
</head>


<body>
    <div class="container"></div>
</body>

</html>
```

`animation: name duration timing-function delay iteration-count direction fill-mode;`

| 属性      | Description |
| ----------- | ----------- |
| `name`      | 名称       |
| `duration`   | 持续时间        |
| `timing-function` | 时间函数; `linear`（匀速）`ease`（慢开始，然后变快，再慢结束）、`ease-in`（慢开始）、`ease-out`（慢结束）`cubic-bezier(0.42, 0, 0.58, 1)`（贝塞尔曲线自定义的缓动效果） |
| `delay` | 延迟时间 |
| `iteration-count` | 迭代次数 |
| `direction` | 动画方向; normal（正常方向）、reverse（反向播放）、alternate（动画在每次迭代时反向播放）、alternate-reverse（动画在第一次迭代时反向播放，然后每次迭代时反向）  |
| `fill-mode` | 填充模式; `none`（默认值，动画在开始前和结束后不会应用任何样式到目标）`forwards`（动画在结束后保持最后一个关键帧的样式）`backwards`（动画会在等待开始时应用第一个关键帧的样式）、`both`（`forwards` 和 `backwards` 的组合） |

### 媒体查询
**设置\<meta>标签**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        .box{
            width: 300px;
            height: 300px;
        }
        @media screen and (max-width: 768px){
            .box{
                background-color: blue;
            }
        }
        @media screen and (min-width: 996px){
            .box{
                background-color: black;
            }
        }
        @media screen and (min-width: 768px) and (max-width: 996px){
            .box{
                background-color: green;
            }
        }
    </style>
</head>
<body>
    <div class="box"></div>
</body>
</html>
```

### 雪碧图

**优点**
1.减少图片的字节数。
2.减少了网页的HTTP请求，从而大大提高了页面的性能。
3.解决了网页设计师在图片命名上的困扰，只需要对一张集合的图片的命名就可以了 不需要对每一个小元素进行命名，从而提高了网页的制作效率。

### 字体图标

**优点**
1.轻量型：加载速度快，减少http请求
2.灵活性：可以通过css设置大小颜色等
3.兼容性：网页字体支持所有现代浏览器，包括IE低版本

[阿里字体图标库](https://www.iconfont.cn/)

### 常见属性
`display: block;` 将元素渲染为块级元素
`display: inline` 将元素渲染为内联元素
`display: none` 元素不会被显示在页面上，也不会占据空间

**注**
>`<style>`标签一般在`<head>`内
`<p>`标签等在`<body>`内
chrome浏览器最小字体大小 12px