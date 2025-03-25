---
title: HTTP Referer
date: 2024-09-26
excerpt: "个人学习，整理自：https://www.ruanyifeng.com/blog/2019/06/http-referer.html "
---

### referrer

#### referrer定义

referrer 是指在请求网页时，浏览器所附带的前一个网页的地址（URL）。通常，访问者点击某个链接时，浏览器会在请求新页面时将当前页面的URL作为Referrer发送给服务器。

#### referrer发生场景

主要情况：
1. 用户点击链接
2. 用户发送表单
3. 网页加载静态资源，如图片、脚本、样式
   
#### referrer作用
Referer字段实际上告诉了服务器，用户在访问当前资源之前的位置。这往往可以用来用户跟踪。

一个典型的应用是，有些网站不允许图片外链，只有自家的网站才能显示图片，外部网站加载图片就会报错。它的实现就是基于Referer字段，如果该字段的网址是自家网址，就放行。

由于涉及隐私，很多时候不适合发送Referer字段。

这里举两个例子，都不适合暴露 URL。一个是功能 URL，即有的 URL 不要登录，可以访问，就能直接完成密码重置、邮件退订等功能。另一个是内网 URL，不希望外部用户知道内网有这样的地址。Referer字段很可能把这些 URL 暴露出去。

此外，还有一种特殊情况，需要定制Referer字段。比如社交网站上，用户在对话中提到某个网址。这时，不希望暴露用户所在的原始网址，但是可以暴露社交网站的域名，让对方知道，是我贡献了你的流量。

#### referrer策略

- `no-referrer`: 不发送 Referrer 信息。
- `no-referrer-when-downgrade`: 仅当发生协议降级时不发送 Referrer 信息。（如 HTTPS 页面引入 HTTP 资源，从 HTTPS 页面跳到 HTTP ）
- `same-origin`: 链接到同源网址（协议+域名+端口 都相同）时发送，否则不发送。
- `origin`: 一律只发送源信息（协议+域名+端口），不管是否跨域。
- `strict-origin`: 如果从 HTTPS 网址链接到 HTTP 网址，不发送Referer字段，其他情况只发送源信息。
- `origin-when-cross-origin`: 同源时，发送完整的Referer字段，跨域时发送源信息。
- `strict-origin-when-cross-origin`: 同源时，发送完整的Referer字段；跨域时，如果 HTTPS 网址链接到 HTTP 网址，不发送Referer字段，否则发送源信息。
- `unsafe-url`: Referer字段包含源信息、路径和查询字符串，不包含锚点、用户名和密码。

#### referrer用法

1. http头信息
通过 HTTP 头信息的Referrer-Policy告诉浏览器
2. `<meta>`标签
`<meta name="referrer" content="origin">`
3. referrerpolicy属性
`<a href="..." referrerpolicy="origin" target="_blank">xxx</a>`

**退出页面重定向可隐藏原始网站**