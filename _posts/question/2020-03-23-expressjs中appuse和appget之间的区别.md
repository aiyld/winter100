---
layout: question
title:  express.js中app.use和app.get之间的区别
date:   2020-03-23T07:22:33.000Z
description: 我是表示和node.js的新手，我无法弄清app.use和app.get之间的区别。似乎您可以同时使用它们来发送信息。例如：app.use('/',f...
img: 
author: 伽罗理查德
category: question
answer: 3
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我是表示和node.js的新手，我无法弄清app.use和app.get之间的区别。</font><font style="vertical-align: inherit;">似乎您可以同时使用它们来发送信息。</font><font style="vertical-align: inherit;">例如：</font></font></p>

<pre><code>app.use('/',function(req, res,next) {<font></font>
    res.send('Hello');<font></font>
    next();<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">似乎与此相同：</font></font></p>

<pre><code>app.get('/', function (req,res) {<font></font>
   res.send('Hello');<font></font>
});<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2905篇《express.js中app.use和app.get之间的区别》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需app.use表示“对所有请求运行此操作” </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
app.get意味着“针对给定的URL对GET请求运行此操作”</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Gil伽罗小宇宙</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><code>app.get</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当</font></font><a href="http://www.w3schools.com/tags/ref_httpmethods.asp"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">HTTP方法</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">设置</font></font><code>GET</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为时</font></font><code>app.use</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">调用</font><font style="vertical-align: inherit;">，而</font><font style="vertical-align: inherit;">无论HTTP方法如何都调用，因此定义了一个层，该层位于Express包允许您访问的所有其他RESTful类型的顶部。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><code>app.use</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 是Express依赖的中间件框架Connect的“较低级别”方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的指导方针：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>app.get</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是否要公开一个GET方法。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>app.use</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，如果你想添加一些中间件（的处理程序HTTP请求它到达您在快速设置路线之前），或者如果你想使你的路由模块（例如，公开了一组路线来自其他Web应用程序可以使用的npm模块）。</font></font></li>
</ul></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
