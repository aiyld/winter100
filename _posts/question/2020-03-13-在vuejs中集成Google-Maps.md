---
layout: question
title:  在vue.js中集成Google Maps
date:   2020-03-13T07:37:01.000Z
description: 我一直在尝试尝试在vue.js项目中初始化Google地图，同时添加以下脚本：<script src="https //maps.googleapis...
img: 
author: 番长十三小宇宙
category: question
answer: 0
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我一直在尝试尝试在vue.js项目中初始化Google地图，同时添加以下脚本：</font></font></p>

<pre><code>&lt;script src="https://maps.googleapis.com/maps/api/js?key="MY_API_KEY"&amp;callback=initMap" async defer&gt;&lt;/script&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题是我的.vue文件看起来像这样： </font></font></p>

<pre><code>&lt;template&gt;<font></font>
  ...<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
  ...<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而且我不能在vue文件中包含多个脚本标签，我可以在通过index.html的同时显示地图，但是我真的不想在index.html上放置js，+我无法指向脚本在vue方法上回调。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你们对如何使用.vue文件显示地图有一些想法吗？</font><font style="vertical-align: inherit;">我确实使用过vue2-google-maps，但我想使用原始的google map。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个小提琴，它做的很好：</font></font><a href="https://jsfiddle.net/okubdoqa/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> : </font><font style="vertical-align: inherit;">//jsfiddle.net/okubdoqa/在脚本标签中不使用回调，但是对我来说不起作用...谢谢</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1397篇《在vue.js中集成Google Maps》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
