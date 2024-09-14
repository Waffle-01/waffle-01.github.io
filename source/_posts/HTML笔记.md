---
title: HTML笔记
date: 2024-09-14
excerpt: "HTML笔记，会时长更新"
---

### HTML5 基本骨架
```html
<!DOCTYPE html>
<html>
  <head>
      <meta charset="UTF-8" />
      <title>...</title>
  </head>
  <body>
  </body>
</html>
```
>`<!DOCTYPE html>` 声明文档类型
`<html>` 这个元素包裹了页面中所有的内容，有时被称为根元素
`<head>` 这个元素是一个容器，它包含了在 HTML 页面中但不显示的内容
`<title>` 标题 对搜索引擎优化（SEO）具有重要意义
`<meta>` 提供了 HTML 文档的元数据
`<body>` 包含了访问页面时所有显示在页面上的内容

### 布局
```html
<header>：页眉。
<nav>：导航栏。
<main>：主内容。主内容中还可以有各种子内容区段，可用<article>、<section> 和 <div> 等元素表示。
<aside>：侧边栏，经常嵌套在 <main> 中。
<footer>：页脚。
```

### 常见标签
```html
<h1></h1> 标题
<p></p> 段落
<br/> 换行
<hr/> 水平线
<blockquote cite=" "></blockquote> 引用
<abbr title=" ">HTML</abbr> 缩略语
<sub></sub> 上标
<sup></sup> 下标
```

### 站点添加自定义图标
```html
<link rel="icon" href="favicon.ico" type="image/x-icon" />
```

### 图片
```html
<img src="" alt="" width="" title="">
```
### 响应式图片

**分辨率切换**
```html
<img
  srcset="elva-fairy-480w.jpg 480w, elva-fairy-800w.jpg 800w"
  sizes="(max-width: 600px) 480px,
         800px"
  src="elva-fairy-800w.jpg"
  alt="Elva dressed as a fairy" />
```


### 视频
```html
<video src="rabbit320.webm" controls>
  <p>
    你的浏览器不支持 HTML 视频。可点击<a href="rabbit320.mp4">此链接</a>观看。
  </p>
</video>

<video controls>
  <source src="rabbit320.mp4" type="video/mp4" />
  <source src="rabbit320.webm" type="video/webm" />
  <p>你的浏览器不支持此视频。可点击<a href="rabbit320.mp4">此链接</a>观看</p>
</video>
```

### iframe 嵌入网页
```html
<iframe src=" " scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true">
</iframe>
```

### 超文本链接
```html
<a href="url">11111</a>
```

### 文本标签
```html
<span>hello</span> 
<em>hello</em> 斜体 定义着重文字
<b>hello</b> 加粗 定义粗体文字
<i>hello</i> 斜体 定义斜体字
<strong>hello</strong> 加粗 定义加重语气
<del>hello</del> 定义删除字 
```


### 列表
**有序列表**
```html
<ol type="">
  <li></li>
  <li></li>
</ol>
```
>`type` 修改列表序号类型

**无序列表**
```html
<ul type="">
  <li></li>
  <li></li>
</ul>
```
>`type` 修改列表序号图案

### 表格
```html
<table>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
```
>`<tr>` 行  `<td>` 列
`border` 边框  `width` 宽  `height` 高
`rowspan=""` 水平合并  `colspan=""`垂直合并

### Form表单
```html
<form action="" name="" method="">
  name:<input type="text" name="name">
  password:<input type="password" name="pwd">
  <input type="submit" value="登录"> 
</form>
```
>`action` 服务器地址
`name` 表单名称
`method` get post

### 块级元素 内联元素
| 块级元素 | 内联元素 |
| ------- | ------- |
|    独占一行,默认情况下，其宽度自动填满其父元素宽度    | 相邻的行内元素会排列在同一行里，直到一行排不下，才会换行，其宽度随元素的内容而变化   |
|    可以设置width，height属性    | 行内元素设置width，height属性无效   |
|    可以设置margin和padding属性    | 行内元素起边距作用的只有margin-left、margin-right、padding-left、padding-right，其它属性不会起边距效果。 | 
|    对应于display:block    | 对应于display:inline | 


### 实体引用
| 原义字符 | 等价字符 |
| ------- | ------- |
|    <    | \&lt;   |
|    >    | \&gt;   |
|    "    | \&quot; | 
|    '    | \&apos; | 
|    &    | \&amp;  |

### sandbox
嵌入的网页默认具有正常权限，比如执行脚本、提交表单、弹出窗口等。为了限制`<iframe>`的风险，HTML 提供了sandbox属性，允许设置嵌入的网页的权限，等同于提供了一个隔离层，即“沙箱”。
sandbox 可以当作布尔属性使用，表示打开所有限制。
```html
<iframe src="https://www.example.com" sandbox>
</iframe>
```

### http 与 https
菜鸟教程: [http与https的区别](https://www.runoob.com/w3cnote/http-vs-https.html)


### 注
1. HTML 元素的内容中使用多个空白字符或换行，当渲染这些代码的时候，HTML 解释器会将连续出现的空白字符减少为一个单独的空格符
2. **注译** ``<!-- <p>我在注释内！</p> -->``

### SVG
SVG 是用于描述矢量图像的语言，它基于 XML