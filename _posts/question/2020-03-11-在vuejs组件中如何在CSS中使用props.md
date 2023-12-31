---
layout: question
title:  在vue.js组件中，如何在CSS中使用props？
date:   2020-03-11T09:21:24.000Z
description: 我是vue.js的新手。这是我的问题：在\* .vue文件中，如下所示：<template>  <div id="a">  </div></t...
img: 
author: 西里A
category: question
answer: 2
tags: CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我是vue.js的新手。</font><font style="vertical-align: inherit;">这是我的问题：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在* .vue文件中，如下所示：</font></font></p>

<pre><code>&lt;template&gt;<font></font>
  &lt;div id="a"&gt;<font></font>
  &lt;/div&gt;<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
  export default {<font></font>
    name: 'SquareButton',<font></font>
    props: ['color']<font></font>
  }<font></font>
&lt;/script&gt;<font></font>
<font></font>
&lt;style scoped&gt;<font></font>
    #a {<font></font>
      background-color: ?<font></font>
    }<font></font>
&lt;style&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我该如何使用道具</font><font style="vertical-align: inherit;">（</font><font style="vertical-align: inherit;">现在</font></font><code>color</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><code>background-color:</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">哪里</font></font><code>?</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谢谢。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第750篇《在vue.js组件中，如何在CSS中使用props？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋斯丁</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为什么不</font></font><code>:style</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以这种方式</font><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">prop：</font></font></p>

<pre><code>&lt;template&gt;<font></font>
  &lt;div :style="{ backgroundColor: color }"&gt;<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
export default {<font></font>
  props: {<font></font>
    color: {<font></font>
      type: String,<font></font>
      default: ''<font></font>
    }<font></font>
  }<font></font>
}<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保以camelCase样式定义css属性。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙斯丁</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您实际上可以！ </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您应该在计算属性中定义CSS变量，然后将计算属性作为需要CSS变量的元素的样式来调用，最后可以在文档底部的标记中使用该变量。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里看看：</font><a href="https://codepen.io/richardtallent/pen/yvpERW/" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> :
 </font></font><a href="https://codepen.io/richardtallent/pen/yvpERW/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//codepen.io/richardtallent/pen/yvpERW/</font></font></a></p>

<pre><code>some code to make the link work.
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并在这里：</font><a href="https://github.com/vuejs/vue/issues/7346" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> :
 </font></font><a href="https://github.com/vuejs/vue/issues/7346" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/vuejs/vue/issues/7346</font></font></a> </p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
