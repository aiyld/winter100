---
layout: question
title:  document.getElementById与jQuery $（）
date:   2020-03-11T15:34:57.000Z
description: 这是：var contents = document.getElementById('contents');与此相同：var content...
img: 
author: 宝儿猿
category: question
answer: 3
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是：</font></font></p>

<pre><code>var contents = document.getElementById('contents');
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与此相同：</font></font></p>

<pre><code>var contents = $('#contents');
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">鉴于jQuery已加载？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第860篇《document.getElementById与jQuery $（）》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva斯丁</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就像大多数人说的那样，主要区别在于以下事实：使用直接调用JavaScript将其包装在带有jQuery调用的jQuery对象中，而不是使用原始DOM对象。</font><font style="vertical-align: inherit;">jQuery对象当然可以使用它执行其他jQuery功能，但是，如果您只需要执行简单的DOM操作（如基本样式或基本事件处理），那么直接的JavaScript方法总是比jQuery快一点，因为您不需要不必加载基于JavaScript的外部代码库。</font><font style="vertical-align: inherit;">它节省了额外的步骤。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪蛋蛋</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我开发了一个noSQL数据库，用于在Web浏览器中存储DOM树，其中将对页面上所有DOM元素的引用存储在短索引中。</font><font style="vertical-align: inherit;">因此，不需要函数“ getElementById（）”来获取/修改元素。</font><font style="vertical-align: inherit;">当在页面上实例化DOM树中的元素时，数据库将为每个元素分配代理主键。</font><font style="vertical-align: inherit;">这是一个免费工具</font></font><a href="http://js2dx.com" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://js2dx.com</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋Itachi</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jQuery是基于JavaScript构建的。</font><font style="vertical-align: inherit;">这意味着无论如何它只是JavaScript。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">document.getElementById（）</font></font></strong></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">document.getElementById（）方法返回具有具有指定值的ID属性的元素，如果不存在具有指定ID的元素，则返回null。一个ID在页面内应唯一。</font></font></p>
</blockquote>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jQuery $（）</font></font></strong></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以id选择器作为参数调用jQuery（）或$（）将返回一个jQuery对象，该对象包含一个零或一个DOM元素的集合。每个id值在文档中只能使用一次。</font><font style="vertical-align: inherit;">如果为多个元素分配了相同的ID，则使用该ID的查询将仅选择DOM中的第一个匹配元素。</font></font></p>
</blockquote></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
