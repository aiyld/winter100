---
layout: question
title:  使用JSON.stringify(obj)，结果中包含了大量的引号
date:   2018-11-14T09:05:12.000Z
description: 在html模板生成中的代码是这样的<script id="stateContainer" type="text/json"><% = JSON.stringif...
img: 
author: Winter
category: question
answer: 1
tags: 前端的一些坑
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p>在html模板生成中的代码是这样的</p>

<p>&lt;script id=&quot;stateContainer&quot; type=&quot;text/json&quot;&gt;&lt;% = JSON.stringify(state)%&gt;&lt;/script&gt;</p>

<p>结果就得到了一串的字符中包含了大量的&amp;#34;&nbsp;，它自动的把引号&quot;转为了编码&amp;#34;</p>
</div>
    {% endraw %}
  </div>
  <p class="winter_mark">第103篇《使用JSON.stringify(obj)，结果中包含了大量的引号》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Winter</span>
            <span class="discuss-time">2018.11.14</span>
          </div>
          <div class="discuss-comment"><p>要把&lt;% = JSON.stringify(state)%&gt;改成&lt;%-&nbsp;JSON.stringify(state)%&gt;</p>
</div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
