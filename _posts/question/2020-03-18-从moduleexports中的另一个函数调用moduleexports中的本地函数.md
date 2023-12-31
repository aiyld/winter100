---
layout: question
title:  从module.exports中的另一个函数调用module.exports中的“本地”函数？
date:   2020-03-18T10:02:32.000Z
description: 如何在module.exports声明中的另一个函数中调用一个函数？app.jsvar bla = require('./bla.js');co...
img: 
author: 逆天AGreen
category: question
answer: 2
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何在</font></font><code>module.exports</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">声明中的</font><font style="vertical-align: inherit;">另一个函数中调用一个函数</font><font style="vertical-align: inherit;">？</font></font></p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">

app.js

</font></font><pre><code>var bla = require('./bla.js');<font></font>
console.log(bla.bar());<font></font>
</code></pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">

bla.js

</font></font><pre><code>module.exports = {<font></font>
<font></font>
  foo: function (req, res, next) {<font></font>
    return ('foo');<font></font>
  },<font></font>
<font></font>
  bar: function(req, res, next) {<font></font>
    this.foo();<font></font>
  }<font></font>
<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试</font></font><code>foo</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从</font><font style="vertical-align: inherit;">函数</font><font style="vertical-align: inherit;">内部</font><font style="vertical-align: inherit;">访问</font><font style="vertical-align: inherit;">函数</font></font><code>bar</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并且得到：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TypeError：对象＃没有方法'foo'</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果我更改</font></font><code>this.foo()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为仅</font></font><code>foo()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">得到：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ReferenceError：未定义foo</font></font></p>
</blockquote></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2133篇《从module.exports中的另一个函数调用module.exports中的“本地”函数？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">前端神无</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><pre><code>const Service = {<font></font>
  foo: (a, b) =&gt; a + b,<font></font>
  bar: (a, b) =&gt; Service.foo(a, b) * b<font></font>
}<font></font>
<font></font>
module.exports = Service<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿猿</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更改</font></font><code>this.foo()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font><code>module.exports.foo()</code></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
