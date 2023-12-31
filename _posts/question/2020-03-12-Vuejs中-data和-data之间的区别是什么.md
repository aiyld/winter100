---
layout: question
title:  Vue.js中“ data：”和“ data（）”之间的区别是什么？
date:   2020-03-12T08:30:58.000Z
description: 我以两种方式使用了数据选项。在第一段数据对象中包含一个键值，但是在第二段数据中则是一个函数。个人有什么好处。无法在Vue.js文档中找到相关说明。这是两个...
img: 
author: 蛋蛋L西里
category: question
answer: 1
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我以两种方式使用了数据选项。</font><font style="vertical-align: inherit;">在第一段数据对象中包含一个键值，但是在第二段数据中则是一个函数。</font><font style="vertical-align: inherit;">个人有什么好处。无法在Vue.js文档中找到相关说明。这是两个代码段：</font></font></p>

<pre><code>new Vue({<font></font>
  el: "#app",<font></font>
  data: {<font></font>
      message: 'hello mr. magoo'<font></font>
    }<font></font>
<font></font>
});<font></font>
<font></font>
new Vue({<font></font>
  el: "#app",<font></font>
  data() {<font></font>
    return {<font></font>
      message: 'hello mr. magoo'<font></font>
    }<font></font>
  }<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">两者都给我相同的输出。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1136篇《Vue.js中“ data：”和“ data（）”之间的区别是什么？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Harry路易</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在考虑您的特定代码示例时，似乎您对问题的评论缺少关键点。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在根Vue实例（即通过构造）中</font></font><code>new Vue({ . . . })</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，您可以简单地使用</font></font><code>data: { . . . }</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不会出现任何问题。问题是当您具有通过定义的可重用组件时，</font></font><code>Vue.component(. . .)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这些实例中，您需要使用</font></font><code>data() {return { . . . };}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>data: function() {return { . . . };}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这样做的原因是为了确保可重用子组件的每个单独实例都有一个唯一的对象，其中包含正在操作的所有数据。</font><font style="vertical-align: inherit;">如果在子组件中改为使用</font></font><code>data: { . . . }</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则子组件之间将共享同一数据对象，这可能会导致一些讨厌的错误。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请查看</font></font><a href="https://vuejs.org/v2/guide/components.html#data-Must-Be-a-Function" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Vue.js文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font><a href="https://vuejs.org/v2/guide/components.html#data-Must-Be-a-Function" rel="noreferrer"><font style="vertical-align: inherit;">相应部分，以</font></a><font style="vertical-align: inherit;">获取有关此问题的更多信息。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
