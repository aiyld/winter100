---
layout: question
title:  Vue.js数据绑定样式backgroundImage不起作用
date:   2020-03-11T02:24:25.000Z
description: 我正在尝试将图像的src绑定到一个元素中，但是它似乎不起作用。我收到“无效的表达式。生成的函数主体：{backgroundImage：{url（image...
img: 
author: Tony米亚
category: question
answer: 1
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试将图像的src绑定到一个元素中，但是它似乎不起作用。</font><font style="vertical-align: inherit;">我收到“无效的表达式。生成的函数主体：{backgroundImage：{url（image）}”。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><a href="http://vuejs.org/guide/class-and-style.html#Object_Syntax-1" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">说使用“ Kebab-case”或“ camel-case”。</font></font></p>

<pre><code>&lt;div class="circular" v-bind:style="{ backgroundImage: { url(image) }"&gt;&lt;/div&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个小提琴：</font><a href="https://jsfiddle.net/0dw9923f/2/" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://jsfiddle.net/0dw9923f/2/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//jsfiddle.net/0dw9923f/2/</font></font></a></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第533篇《Vue.js数据绑定样式backgroundImage不起作用》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪小卤蛋</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><pre><code>&lt;div :style="{ backgroundImage: `url(${post.image})` }"&gt;
</code></pre>

<p>there are multiple ways but i found <strong>template string</strong> easy and simple</p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
