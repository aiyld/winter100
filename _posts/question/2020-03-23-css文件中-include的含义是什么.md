---
layout: question
title:  .css文件中“ \`include”的含义是什么？
date:   2020-03-23T13:50:19.000Z
description: 我不明白，.css文件中\`include标记的含义是什么。例如 ：.wrapper {display  flex;width  100%;\`in...
img: 
author: 村村
category: question
answer: 1
tags: CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不明白，.css文件中@include标记的含义是什么。</font><font style="vertical-align: inherit;">例如 ：</font></font></p>

<pre><code>.wrapper {<font></font>
display: flex;<font></font>
width: 100%;<font></font>
@include display(flex);<font></font>
@include flex-direction(column);<font></font>
@include align-items(center);<font></font>
@include justify-content(center);<font></font>
@include transition(all 2s linear);<font></font>
}<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3098篇《.css文件中“ \`include”的含义是什么？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><code>@include</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是SCSS的一部分，称为Mixin。</font><font style="vertical-align: inherit;">这是一个例子：</font></font></p>

<pre><code>@mixin border-radius($radius) {<font></font>
    -webkit-border-radius: $radius;<font></font>
       -moz-border-radius: $radius;<font></font>
        -ms-border-radius: $radius;<font></font>
            border-radius: $radius;<font></font>
}<font></font>
<font></font>
.box { @include border-radius(10px); }<font></font>
</code></pre>

<p><code>@include</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">s是存储特别是诸如供应商前缀之类的东西的快捷方式。</font><font style="vertical-align: inherit;">上面的CSS输出将是：</font></font></p>

<pre><code>.box {<font></font>
    -webkit-border-radius: 10px;<font></font>
       -moz-border-radius: 10px;<font></font>
        -ms-border-radius: 10px;<font></font>
            border-radius: 10px;<font></font>
}<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
