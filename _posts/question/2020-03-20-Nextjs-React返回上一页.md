---
layout: question
title:  Next.js + React返回上一页
date:   2020-03-20T06:17:01.000Z
description: 我使用路由next.js。如何实现后退按钮并返回上一页？就像浏览器上的按钮一样...
img: 
author: Tony凯
category: question
answer: 1
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我使用路由next.js。</font><font style="vertical-align: inherit;">如何实现后退按钮并返回上一页？</font><font style="vertical-align: inherit;">就像浏览器上的按钮一样</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2536篇《Next.js + React返回上一页》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan路易</span>
            <span class="discuss-time">2020.03.20</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">next / link为您完成所有location.history处理。</font><font style="vertical-align: inherit;">您甚至不需要编写一行客户端路由代码。</font><font style="vertical-align: inherit;">这没有任何属性。</font><font style="vertical-align: inherit;">而是创建一个功能组件</font></font></p>

<pre><code>const BsNavLink=(props)=&gt;{<font></font>
   const {route,title}=props<font></font>
   return ( &lt;Link  href={route}&gt;&lt;a &gt;{title}&lt;/a&gt;&lt;/Link&gt;)<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这种情况下，next / link组件的子代是锚标记。</font><font style="vertical-align: inherit;">它也可以与任何其他组件或标签一起使用，放置在其中的组件的唯一要求是它们应接受onClick道具。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
