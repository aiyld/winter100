---
layout: question
title:  在Vue.js中，如何通过在main.js中进行声明，在单独的文件中编写自定义过滤器，并在各种组件中使用它们？
date:   2020-03-17T07:10:13.000Z
description: 我尝试这样做，但是不起作用。    // filter.jsexport default {    converTimestamp  funct...
img: 
author: 古一Pro
category: question
answer: 0
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我尝试这样做，但是不起作用。    </font></font></p>

<pre class="lang-js prettyprint-override"><code>// filter.js<font></font>
<font></font>
export default {<font></font>
    converTimestamp: function (seconds) {<font></font>
      var date = new Date(seconds * 1000);<font></font>
      return date.toDateString();<font></font>
    }<font></font>
};<font></font>
<font></font>
// main.js<font></font>
<font></font>
import customFilters from './store/filters';<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1887篇《在Vue.js中，如何通过在main.js中进行声明，在单独的文件中编写自定义过滤器，并在各种组件中使用它们？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
