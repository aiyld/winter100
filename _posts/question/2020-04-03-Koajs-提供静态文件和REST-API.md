---
layout: question
title:  Koa.js-提供静态文件和REST API
date:   2020-04-03T03:02:55.000Z
description: 我是koa.js库的新手，我需要一些帮助。我正在尝试使用koa制作简单的REST应用程序。我有一个静态html和javascript文件，我希望在上进行路...
img: 
author: 斯丁前端
category: question
answer: 0
tags: JavaScript KoaJS
topic: KoaJS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我是koa.js库的新手，我需要一些帮助。</font><font style="vertical-align: inherit;">我正在尝试使用koa制作简单的REST应用程序。</font><font style="vertical-align: inherit;">我有一个静态html和javascript文件，我希望在上进行路由</font></font><code>/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和REST API访问</font></font><code>/api/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的项目目录树：</font></font></p>

<pre><code>project<font></font>
├── server<font></font>
│&nbsp;&nbsp; ├── node_modules<font></font>
│&nbsp;&nbsp; ├── package.json<font></font>
│&nbsp;&nbsp; └── src<font></font>
│&nbsp;&nbsp;     ├── config<font></font>
│&nbsp;&nbsp;     ├── resources<font></font>
│&nbsp;&nbsp;     └── server.js<font></font>
├── ui<font></font>
│&nbsp;&nbsp; ├── app<font></font>
│&nbsp;&nbsp; ├── bower.json<font></font>
│&nbsp;&nbsp; ├── bower_components<font></font>
│&nbsp;&nbsp; ├── dist<font></font>
│&nbsp;&nbsp; ├── node_modules<font></font>
│&nbsp;&nbsp; ├── package.json<font></font>
│&nbsp;&nbsp; └── test<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的来源：</font></font></p>

<pre><code>var app = require('koa')();<font></font>
app.use(mount('/api/places', require('../resources/places')));<font></font>
<font></font>
// does not work<font></font>
var staticKoa = require('koa')();<font></font>
staticKoa.use(function *(next){<font></font>
  yield next;<font></font>
  app.use(require('koa-static')('../ui/app', {}));<font></font>
});<font></font>
app.use(mount('/', staticKoa));<font></font>
<font></font>
// does not work<font></font>
app.use(mount('/', function*() {<font></font>
    app.use(require('koa-static')('../ui/app/', {}));<font></font>
}));<font></font>
<font></font>
// does not work<font></font>
app.use(mount('/', function*() {<font></font>
    app.use(require('koa-static')('.', {}));<font></font>
}));<font></font>
// GET package.json -&gt; 404 not found<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我试过</font></font><code>koa-static</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>koa-static-folder</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>koa-static-server</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">图书馆也不作品，所以我做错了什么。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经尝试过了并且可以使用，但是我没有访问我的REST api的权限：</font></font></p>

<pre><code>var app = require('koa')();<font></font>
app.use(require('koa-static')('../ui/app/', {}));<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3950篇《Koa.js-提供静态文件和REST API》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
