---
layout: question
title:  Nuxt.js-使用参数在URL的末尾添加斜杠
date:   2020-03-23T02:55:50.000Z
description: 该问题基于上一个问题由于SEO的原因，我希望所有URL都以斜杠结尾。到目前为止，我已经将此功能与nuxt-redirect-module一起使用r...
img: 
author: 小宇宙
category: question
answer: 0
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该问题基于</font></font><a href="https://stackoverflow.com/questions/54346345/nuxt-js-force-trailing-slash-at-the-end-of-all-urls"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上一个问题</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于SEO的原因，我希望所有URL都以斜杠结尾。</font><font style="vertical-align: inherit;">到目前为止，我已经将此功能与</font></font><a href="https://github.com/nuxt-community/redirect-module" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nuxt-redirect-module一起使用</font></font></a></p>

<pre><code>redirect: [<font></font>
    {<font></font>
        from: '^.*(?&lt;!\/)$',<font></font>
        to: (from, req) =&gt; req.url + '/'<font></font>
    }<font></font>
]<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这会检查url，并</font></font><code>/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在末尾</font><font style="vertical-align: inherit;">添加一个</font><font style="vertical-align: inherit;">（如果没有）。</font><font style="vertical-align: inherit;">问题是当url末尾有参数时。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所以现在，这个重定向</font></font></p>

<p><code>https://example.com/folder</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 至 </font></font></p>

<p><code>https://example.com/folder/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> （预期行为）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用params</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，现在它的工作方式如下：</font></font></p>

<p><code>https://example.com/folder?param=true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 至 </font></font></p>

<p><code>https://example.com/folder?param=true/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（它</font></font><code>/</code> <strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在params之后</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">添加</font><font style="vertical-align: inherit;">）</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">题</font></font></strong> </p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将是实现它的方法，因此它将重定向而不是从 </font></font></p>

<p><code>https://example.com/folder?param=true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 至 </font></font></p>

<p><code>https://example.com/folder/?param=true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
（因此它将</font></font><code>/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在url的末尾但</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在params之前</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">添加</font><font style="vertical-align: inherit;">）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提前致谢！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2702篇《Nuxt.js-使用参数在URL的末尾添加斜杠》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
