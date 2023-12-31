---
layout: question
title:  Express.js-app.listen与server.listen
date:   2020-03-17T10:02:38.000Z
description: 这可能是一个非常基本的问题，但我根本不明白。使用Express.js创建应用程序和在端口1234上启动应用程序侦听之间有什么区别，例如：var exp...
img: 
author: 小胖逆天
category: question
answer: 2
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这可能是一个非常基本的问题，但我根本不明白。</font><font style="vertical-align: inherit;">使用</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Express.js</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">创建应用程序</font><font style="vertical-align: inherit;">和在端口1234上启动应用程序侦听</font><font style="vertical-align: inherit;">之间有什么区别</font><font style="vertical-align: inherit;">，例如：</font></font></p>

<pre><code>var express = require('express');<font></font>
var app = express();<font></font>
<font></font>
//app.configure, app.use etc<font></font>
<font></font>
app.listen(1234);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并添加http服务器：</font></font></p>

<pre><code>var express = require('express');<font></font>
var http = require('http');<font></font>
<font></font>
var app = express();<font></font>
var server = http.createServer(app);<font></font>
<font></font>
//app.configure, app.use etc<font></font>
<font></font>
server.listen(1234);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有什么不同？</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
如果导航到</font></font><code>http://localhost:1234</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则得到相同的输出。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1954篇《Express.js-app.listen与server.listen》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门逆天猴子</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅出于守时的目的，请添添一点答案。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
根据</font></font><a href="https://expressjs.com/en/api.html#app.listen" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">官方文件</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过快递（）返回该应用程序实际上是一个JavaScript函数， 
   </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DESIGNED传递</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到节点的HTTP服务器作为一个回调来处理请求。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这使为应用程序的HTTP和HTTPS版本提供相同的代码库变得容易，因为该应用程序不继承自这些代码（它只是一个回调）：</font></font></p>
</blockquote>

<pre><code>http.createServer(app).listen(80);<font></font>
https.createServer(options, app).listen(443);<font></font>
</code></pre>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所述</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">app.listen（）</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法返回的</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http.Server</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对象和（对于HTTP）是一个</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方便的方法</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于以下情况：</font></font></p>
</blockquote>

<pre><code>app.listen = function() {<font></font>
  var server = http.createServer(this);<font></font>
  return server.listen.apply(server, arguments);<font></font>
};<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙小小米亚</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Express基本上是http模块的包装，它是为了使开发人员易于使用而创建的。</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他们可以设置中间件以使用express轻松响应HTTP请求。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他们可以使用express将参数传递给模板，从而动态呈现HTML页面。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他们还可以使用express轻松定义路由。</font></font></li>
</ol></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
