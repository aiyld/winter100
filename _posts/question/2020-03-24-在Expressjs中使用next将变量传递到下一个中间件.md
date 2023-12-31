---
layout: question
title:  在Express.js中使用next（）将变量传递到下一个中​​间件
date:   2020-03-24T06:05:05.000Z
description: 好吧，我的问题是我想将一些变量从第一个中间件传递给另一个中间件，我尝试这样做，但是有req.somevariable一个“给定为'undefined'”。...
img: 
author: Davaid阳光伽罗
category: question
answer: 5
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">好吧，我的问题是我想将一些变量从第一个中间件传递给另一个中间件，我尝试这样做，但是有</font></font><code>req.somevariable</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个“给定为'undefined'”。</font></font></p>

<hr>

<pre><code>//app.js<font></font>
..<font></font>
app.get('/someurl/', middleware1, middleware2)<font></font>
...<font></font>
</code></pre>

<hr>

<pre><code>////middleware1<font></font>
...<font></font>
some conditions<font></font>
...<font></font>
res.somevariable = variable1;<font></font>
next();<font></font>
...<font></font>
</code></pre>

<hr>

<pre><code>////middleware2<font></font>
...<font></font>
some conditions<font></font>
...<font></font>
variable = req.somevariable;<font></font>
...<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3338篇《在Express.js中使用next（）将变量传递到下一个中​​间件》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Gil</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如上所述，res.locals是一种很好的方法（推荐）。</font><font style="vertical-align: inherit;">有关</font><font style="vertical-align: inherit;">如何在Express中执行此操作的快速教程，</font><font style="vertical-align: inherit;">请参见</font></font><a href="https://youtu.be/zPYmM9K8-g8" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此处</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那是因为</font></font><code>req</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>res</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是两个不同的对象。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您需要在添加属性的同一对象上查找属性。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy村村</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为最佳做法不会传递类似的变量</font></font><code>req.YOUR_VAR</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">您可能要考虑</font></font><code>req.YOUR_APP_NAME.YOUR_VAR</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>req.mw_params.YOUR_VAR</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将帮助您避免覆盖其他属性。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这就是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">res.locals</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对象的用途。</font><font style="vertical-align: inherit;">不支持也不记录直接在请求对象上设置变量。</font><font style="vertical-align: inherit;">保证</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">res.locals</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在请求的生命周期内保持状态。</font></font></p>

<p><a href="http://expressjs.com/en/api.html#res.locals" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本地人</font></font></a></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个对象，该对象包含范围为请求的响应局部变量，因此仅可用于在该请求/响应周期（如果有）中呈现的视图。</font><font style="vertical-align: inherit;">否则，此属性与app.locals相同。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此属性对于公开请求级别的信息很有用，例如请求路径名，经过身份验证的用户，用户设置等。</font></font></p>
</blockquote>



<pre class="lang-js prettyprint-override"><code>app.use(function(req, res, next) {<font></font>
    res.locals.user = req.user;  <font></font>
    res.locals.authenticated = !req.user.anonymous;<font></font>
    next();<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要在下一个中间件中检索变量：</font></font></p>



<pre class="lang-js prettyprint-override"><code>app.use(function(req, res, next) {<font></font>
    if (res.locals.authenticated) {<font></font>
        console.log(res.locals.user.id);<font></font>
    }<font></font>
    next();<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将变量附加到</font></font><code>req</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对象，而不是</font></font><code>res</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代替</font></font></p>

<pre><code>res.somevariable = variable1;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有：</font></font></p>

<pre><code>req.somevariable = variable1;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正如其他人指出的那样，</font></font><code>res.locals</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">推荐的方法是通过中间件传递数据。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
