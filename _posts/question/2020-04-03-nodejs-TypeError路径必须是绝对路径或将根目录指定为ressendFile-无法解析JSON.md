---
layout: question
title:  node.js TypeError：路径必须是绝对路径或将根目录指定为res.sendFile \[无法解析JSON\]
date:   2020-04-03T04:16:47.000Z
description: \[添加\]因此，我的下一个问题是，当我尝试添加新的依赖项时（npm install --save socket.io）。JSON文件也有效。我收到此错误：无...
img: 
author: 路易Eva
category: question
answer: 1
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">[添加]因此，我的下一个问题是，当我尝试添加新的依赖项时（npm install --save socket.io）。</font><font style="vertical-align: inherit;">JSON文件也有效。</font><font style="vertical-align: inherit;">我收到此错误：无法解析json</font></font></p>

<pre><code>npm ERR! Unexpected string<font></font>
npm ERR! File: /Users/John/package.json<font></font>
npm ERR! Failed to parse package.json data.<font></font>
npm ERR! package.json must be actual JSON, not just JavaScript.<font></font>
npm ERR! <font></font>
npm ERR! This is not a bug in npm.<font></font>
npm ERR! Tell the package author to fix their package.json file. JSON.parse <font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，我一直在尝试找出为什么此错误一直在返回。</font><font style="vertical-align: inherit;">所有文件（HTML，JSON，JS）都在我桌面上的同一文件夹内。</font><font style="vertical-align: inherit;">我正在使用node.js和socket.io</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的JS文件：</font></font></p>

<pre><code>var app = require('express')();<font></font>
var http = require('http').Server(app);<font></font>
<font></font>
app.get('/', function(req, res){<font></font>
  res.sendFile('index.html');<font></font>
});<font></font>
<font></font>
http.listen(3000,function(){<font></font>
    console.log('listening on : 3000');<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是返回的内容：</font></font></p>

<pre><code>MacBook-Pro:~ John$ node /Users/John/Desktop/Chatapp/index.js <font></font>
listening on : 3000<font></font>
TypeError: path must be absolute or specify root to res.sendFile<font></font>
    at ServerResponse.sendFile (/Users/John/node_modules/express/lib/response.js:389:11)<font></font>
    at /Users/John/Desktop/Chatapp/index.js:5:7<font></font>
    at Layer.handle [as handle_request] (/Users/John/node_modules/express/lib/router/layer.js:76:5)<font></font>
    at next (/Users/John/node_modules/express/lib/router/route.js:100:13)<font></font>
    at Route.dispatch (/Users/John/node_modules/express/lib/router/route.js:81:3)<font></font>
    at Layer.handle [as handle_request] (/Users/John/node_modules/express/lib/router/layer.js:76:5)<font></font>
    at /Users/John/node_modules/express/lib/router/index.js:234:24<font></font>
    at Function.proto.process_params (/Users/John/node_modules/express/lib/router/index.js:312:12)<font></font>
    at /Users/John/node_modules/express/lib/router/index.js:228:12<font></font>
    at Function.match_layer (/Users/John/node_modules/express/lib/router/index.js:295:3)<font></font>
TypeError: path must be absolute or specify root to res.sendFile<font></font>
    at ServerResponse.sendFile (/Users/John/node_modules/express/lib/response.js:389:11)<font></font>
    at /Users/John/Desktop/Chatapp/index.js:5:7<font></font>
    at Layer.handle [as handle_request] (/Users/John/node_modules/express/lib/router/layer.js:76:5)<font></font>
    at next (/Users/John/node_modules/express/lib/router/route.js:100:13)<font></font>
    at Route.dispatch (/Users/John/node_modules/express/lib/router/route.js:81:3)<font></font>
    at Layer.handle [as handle_request] (/Users/John/node_modules/express/lib/router/layer.js:76:5)<font></font>
    at /Users/John/node_modules/express/lib/router/index.js:234:24<font></font>
    at Function.proto.process_params (/Users/John/node_modules/express/lib/router/index.js:312:12)<font></font>
    at /Users/John/node_modules/express/lib/router/index.js:228:12<font></font>
    at Function.match_layer (/Users/John/node_modules/express/lib/router/index.js:295:3)<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4015篇《node.js TypeError：路径必须是绝对路径或将根目录指定为res.sendFile \[无法解析JSON\]》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tom凯</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这可以通过另一种方式解决： </font></font></p>

<pre><code>app.get("/", function(req, res){<font></font>
<font></font>
    res.send(`${process.env.PWD}/index.html`)<font></font>
<font></font>
});<font></font>
</code></pre>

<p><code>process.env.PWD</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 进程启动时，它将在工作目录之前。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
