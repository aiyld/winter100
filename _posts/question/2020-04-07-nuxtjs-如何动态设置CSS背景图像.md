---
layout: question
title:  nuxt.js-如何动态设置CSS背景图像
date:   2020-04-07T03:53:57.000Z
description: 我正在使用Nuxt.js，并具有一个自定义组件。 该组件中的css使用css设置背景图像。我尝试了以下操作，但是运行此程序时出现错误。错误是：...
img: 
author: LGil
category: question
answer: 1
tags: JavaScript Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用Nuxt.js，并具有一个自定义组件。 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该组件中的css使用css设置背景图像。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我尝试了以下操作，但是运行此程序时出现错误。</font><font style="vertical-align: inherit;">错误是：</font></font></p>

<pre><code> invalid expression: Invalid regular expression flags in
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">零件</font></font></strong></p>

<pre><code>&lt;template&gt;<font></font>
  &lt;section class="bg-img hero is-mobile  header-image" v-bind:style="{ backgroundImage: 'url(' + image + ')' }"&gt;<font></font>
    &lt;div class=""&gt;<font></font>
      &lt;div class="hero-body"&gt;<font></font>
        &lt;div class="container"&gt;<font></font>
          &lt;h1 class="title"&gt;<font></font>
            {{ result }}<font></font>
          &lt;/h1&gt;<font></font>
          &lt;h2 class="subtitle "&gt;<font></font>
            Hero subtitle<font></font>
          &lt;/h2&gt;<font></font>
        &lt;/div&gt;<font></font>
      &lt;/div&gt;<font></font>
    &lt;/div&gt;<font></font>
<font></font>
&lt;/section&gt;<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
<font></font>
export default {<font></font>
  props: ['result', 'image']<font></font>
}<font></font>
&lt;/script&gt;<font></font>
<font></font>
<font></font>
&lt;style&gt;<font></font>
<font></font>
<font></font>
<font></font>
.bg-img {<font></font>
        background-image: url(~/assets/autumn-tree.jpg);<font></font>
        background-position: center center;<font></font>
        background-repeat:  no-repeat;<font></font>
        background-attachment: fixed;<font></font>
        background-size:  cover;<font></font>
        background-color: #999;<font></font>
<font></font>
 }<font></font>
<font></font>
&lt;/style&gt;<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4134篇《nuxt.js-如何动态设置CSS背景图像》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony凯</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在</font></font><a href="https://github.com/nuxt/nuxt.js/issues/2123" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/nuxt/nuxt.js/issues/2123</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上找到了答案</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本上，在组件中执行以下操作：</font></font></p>

<pre><code>&lt;div :style="{ backgroundImage: `url(${backgroundUrl})` }"&gt;Content with background here&lt;/div&gt;
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
