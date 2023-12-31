---
layout: question
title:  express.Router和app.get之间的区别？
date:   2020-03-20T05:49:18.000Z
description: 我从NodeJS和Express 4开始，我有些困惑。我一直在阅读Express网站，但看不到何时使用路由处理程序或何时使用express.Router。...
img: 
author: 猪猪
category: question
answer: 4
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我从NodeJS和Express 4开始，我有些困惑。</font><font style="vertical-align: inherit;">我一直在阅读Express网站，但看不到</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">何时</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用路由处理程序或何时使用</font></font><code>express.Router</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如我所见，例如，如果我想在用户点击时显示页面或其他内容，</font></font><code>/show</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则应使用：</font></font></p>

<pre><code>var express = require('express')    <font></font>
var app = express()    <font></font>
app.get("/show", someFunction)  <font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一开始，我认为这很旧（对于Express 3）。</font><font style="vertical-align: inherit;">是这样吗，还是Express 4也是如此？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果这是在Express 4中实现的方式，那么它的</font></font><code>express.Router</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用途是什么？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我读了几乎与上面相同的示例，但是使用了</font></font><code>express.Router</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>var express = require('express');<font></font>
var router = express.Router();<font></font>
router.get("/show", someFunction)<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么，两个示例之间有什么区别？ </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果我只想创建一个简单的测试网站，应该使用哪一个？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2495篇《express.Router和app.get之间的区别？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">null</span>
            <span class="discuss-time">2020.03.20</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">总之</font><font style="vertical-align: inherit;">，与中间件</font></font><code>express.Router</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相比</font><font style="vertical-align: inherit;">，它</font><font style="vertical-align: inherit;">可以做更多的事情</font></font><code>app.get()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，而且，您可以使用</font></font><code>express.Router()</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">EvaTom</span>
            <span class="discuss-time">2020.03.20</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用app.js编写路由意味着当在应用程序启动时加载app.js时，所有用户都可以访问它们。</font><font style="vertical-align: inherit;">但是，将路由放入express.router（）微型应用程序会保护并限制其可访问性。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋猿</span>
            <span class="discuss-time">2020.03.20</span>
          </div>
          <div class="discuss-comment"><p><code>express.Router</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 有很多选择：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">启用区分大小写：</font></font><code>/show</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">路由与不相同</font></font><code>/Show</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，默认情况下禁用此行为</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">严格的路由模式：</font></font><code>/show/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">路由到不相同</font></font><code>/show</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，默认情况下也禁用此行为</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们可以将特定的中间件添加到特定的路由</font></font></li>
</ul></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯西里</span>
            <span class="discuss-time">2020.03.20</span>
          </div>
          <div class="discuss-comment"><p>Express 4.0 comes with the new Router. As mentioned on the site: </p>

<blockquote>
  <p>The express.Router class can be used to create modular mountable route
  handlers. A Router instance is a complete middleware and routing
  system; for this reason it is often referred to as a “mini-app”.</p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><a href="https://scotch.io/tutorials/learn-to-use-the-new-router-in-expressjs-4" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://scotch.io/tutorials/learn-to-use-the-new-router-in-expressjs-4中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有一篇很好的文章</font><font style="vertical-align: inherit;">，描述了差异以及如何使用路由器。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">总结一下</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用路由器，您可以更轻松地将代码模块化。</font><font style="vertical-align: inherit;">您可以将路由器用作：</font></font></p>

<blockquote>
  <ol>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本路线：首页，关于</font></font></li>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">路由中间件以将请求记录到控制台</font></font></li>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">带参数的路线</font></font></li>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">路由中间件获取参数以验证特定参数</font></font></li>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">验证传递给特定路由的参数</font></font></li>
  </ol>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：</font></font></p>

<p><font style="vertical-align: inherit;"></font><code>app.router</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Express 4中删除</font><font style="vertical-align: inherit;">的</font><font style="vertical-align: inherit;">对象在Express 5中又卷土重来。在新版本中，它只是对基本Express路由器的引用，与Express 3不同，在Express 3中，应用程序必须显式加载它。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
