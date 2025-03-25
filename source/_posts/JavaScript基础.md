---
title: JavaScript 笔记
date: 2024-9-25
excerpt: "javascript基础内容"
---


### JavaScript和ECMAScript之间的关系

- ECMAScript 也是一门脚本语言，缩写为ES，通常看做JavaScript的标准化规范。
- JavaScript是ECMAScript的扩展语言，因为ECMAScript只提供了最基本的语法。
- JavaScript实现了ECMAScript的语言标准，并且在这个基础之上做了一些扩展，使得我们可以在浏览器环境中操作DOM 和 BOM，在node环境中可以做读写文件之类的操作。
>在浏览器环境中，JavaScript = ECMAScript + BOM + DOM
在node环境中，JavaScript = ECMAScript + Node APIs

### 引入js
1. 嵌入HTML
```html
<body>
    <script>
        var num = 10;
        console.log(num);    
    </script>
</body>
```
2. 引入本地文件
```html
<body>
    <script type = "text/javascript" src = " "></script>
<body>
```
3. 引入网络文件
```html
<body>
    <script src = " "></script>
<body>
```

### JavaScript输出方式
```JavaScript
alert("我是弹出框");
document.write("输出到页面");
console.log();
```

### 数据类型

| **类型**      | **包含的数据类型** |
|--------------|----------------|
| **基本类型**  | `String`（字符串）、`Number`（数字）、`Boolean`（布尔值）、`Null`（空值）、`Undefined`（未定义）、`Symbol`（符号，ES6 引入） |
| **引用类型**  | `Object`（对象）、`Array`（数组）、`Function`（函数） |
| **特殊对象**  | `RegExp`（正则表达式）、`Date`（日期） |

### typeof
typeof 运算符返回类型
```JavaScript
console.log(typeof 42);
// Expected output: "number"

console.log(typeof 'blubber');
// Expected output: "string"

console.log(typeof true);
// Expected output: "boolean"

console.log(typeof undeclaredVariable);
// Expected output: "undefined"
```

### 字符串

**在页面显示引号内内容**
```html
<script>
    var s = "hello \"world\" ";
    document.write(s);
</script>
```
**charAt()**

**concat()**
连接两个字符串，返回一个新的字符串，不改变原字符串
```html
<script>
    var num1 = 1;
    var num2 = 2;
    var num3 = "3";
    console.log("".concat(num1,num2,num3)); //123
    console.log(num1+num2+num3); //33
</script>
```

**substring()**
截取字符串。
`str.substring(0,5);`不包括5 （第一个数字大于第二个会自动互换）

**substr**
`str.substring(0,5);`
(0代表开始位置，5代表字符串长度)

**indexOf**
返回在一个字符串第一个出现的位置，如果没有返回-1
`"hello".indexOf("o");`

**trim**
去除字符串两端的空格(包括`\t \n`)，返回新字符串，不改变原字符串
ES6扩展写法  `trimStart()` `trimEnd()`

**split**
按规定分开字符串形成数组
```html
<script>
    var str = "hello world";
    console.log(str.split(" "));
</script>
```

### 数组
任何类型的数据都可以存入数组
`var arr = ['hello','worle'];`
>`aar[5]`超出数组长度会显示 undefined

**数组的静态方法**
`Array.isArray()` 判断是否是数组

**push**
数组末端添加元素，并返回添加后的数组长度，会改变原数组长度
```html
<script>
    var arr = [];
    var len = arr.push("hello","world");
    console.log(arr);
    console.log(len);
</script>
```

**pop**
删除数组最后一个元素并返回该元素
```html
<script>
    var arr = ["hello","world"];
    var s = arr.pop();
    console.log(arr);
    console.log(s);
</script>
```

**shift**
删除数组第一个元素并返回该元素
```html
<script>
    var arr = ["hello","world"];
    var s = arr.shift();
    console.log(arr);
    console.log(s);
</script>
```

**unshift**
在数组的开头添加元素
```html
<script>
    var arr = ["hello","world"];
    arr.unshift("你好");
    console.log(arr);
</script>
```

**join**
指定分隔符将数组中的元素连成字符串，默认用逗号分割(如果数组中是`undefine` `null`会被转换成空字符串)
```html 
<script>
    var arr = ["hello","world"];
    console.log(arr.join());// hello,world
    console.log(arr.join(" ")) // hello world
</script>
```

**split**
拆分（与join相反）

**concat**
数组合并，返回新数组
```html
<script>
    var arr1 = ["hello"];
    var arr2 = ["world"];
    var arr = arr1.concat(arr2);
    var str = arr1+arr2;
    console.log(arr);
    console.log(str); //变成字符串
</script>
```

**reverse**
数组元素顺序翻转，会改变原数组

**indexOf**
返回在元素在数组中第一个出现的位置，如果没有返回-1

### 函数
```html
<body>
    <button type="button" onclick="hello()">按钮</button>
    <script>
        function hello(){
            alert("你好");
        }
    </script>
</body>
```

### 对象

```html
<script>
var person = {
    firstName: 'John',
    lastName: 'Doe',
    age: 30,
    isStudent: false,
    greet: function() {
        console.log('Hello, I am ' + this.firstName + ' ' + this.lastName);
    }
};

console.log(person.firstName);  // 输出: John
person.greet();  // 输出: Hello, I am John Doe
</script>
```

```html
<script>
function person(firstname,lastname,age,eyecolor){
	this.firstname=firstname;
	this.lastname=lastname;
	this.age=age;
    this.eyecolor=eyecolor;
}
myFather=new person("John","Doe",50,"blue");
document.write(myFather.firstname + " is " + myFather.age + " years old.");
</script>
```

### Math
- `Math.abs(-1)` 返回绝对值
- `Math.max(1,2,3)` 返回最大值
- `Math.min(1,2,3)` 返回最小值
- `Math.ceil(x)` 对 x 进行上舍入
- `Math.floor(x)` 对 x 进行下舍入
- `Math.random()` 返回 0 ~ 1 之间的随机数
- `Math.pow(x,y)` 返回 x 的 y 次幂

### Date
使用 Date() 方法获得现在的日期
```html 
<script>
    var d=new Date();
    document.write(d);
</script>
```

- `getFullYear()` 使用 getFullYear() 获取年份
- `getTime()` 返回从 1970 年 1 月 1 日至今的毫秒数
- `setFullYear()` 使用 setFullYear() 设置具体的日期
- `toUTCString()` 使用 toUTCString() 将当日的日期（根据 UTC）转换为字符串
- `getDay()` 使用 getDay() 和数组来显示星期，而不仅仅是数字

### Dom 概述

#### Dom
DOM 是 JavaScript 操作网页的接口，全称为“文档对象模型”（Document Object Model）。它的作用是将网页转为一个 JavaScript 对象，从而可以用脚本进行各种操作（比如增删内容）。

浏览器会根据 DOM 模型，将结构化文档（比如 HTML 和 XML）解析成一系列的节点，再由这些节点组成一个树状结构（DOM Tree）。所有的节点和最终的树状结构，都有规范的对外接口。

DOM 只是一个接口规范，可以用各种语言实现。所以严格地说，DOM 不是 JavaScript 语法的一部分，但是 DOM 操作是 JavaScript 最常见的任务，离开了 DOM，JavaScript 就无法控制网页。另一方面，JavaScript 也是最常用于 DOM 操作的语言。后面介绍的就是 JavaScript 对 DOM 标准的实现和用法。

#### 节点
DOM 的最小组成单位叫做节点（node）。文档的树形结构（DOM 树），就是由各种不同类型的节点组成。每个节点可以看作是文档树的一片叶子。

- Document：整个文档树的顶层节点
- DocumentType：doctype标签（比如`<!DOCTYPE html>`）
- Element：网页的各种HTML标签（比如`<body>`、`<a>`等）
- Attr：网页元素的属性（比如class="right"）
- Text：标签之间或标签包含的文本
- Comment：注释
- DocumentFragment：文档的片段

#### 节点树

一个文档的所有节点，按照所在的层级，可以抽象成一种树状结构。这种树状结构就是 DOM 树。它有一个顶层节点，下一层都是顶层节点的子节点，然后子节点又有自己的子节点，就这样层层衍生出一个金字塔结构，又像一棵树。

浏览器原生提供document节点，代表整个文档。

>document
// 整个文档树

文档的第一层有两个节点，第一个是文档类型节点（`<!doctype html>`），第二个是 HTML 网页的顶层容器标签`<html>`。后者构成了树结构的根节点（root node），其他 HTML 标签节点都是它的下级节点。

除了根节点，其他节点都有三种层级关系。

- 父节点关系（parentNode）：直接的那个上级节点
- 子节点关系（childNodes）：直接的下级节点
- 同级节点关系（sibling）：拥有同一个父节点的节点
DOM 提供操作接口，用来获取这三种关系的节点。比如，子节点接口包括`firstChild`（第一个子节点）和`lastChild`（最后一个子节点）等属性，同级节点接口包括`nextSibling`（紧邻在后的那个同级节点）和`previousSibling`（紧邻在前的那个同级节点）属性。

### document对象

**innerHTML**
1. 获取元素
```javascript
var element = document.getElementById("myElement");
var content = element.innerHTML;
alert(content);
```
2. 修改元素
```javascript
var element = document.getElementById("myElement");
element.innerHTML = "<h1>内容已更新</h1><p>这是一个新内容。</p>";
```

**获取元素**

- `document.getElementsByTagName("div")` 返回带有指定标签名的对象的集合
- `document.getElementsByClassName( )`
- `document.getElementById( );`
- `document.getElementsByName()`
- `document.document.querySelector("#name");` 返回文档中匹配指定 CSS 选择器的一个元素;获取`id`的名使用`#` 获取`class`的名使用`.`
- `document.document.querySelectorALL("#name");` 返回文档中匹配的CSS选择器的所有元素节点列表

**创建元素**

```javascript
function addElement() {
  // 创建一个新的 div 元素
  let newDiv = document.createElement("div");
  // 给它一些内容
  let newContent = document.createTextNode("Hi there and greetings!");
  // 添加文本节点 到这个新的 div 元素
  newDiv.appendChild(newContent);

  // 将这个新的元素和它的文本添加到 DOM 中
  let currentDiv = document.getElementById("div1");
  document.body.insertBefore(newDiv, currentDiv);
}
```

### Element 对象

```javascript
document.getElementById("box");
console.log(id1.id);//id可修改
``` 

**id**

**className**

**classList**

- `add()` 增加一个class
- `remove()` 移除一个class
- `contains()` 检查当前元素是否包含class
- `toggle()` 将某个class移入或移出当前元素 

**innerHTML**
可以识别标签

**innerTEXT** 
与`innerHTML`类似，`innerTEXT`无法识别元素，直接渲染成字符串

### Element 获取元素位置

**`getBoundingClientRect()`**

获取元素 相对于视口（viewport） 的位置，包括 top、left、right、bottom、width 和 height。
```javascript
const rect = element.getBoundingClientRect();
console.log(rect.top, rect.left, rect.width, rect.height);
```

**`offsetTop` / `offsetLeft`**

获取元素 相对于最近的 offsetParent（最近的 position 不为 static 的祖先元素） 的偏移量。
```javascript
const top = element.offsetTop;
const left = element.offsetLeft;
```

**`clientTop` / `clientLeft`**

获取元素 边框的宽度，通常用于计算边框尺寸
```javascript
const borderTop = element.clientTop; // 上边框宽度
const borderLeft = element.clientLeft; // 左边框宽度
```

**`scrollTop` / `scrollLeft`**

获取元素 滚动的距离，用于可滚动容器的滚动监测。
```javascript
const scrollTop = element.scrollTop;
const scrollLeft = element.scrollLeft;
```

### CSS操作

```html
<body>
    <div class="box" id = "box"></div>
    <script>
        var box = document.getElementById("box");
        box.setAttribute("style","width: 200px;height: 200px;background-color:green");
    </script>
</body>
```

```html
<body>
    <div class="box" id = "box"></div>
    <script>
        var box = document.getElementById("box").style;
        box.width = "200px";
        box.height = "200px";
        box.backgroundColor = "#000000";
    </script>
</body>
```

```html
<body>
    <div class="box" id = "box"></div>
    <script>
        var box = document.getElementById("box").style;
        box.cssText = 'width: 200px;'+'height: 200px;'+'background-color:#000;';
    </script>
</body>
```

### 事件处理程序

**HTML事件**

```html
<body>
    <button class="hello" onclick="hello()">hello</button>
    <script>
        function hello(){
            alert("hello world");
        }
    </script>
</body>
```

**DOM0级事件**
HTML和js是分离的，但无法同时添加多个事件（前面的会被覆盖）
```html
<body>
    <button class="hello" id="hello">hello</button>
    <script>
        var h = document.getElementById("hello");
        h.onclick = function(){alert("hello world")}
    </script>
</body>
```

**DOM2级事件**

```html
<body>
    <button class="hello" id="hello">hello</button>
    <script>
        var h = document.getElementById("hello");
        h.addEventListener("click",function(){
            alert("hello world");
        })
    </script>
</body>
```

### 事件类型-鼠标事件

|项目	|Value|
|-----|-----|
|`click` |单击鼠标左键时发生。当用户的焦点在按钮上并按了 Enter 键时，同样触发|
|`dblclick`	|双击鼠标左键时发生，如果右键也按下则不会发生|
|`mousedown` |单击任意一个鼠标按钮时发生|
|`mouseout`	|鼠标指针位于某个元素上且将要移出元素的边界时发生|
|`mouseover` |鼠标指针移出某个元素到另一个元素上时发生|
|`mouseup`	|松开任意一个鼠标按钮时发生|
|`mousemove` |鼠标在某个元素上时，持续发生|

### Event 事件对象

<a herf="https://developer.mozilla.org/zh-CN/docs/Web/API/Event">event详解</a>

### 事件类型-键盘事件

`keydown` 在键盘上按下某个键时触发。如果按住某个键，会不断触发该事件。但是Opera浏览器不支持这种连续操作。该事件处理函数返回false时，会取消默认的动作(如输入的键盘字符，在IE和Safari浏览器下还会禁止keypress事件响应)
`keypress` 按下某个键盘键并释放时触发。如果按住某个键，会不断触发该事件。该事件处理函数返回false时，会取消默认的动作(如输入的键盘字符)(`ctrl` `Alt` `Shift` `Meat`等无法触发)
`keyup` 释放某个键盘键时触发。该事件仅在松开键盘时触发一次，不是一个连续的响应状态

**keycode**
唯一标识 enter按键-> 13

```html
<body>  
    <input type="text" id="username">  
    <script>  
        var usernameInput = document.getElementById("username");  
        usernameInput.addEventListener("keyup", function(e) {  
            console.log(e.target.value);  
        });  
    </script>  
</body> 
```

### 事件类型-表单事件

| 事件 | 详细 |
|----|---| 
|input事件|input事件当`<input>` `<select>` `<textarea>`的值发生变化时触发。对于复选框`<input type=checkbox>`或单选框`<input type=radio>`，用户改变选项时，也会触发这个事件|
|select事件|select事件当在`<input>` `<textarea>`里面选中文本时触发|
|Change事件|change事件当`<input>` `<select>` `<textarea>`的值发生变化时触发。它与input事件的最大不同，就是不会连续触发，只有当全部修改完成时才会触发，另一方面input事件必然伴随change事件|
|reset事件|reset事件当表单重置（所有表单成员变回默认值）时触发|
|submit事件|submit事件当表单数据向服务器提交时触发。submit事件的发生对象是<form>元素，而不是`<button>`元素，因为提交的是表单，而不是按钮|


```html
<body>
    <form if = "myForm">
        <input type="text" id="username">
        <input type="text" id="password">
        <button id = "res">重置</button>
    </form>

    <script>
        var myForm = document.getElementById("myForm");
        var butt = document.getElementById("res");  
        usernameInput.addEventListener("click", function () {
            myForm.reset();
        });  
    </script>
</body>
```

### 事件代理

把原本需要绑定在子元素的响应事件委托给父元素，让父元素担当事件监听的职务。事件代理的原理是DOM元素的事件冒泡

```html
<body>
    <ul id="list">
        <li>列表1</li>
        <li>列表2</li>
        <li>列表3</li>
        <li>列表4</li>
    </ul>

    <script>
        var list = document.getElementById('list');
        list.addEventListener('click', function (e) {
            if (e.target.tagName === "LI") {
                console.log(e.target.innerHTML);
            }
        })
    </script>
</body>
```

### 定时器

#### setTimeout()
在指定的毫秒数后调用函数或计算表达式

```html
<body>
    <script>
        var name = "join";
        user = {
            name: "kelen",
        }

        var getname = setTimeout(function(){
            alert(this.name);//join
        },2000)
    </script>
</body>
```

`clearTimeout()` 取消定时器，不会再执行了

>`setTimeout` 的`this`会指向全局环境

#### setInterval()
按照指定的周期（以毫秒计）来调用函数或计算表达式

```html
<!DOCTYPE html>  
<html lang="en">  
  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Document</title>  
    <style>  
        .box {  
            width: 200px;  
            height: 200px;  
            background-color: #000000;  
            opacity: 1;  
            transition: opacity 0.5s ease; /* 添加平滑过渡效果 */  
        }  
    </style>  
</head>  
  
<body>  
    <div class="box"></div>  
    <script>  
        var divStyles = document.getElementsByClassName("box"); // 注意变量名改为复数形式以反映其性质  
  
        if (divStyles.length > 0) { // 确保至少有一个元素  
            var changeColor = setInterval(function() {  
                var opacity = parseFloat(divStyles[0].style.opacity) || 1; // 获取当前opacity值，如果没有设置则为1  
                opacity -= 0.05;  
                if (opacity < 0) opacity = 0; // 确保opacity不会低于0  
                divStyles[0].style.opacity = opacity.toString(); // 更新样式  
            }, 50);  
        }  
    </script>  
</body>  
  
</html>
```

`clearInterval()` 取消定时器

### 防抖

防抖是指在**事件触发后的一段时间内不再触发该事件**，只有当事件停止触发一定时间后，才执行一次函数。每次事件触发时，如果在设定的时间间隔内再次触发，则会重新计时。

```javascript
function debounce(fn, delay) {
    var timer = null;
    return function () {
    if(timer){   
        clearTimeout(timer);  // 清除之前的定时器
    }   
    timer = setTimeout(fn,delay);
    };
}
```

### 节流

节流是指在**连续触发事件时，保证一定时间间隔内只执行一次函数**，即函数调用是固定频率的，而不会因为事件频繁触发而频繁执行。

```javascript
function throttle(fn, interval) {
    let lastTime = 0;
    return function () {
        const now = Date.now();
        if (now - lastTime >= interval) {
            lastTime = now;
            fn.apply();  // 执行目标函数
        }
    };
}
```

### Babel转码器

可将ES6转换成ES5

## ES6新特性

### let和const

**var,let,const的区别**

1. var声明变量存在变量提升，let和const不存在变量提升
```javascript
console.log(a); // undefined  ===>  a已声明还没赋值，默认得到undefined值
console.log(b); // 报错：b is not defined  ===> 找不到b这个变量
console.log(c); // 报错：c is not defined  ===> 找不到c这个变量
var a = 100;	
let b = 10;
const c = 10;
console.log(a);//a=100
```
2. let和const只能在块作用域里访问
   
```javascript
if(1){
    var a = 100;
    let b = 10;
    const c = 1;
}

console.log(a); // 100
console.log(b)  // 报错：b is not defined  ===> 找不到b这个变量
console.log(c)  // 报错：c is not defined  ===> 找不到c这个变量
```
3. 同一作用域下let和const不能声明同名变量，而var可以

```javascript
var a = 100;
console.log(a); //控制台输出 100

var a = 10;
console.log(a); //控制台输出 10

let a = 100;
let a = 10;
// 控制台报错：Identifier 'a' has already been declared  ===> 标识符a已经被声明了。
```

4. const定义常量，而且不能修改，但是在定义的对象时对象属性值可以改变
```javascript
 const a=2
 a=3
 console.log(a) //控制台报错
```
```javascript
const person = {
    name : 'make',
    sex : '男'
}

person.name = 'test'
console.log(person.name) //运行发现控制台没有报错，且 person.name 被成功修改
```

### 对象解构赋值

```javascript
var user = {
    name: "kitty",
    age: 18,
}

const {name,age} = user;
console.log(name,age);
```

### 字符串扩展

**unicode表示**
允许使用"\uxxxx"表示一个字符，xxxx表示字符的unicode码点。
`console.log("\u0061")` 
> a

**字符串遍历**
```javascript
var str = "hello";
for(let i of str){
    console.log(i);
}
```

**模板字符串**
```html
<script>
      url="xxxxxx"
       // es6之前
       let html="<div>"+" <a>" + url + "</a>" + "</div>";
		//es6
       let eshtml=`<div><a>${url}</a></div>`
</script>
```

### 字符串新增方法

`includes()` 判断字符串是否包含参数字符串，返回boolean值
`startsWith()`  `endsWith()`判断字符串是否以参数字符串开头或结尾。返回boolean值。可以有第二个参数，一个数字，表示开始查找的位置
```javascript
let str = 'blue,red,orange,white';
str.includes('blue');//true
str.startsWith('blue');//true
str.endsWith('blue');//false
```

`repeat()` 方法按指定次数返回一个新的字符串

```javascript
console.log('hello'.repeat(2));   //'hellohello'
```

`padStart()``padEnd()` 如果字符串不够长度，可以在前面或后面补全

```javascript
let arr = 'hell';
console.log(arr.padEnd(5,'o'));  //'hello'
console.log(arr.padEnd(6,'o'));  //'helloo'
console.log(arr.padEnd(6));  //'hell  ',如果没有指定将用空格代替
  
console.log(arr.padStart(5,'o'));  //'ohell'
```

`trimStart()` `trimEnd()`

### 数组扩展

**扩展运算符**

`console.log(...[1,2,3]);`
>1 2 3

**求数组最大值**

`Math.max.apply(null,arr)`
`Math.max(...arr)`

**合并数组**

```javascript    
var arr1 = [1,2,3];
var arr2 = [2,5,8];

console.log(arr1.concat(arr2));
console.log([...arr1,...arr2]);
```

**[Array.form()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/from)**
用于将类似数组的对象和可遍历的对象转化为数组


**[Array.of()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/of)**
通过可变数量的参数创建一个新的 Array 实例，而不考虑参数的数量或类型

### 对象的扩展

**属性的简介表示法**

```javascript
var name = "iwen";
var user = {
    name,//属性名和属性值变量名称相同可省略
    age: 18,
}
console.log(user);
```

```javascript
function getPoint() {
    var x = 4;
    var y = 6;
    return {x,y};
}
console.log(getPoint().x,getPoint().y) //4 6
```

**属性表达式：[]**

```javascript
let a = 'abc'
let es6_obj = {
    // 字面量定义对象的属性名
    [a]: 'ddddd',

    // 表达式作为对象的属性名
    ['k' + 'ey' + 'Val']: 'kkkkk',

    // 表达式用于定于方法名
    ['f' + 'un' + '1']() {
        return '表达式用于定于方法名'
    }
}
console.log(es6_obj); // {abc: 'ddddd', keyVal: 'kkkkk', fun1: ƒ}
```

**ES6 对象扩展运算符**

```javascript
let a = {a: 1, b: 2};
let n = {...a};
let m = {a};
console.log(n);//{a: 1, b: 2}
console.log(m);//{a:{a: 1, b: 2}}
```

### 函数的扩展

**箭头创建函数**

```javascript
var add = (x,y) => x+y;
console.log(add(1,2));//3
```
```javascript
var name = "kitty";
var user = {
    name: "iwen",
    age: 20,
    getName() {
        setTimeout(() => {
            console.log(this.name);//this指向user
        })
    }
}
console.log(user.getName());//iwen
```
>箭头函数中没有自己的this,而是引用外层的this

### Set数据结构
类似于数组，但是成员的值都是唯一的，没有重复值

```javascript
const nums = new Set();
[1,2,4,5,2,3,5,5,1].forEach(x =>nums.add(x));
for(let i of nums){
    console.log(i);
}//1 2 4 5 3
```
**字符串去除重复字符**

```javascript
var a = [...new Set("aaddaaccvw")].join('');
console.log(a);//adcvw
```

**Set()加入值时，不会发生类型转换**

```javascript
const a = new Set([1,2,3]);
a.add('1');
console.log(a);//{1,2,3,'1'}
```

**Set()常见方法**

`add()`
`delete()`
`size()`
`has()`

### <font color = "red">Promise对象</font>

[回调地狱，异步任务，Promise，async/await](https://blog.waffle.icu/2024/10/02/Promise%E5%AF%B9%E8%B1%A1/)

### class

**基本用法**

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    getName() {
        console.log(this.name);
    }
}

const p = new Person("kitty",20);
p.getName();// kitty
```

**静态方法**

在方法面前加上 `static` 关键字，就表示该方法不会被实列继承，而是直接通过类来调用
静态方法内的 `this` 指向类，而不是实列对象

```javascript
class Person {
    static getMethod(){
    console.log("hello");
    this.sayHello();
    }

    static sayHello(){
    console.log("你好");
    }
}

Person.getMethod();
// hello
// 你好
var p = new Person();
p.getMethod();//报错 p.getMethod is not a function
```

**继承**

`super()` 方法引用父类。
通过在 `constructor` 方法中调用 `super()` 方法，调用父级的 `constructor` 方法，获得了父级的属性和方法的访问权限。

```javascript
class Person {
    constructor(name,age){
        this.name = name;
        this.age = age;
    }

    getName(){
        console.log(this.name);
    }
    static getInfo(){
        console.log("run!run!run!")
    }
}

class Student extends Person{
    constructor(name,age,school){
        super(name,age);
        this.school = school;
    }
    getSchool(){
        console.log(this.school);
    }
}

var s = new Student("小明",16,"suda");
s.getName();// 小明
Student.getInfo();// run!run!run!
s.getSchool();// suda
```


### Module

[Module](https://blog.csdn.net/chehec2010/article/details/119804381#:~:text=JavaScript)