---
layout: question
title:  如何将socket.io与webpack-hot-middleware一起使用？
date:   2020-03-30T09:17:36.000Z
description: 我有一个使用webpack-dev-middleware和webpack-hot-middleware进行热模块替换（HMR）的Koa服务器，因此中间件使...
img: 
author: Tony西里
category: question
answer: 0
tags: Node.js的 KoaJS
topic: KoaJS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个使用webpack-dev-middleware和webpack-hot-middleware进行热模块替换（HMR）的Koa服务器，因此中间件使用websocket将更改推送到客户端。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是我的应用程序代码还需要在客户端和Koa服务器之间建立自己的websocket连接。</font><font style="vertical-align: inherit;">我不知道该如何实现？</font><font style="vertical-align: inherit;">好像两者是矛盾的。</font><font style="vertical-align: inherit;">我可以并排吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的服务器代码看起来像这样</font></font></p>

<pre><code>const compiler = webpack(webpackConfig)<font></font>
const app = new Koa()<font></font>
<font></font>
app.use(webpackDevMiddleware(compiler, {<font></font>
  quiet: true,<font></font>
  noInfo: true<font></font>
  stats: {<font></font>
    colors: true,<font></font>
    reasons: true<font></font>
  }<font></font>
})))<font></font>
<font></font>
app.use(webpackHotMiddleware(compiler))<font></font>
<font></font>
const server = require('http').createServer(app.callback())<font></font>
const io = require('socket.io')(server)<font></font>
io.on('connection', function() { console.log('socket connection!!') })<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和我的客户一样</font></font></p>

<pre><code>import Client from 'socket.io-client'<font></font>
const io = Client()<font></font>
io.on('connection', (socket) =&gt; {<font></font>
  console.log('+++ io connected! ++++')<font></font>
  io.on('disconnect', () =&gt; { console.log('disconnected', socket) })<font></font>
})<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">HMR套接字正常工作，但是另一个正在尝试与之交谈， 
 </font></font><code>GET /socket.io/?EIO=3&amp;transport=polling&amp;t=1446911862461-0</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且这些请求失败。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何创建不与HMR插座冲突的Websocket？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3837篇《如何将socket.io与webpack-hot-middleware一起使用？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
