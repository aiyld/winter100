---
layout: question
title:  在React.js中设置onSubmit
date:   2020-03-12T09:03:04.000Z
description: 在提交表单时，我尝试doSomething()代替默认的发布行为。显然在React中，onSubmit是表单支持的事件。但是，当我尝试以下代码时：...
img: 
author: 阿飞A
category: question
answer: 1
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在提交表单时，我尝试</font></font><code>doSomething()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代替默认的发布行为。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">显然在React中，</font></font><a href="http://facebook.github.io/react/docs/events.html#form-events" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">onSubmit是表单支持的事件。</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，当我尝试以下代码时：</font></font></p>

<pre><code>var OnSubmitTest = React.createClass({<font></font>
    render: function() {<font></font>
        doSomething = function(){<font></font>
           alert('it works!');<font></font>
        }<font></font>
<font></font>
        return &lt;form onSubmit={doSomething}&gt;<font></font>
        &lt;button&gt;Click me&lt;/button&gt;<font></font>
        &lt;/form&gt;;<font></font>
    }<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该方法</font></font><code>doSomething()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">已运行，但是此后仍执行默认的发布行为。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以在我的</font></font><a href="https://jsfiddle.net/ayda5w9m/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jsfiddle中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行测试</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的问题：如何防止默认的发布行为？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1172篇《在React.js中设置onSubmit》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猴子樱</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><pre><code>&lt;form onSubmit={(e) =&gt; {this.doSomething(); e.preventDefault();}}&gt;&lt;/form&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我来说很好</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
