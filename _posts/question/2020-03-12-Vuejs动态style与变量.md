---
layout: question
title:  Vue.js动态<style>与变量
date:   2020-03-12T09:40:09.000Z
description: 是否可以在样式中添加动态变量？我的意思是：<style> .class_name{  background-image({{project.b...
img: 
author: 宝儿Pro
category: question
answer: 1
tags: css CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是否可以在样式中添加动态变量？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的意思是：</font></font></p>

<pre><code>&lt;style&gt;<font></font>
 .class_name{<font></font>
  background-image({{project.background}});<font></font>
 }<font></font>
@media all and (-webkit-min-device-pixel-ratio : 1.5),<font></font>
 all and (-o-min-device-pixel-ratio: 3/2),<font></font>
 all and (min--moz-device-pixel-ratio: 1.5),<font></font>
 all and (min-device-pixel-ratio: 1.5) {<font></font>
 .class_name{<font></font>
  background-image({{project.background_retina}});<font></font>
 } <font></font>
}<font></font>
&lt;/style&gt;<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1233篇《Vue.js动态<style>与变量》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神乐神乐</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一些动态特性，可以用JS和更少的代码来操作SCSS。</font><font style="vertical-align: inherit;">我用bulma如下</font></font></p>

<pre><code>&lt;style lang="scss" scoped&gt;<font></font>
  $size-10: 10px;<font></font>
  $size-9: 20px;<font></font>
  $size-8: 30px;<font></font>
  $size-7: 10px;<font></font>
  $size-6: 20px;<font></font>
  $size-5: 30px;<font></font>
  $size-4: 40px;<font></font>
  $size-3: 50px;<font></font>
  $size-2: 60px;<font></font>
  $size-1: 70px;<font></font>
  $sizes: (<font></font>
    1,<font></font>
    2,<font></font>
    3,<font></font>
    4,<font></font>
    5,<font></font>
    6,<font></font>
    7,<font></font>
    8,<font></font>
    9,<font></font>
    10<font></font>
  );<font></font>
  $positions: (<font></font>
    "top",<font></font>
    "left",<font></font>
    "bottom",<font></font>
    "right"<font></font>
  );<font></font>
  $bulmaSizes: (<font></font>
    $size-1,<font></font>
    $size-2,<font></font>
    $size-3,<font></font>
    $size-4,<font></font>
    $size-5,<font></font>
    $size-6,<font></font>
    $size-7,<font></font>
    $size-8,<font></font>
    $size-9,<font></font>
    $size-10<font></font>
  );<font></font>
  $i: 1;<font></font>
  @each $size in $sizes {<font></font>
    $sizee: nth($bulmaSizes, $i);<font></font>
    $i: $i+1;<font></font>
    .has-margin-#{$size} {<font></font>
      margin: $sizee !important;<font></font>
    }<font></font>
    @each $position in $positions {<font></font>
      .has-padding-#{$position}-#{$size} {<font></font>
        margin-#{$position}: $sizee !important;<font></font>
      }<font></font>
    }<font></font>
  }<font></font>
&lt;/style&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望这会对你们中的一些人有所帮助。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
