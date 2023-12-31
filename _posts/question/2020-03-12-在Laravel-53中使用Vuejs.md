---
layout: question
title:  在Laravel 5.3中使用Vue.js
date:   2020-03-12T10:22:16.000Z
description: 在5.3之前的Laravel项目中，我已经使用Vue.js并使用了脚本标签，如下所示：<script type="text/javascript" s...
img: 
author: 猿米亚
category: question
answer: 1
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在5.3之前的Laravel项目中，我已经使用Vue.js并使用了脚本标签，如下所示：</font></font></p>

<pre><code>&lt;script type="text/javascript" src="../js/vue.js"&gt;&lt;/script&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，我将为该页面创建一个Vue实例，如下所示：</font></font></p>

<pre><code>&lt;script&gt;<font></font>
    new Vue({<font></font>
      el: '#app',<font></font>
      data: {<font></font>
        message: 'Hello Vue.js!'<font></font>
      }<font></font>
    });<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后将其绑定到HTML中的相关div＃id。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，在Laravel 5.3中捆绑了Vue.js，我完全意识到我可以通过使用gulp / elixir使用文档中所述的组件，但是，我的问题是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我是否要像刚才提到的那样创建Vue.js实例，即我严格为给定页面（不是组件）创建Vue.js实例的方式？</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是否像以前那样通过在脚本标签中导入vue.js库来进行设置，还是可以使用生成的app.js？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不应该这样做吗，我应该为所有内容创建组件吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我来说，为仅使用一次的组件制作组件是没有意义的-我认为组件的目的是可重用-您可以在多个地方使用它。</font><font style="vertical-align: inherit;">如Vue.js文档中所述：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件是Vue.js最强大的功能之一。</font><font style="vertical-align: inherit;">它们可以帮助您扩展基本HTML元素以封装</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可重用的代码</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">任何建议，将不胜感激，谢谢！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1277篇《在Laravel 5.3中使用Vue.js》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">ItachiGreen</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您使用的是Laravel 5.5及更高版本，那么这是最好的解决方案，如果您想利用Blade的强大功能但仍然喜欢VueJS的反应</font></font></p>

<p><a href="https://stackoverflow.com/a/54349029/417899"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://stackoverflow.com/a/54349029/417899</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
