---
layout: question
title:  $ router.push中的Params字段为空
date:   2020-03-18T11:14:37.000Z
description: 考虑一下：this.$root.$router.push({    path  '/dashboard',     params  { error...
img: 
author: MonsterKK梅
category: question
answer: 0
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">考虑一下：</font></font></p>

<pre><code>this.$root.$router.push({<font></font>
    path: '/dashboard', <font></font>
    params: { errors: 'error' }, <font></font>
    query: { test: 'test' }<font></font>
})<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在组件中使用它来重定向到另一个URL，并且发生了一些错误。</font><font style="vertical-align: inherit;">问题是，当我要访问</font></font><code>params</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仪表板组件中的字段时，该字段为空。</font><font style="vertical-align: inherit;">该</font></font><code>query</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">领域运作良好。</font><font style="vertical-align: inherit;">我正在尝试通过访问它</font></font><code>this.$route.params.errors</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2175篇《$ router.push中的Params字段为空》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
