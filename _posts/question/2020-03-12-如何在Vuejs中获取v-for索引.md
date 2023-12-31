---
layout: question
title:  如何在Vue.js中获取v-for索引？
date:   2020-03-12T07:57:26.000Z
description: 我有一个像下面这样的Vue组件：<div v-for="item in items"  key="there I want get the for-l...
img: 
author: Gil理查德
category: question
answer: 2
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个像下面这样的Vue组件：</font></font></p>

<pre><code>&lt;div v-for="item in items" :key="there I want get the for-loop index"  &gt;<font></font>
<font></font>
&lt;/div&gt;<font></font>
<font></font>
... <font></font>
<font></font>
data(){<font></font>
  items: [{name:'a'}, {name:'b'}...]<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在vue.js中执行for循环时，如何获取索引？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1101篇《如何在Vue.js中获取v-for索引？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猿AJim</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用$ index获取v-for的索引。</font></font></p>

<pre><code>&lt;div v-for="item in items" :key="`$index`"  &gt;<font></font>
<font></font>
&lt;/div&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一种方法：</font></font></p>

<pre><code>&lt;div v-for="(item, index) in items" :key="index"  &gt;<font></font>
<font></font>
&lt;/div&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">DavaidAPro</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">创建一个方法：</font></font></p>

<pre><code>  methods: {<font></font>
    roleCount(key) {<font></font>
      return key + 1;<font></font>
    },<font></font>
  },<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果阵列键已编号，则从零开始。
</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">items [0]，items [1]等。</font></font></em><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
您可以使用阵列的键</font></font></p>

<pre><code>&lt;div v-for="(item, key) in items" :key="key"&gt;<font></font>
{{ incementIndex(key) }}<font></font>
&lt;/div&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，如果数组键是typeof </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">String，</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则可以</font></font></p>

<pre><code>&lt;div v-for="(item, key, index) in items" :key="key"&gt;<font></font>
{{ incementIndex(index) }}<font></font>
&lt;/div&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第二个版本使用v-for循环中的“计数器”。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
