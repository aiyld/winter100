---
layout: question
title:  （Next.js，Express会话）在getInitialProps内部进行的每个请求的新会话
date:   2020-03-23T13:05:45.000Z
description: 我正在尝试使Express会话可以与Next.js一起使用，并且已经在客户端成功完成了此操作，但是我在getInitialProps内部进行的API调用遇...
img: 
author: 小胖
category: question
answer: 0
tags: 表达 React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试使</font></font><a href="https://github.com/expressjs/session" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Express会话</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以与</font></font><a href="https://github.com/zeit/next.js/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Next.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一起</font><a href="https://github.com/zeit/next.js/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">使用</font></a><font style="vertical-align: inherit;">，并且已经在客户端成功完成了此操作，但是我在getInitialProps内部进行的API调用遇到了麻烦。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：我正在使用</font></font><a href="https://github.com/developit/unfetch/tree/master/packages/isomorphic-unfetch" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">isomorphic-unfetch</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行API调用。</font><font style="vertical-align: inherit;">我的Next.js安装在localhost：3000上运行，我的Express服务器在localhost：5000上运行。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是客户端API调用的示例（在getInitialProps之外）：</font></font></p>

<pre><code>componentDidMount() {<font></font>
  fetch('/path/to/endpoint', {<font></font>
    method: 'GET',<font></font>
    credentials: 'include',<font></font>
  }).then((res) =&gt; console.log(res));<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在这里记录res，因为我想查看标题。</font><font style="vertical-align: inherit;">原来这个请求有一个空的标题对象。</font><font style="vertical-align: inherit;">如果我能兑现诺言，我会得到我要求的数据。</font><font style="vertical-align: inherit;">即使刷新页面，此调用中的会话ID在服务器上也保持一致。</font><font style="vertical-align: inherit;">一切都按预期工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是getInitialProps内部的API调用示例：</font></font></p>

<pre><code>static async getInitialProps(ctx) {<font></font>
  fetch('/path/to/endpoint', {<font></font>
    method: 'GET',<font></font>
    credentials: 'include',<font></font>
  }).then((res) =&gt; console.log(res.headers));<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">再次登录以查看标题。</font><font style="vertical-align: inherit;">此响应具有标题，它们如下所示：</font></font></p>

<pre><code>Headers {<font></font>
_headers:<font></font>
{ 'x-powered-by': [ 'Express' ],<font></font>
'access-control-allow-origin': [ 'http://localhost:3000' ],<font></font>
vary: [ 'Origin, Accept-Encoding' ],<font></font>
'access-control-allow-credentials': [ 'true' ],<font></font>
'x-frame-options': [ 'SAMEORIGIN' ],<font></font>
'x-xss-protection': [ '1; mode=block' ],<font></font>
'set-cookie'['YgJGcZPBgbE_nEqqLZpw0ba0pyaf2eNS','connect.sid=s%3AYgJGcZPBgbE_nEqqLZpw0ba0pyaf2eNS.Oye%2F7%2BsyXrrLJwphEJ3nq3yMkBhM3%2Fm4PCl9KIV%2FTzA; Path=/; Expires=Sun, 05 Aug 2018 15:56:52 GMT;     HttpOnly' ],<font></font>
'content-type': [ 'application/json; charset=utf-8' ],<font></font>
'content-length': [ '246' ],<font></font>
etag: [ 'W/"f6-82FKQ+ERtkxLiKa8hEIeY4kgGgE"' ],<font></font>
date: [ 'Sun, 22 Jul 2018 15:56:52 GMT' ],<font></font>
connection: [ 'close' ] } }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如您所见，我的set-cookie标头中有connect.sid（express会话ID），但是问题是，每当刷新页面时connect.sid cookie都会更改，并且与客户端API调用的会话ID不匹配（即使刷新页面后也保持不变）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在Express服务器上的会话对象如下所示：</font></font></p>

<pre><code>app.use(<font></font>
  session({<font></font>
  resave: false,<font></font>
  name: 'connect.sid',<font></font>
  saveUninitialized: false,<font></font>
  secret: SESSION_SECRET,<font></font>
  unset: 'destroy',<font></font>
  cookie: {<font></font>
    maxAge: 3600000 * 24 * 14,<font></font>
    secure: false,<font></font>
  },<font></font>
  store: new MongoStore({<font></font>
    url: mongoUrl,<font></font>
    autoReconnect: true,<font></font>
  }),<font></font>
})<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）;</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果有人知道如何从getInitialProps内部进行快速调用来进行API调用，我将不胜感激！</font><font style="vertical-align: inherit;">先感谢您。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3044篇《（Next.js，Express会话）在getInitialProps内部进行的每个请求的新会话》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
