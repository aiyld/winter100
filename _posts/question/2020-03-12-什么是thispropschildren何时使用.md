---
layout: question
title:  什么是{this.props.children}？何时使用？
date:   2020-03-12T10:08:41.000Z
description: 作为React世界的初学者，我想深入了解我使用时会发生{this.props.children}什么以及使用该情况的情况。下面的代码片段与它有什么关系？...
img: 
author: 前端猿
category: question
answer: 0
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为React世界的初学者，我想深入了解我使用时会发生</font></font><code>{this.props.children}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">什么以及</font><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">该情况的情况。</font><font style="vertical-align: inherit;">下面的代码片段与它有什么关系？</font></font></p>

<pre><code>render() {<font></font>
  if (this.props.appLoaded) {<font></font>
    return (<font></font>
      &lt;div&gt;<font></font>
        &lt;Header<font></font>
          appName={this.props.appName}<font></font>
          currentUser={this.props.currentUser}<font></font>
        /&gt;<font></font>
        {this.props.children}<font></font>
      &lt;/div&gt;<font></font>
    );<font></font>
  }<font></font>
}<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1253篇《什么是{this.props.children}？何时使用？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
