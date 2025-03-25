---
title: Promise async/await
date: 2024-10-02
excerpt: "解释回调地狱，异步任务，promise以及async/await"
---


这篇文章开始前，我们先讲讲什么是**回调地狱**：

存在异步任务的代码，不能保证能按照顺序执行，如果非要代码顺序执行,可能出现回调函数套回调函数，这会让代码可读性差，不好维护。

#### 回调函数

当一个函数作为参数传入另一个参数中，并且它不会立即执行，只有当满足一定条件后该函数才可以执行，这种函数就称为回调函数。定时器和Ajax中就存在回调函数。

回调函数: `function(){console.log('执行了回调函数')}`

```javascript
setTimeout(function(){
	console.log('执行了回调函数');
},3000)
```

回调函数: `xhr.onreadystatechange`绑定的函数。

```javascript
//1.创建异步对象
var xhr=new XMLHttpRequest();
//2.绑定监听事件(接收请求)
xhr.onreadystatechange=function(){
    //此方法会被调用4次
    //最后一次，readyState==4
    //并且响应状态码为200时，才是我们要的响应结果 xhr.status==200
    if(xhr.readyState==4 && xhr.status==200){
        //把响应数据存储到变量result中
        var result=xhr.responseText;
        console.log(result);
    }
}
//3.打开链接（创建请求）
xhr.open("get","/demo/ajaxDemo",true);
//4.发送请求
xhr.send();
```

#### 异步任务

同步任务在主线程上排队执行，只有前一个任务执行完毕，才能执行下一个任务。
异步任务不进入主线程，而是进入异步队列，前一个任务是否执行完毕不影响下一个任务的执行。

```javascript
setTimeout(function(){
    console.log('执行了回调函数');
},3000)
console.log('111');
//111
//执行了回调函数
```

## Promise

### 介绍

`Promise` 是 **异步编程** 的一种解决方案，比传统的解决方案（回调函数）更加合理和更加强大。

```javascript
const promise = new Promise(function(resolve, reject){
    // code

    if(/*异步操作成功*/){
        resolve(value);
    }else{
        reject(error);
    }
})

promise.then(function(value){
    //success
},function(error){
    //error
})
```

### Promise Ajax实操

```javascript
const getJSON = function (url) { // 添加url参数  
    const promise = new Promise(function (resolve, reject) {
        const client = new XMLHttpRequest();
        const handler = function () {
            if (this.readyState !== 4) {
                return;
            } else if (this.status === 200) { // 修正拼写错误  
                resolve(this.responseText); // 通常使用responseText来获取响应文本  
            } else {
                reject(new Error(this.statusText)); // 添加错误处理  
            }
        };
        client.onreadystatechange = handler; // 绑定事件监听器  
        client.open("GET", url, true); // 设置请求方法和URL  
        client.send(); // 发送请求  
    });
    return promise; // 返回promise对象  
};

// 使用示例  
getJSON("https://blog.waffle.icu/2024/09/01/hello-world/").then(function (data) {
    console.log(data); // 处理成功响应  
}).catch(function (error) {
    console.error("请求失败:", error); // 处理错误  
});  
```

## async/await

### async

`async` 是一个通过异步执行并隐式返回 `Promise` 作为结果的函数。

`async` 函数返回的是一个 `promise` 对象，并且`Promise`还有`state`和`result`。
如果 `async`函数中有返回值，当调用该函数时，内部会调用`Promise.resolve()`方法把它转化成一个`promise`对象作为返回。
想获取到 `async` 函数的执行结果，就要调用 `promise` 的 `then` 或 `catch` 来给它注册回调函数

```javascript
async function timeout() {
    return 'hello world!';
}
timeout();// 虽然调用了，但是没有打印 hello world!
console.log('我虽然在后面，但是先执行');// 我虽然在后面，但是先执行
console.log(timeout());// 返回promise对象
```

```javascript
async function timeout() {
    return 'hello world!'
}
timeout().then(val => {
    console.log(val)
})
console.log('我虽然在后面，但是先执行')
//我虽然在后面，但是先执行
//hello world!
```

### await

1. `await` 关键字只能放到 `async` 函数内部。
   
2. `await` 不仅仅用于等 `Promise` 对象，还可以等任意表达式,`await` 后面可以接普通函数调用或者直接量的，不过更多是放一个返回 `promise` 对象的表达式。等待`promise`对象执行完毕，并返回结果。

3. `await` 等待到 `Promise` 对象，会阻塞后面代码，等待并获得`resolve` `reject` 的值。
   
4. `await` 等待到 非`Promise` 对象，会自动将该对象包装成一个已经 `resolve` 的 `Promise` 对象。

```javascript
function getFirst() {
    return 'first';
}
async function testAsync() {
    return Promise.resolve('hello async');
}
async function test() {
    const v1 = await getFirst();
    const v2 = await testAsync();
    console.log(v1, v2);
}
test();//first hello async
```

```javascript
function log(time) {
    setTimeout(function () {
        console.log(time);
    }, time)
}
async function fun() {
    let a = await log(1000);//由于 log(1000) 返回 undefined（且不被当作 Promise），await 关键字将其视为一个立即解决的 Promise
    let b = await log(3000);
    let c = log(2000);
    console.log(a);// undefined
    console.log(1)
}
fun();
// 立即输出 undefined 1
// 1秒后输出 1000
// 2秒后输出 2000
// 3秒后输出 3000
```