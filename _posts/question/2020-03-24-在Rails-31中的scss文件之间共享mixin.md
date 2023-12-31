---
layout: question
title:  在Rails 3.1中的scss文件之间共享mixin
date:   2020-03-24T07:26:42.000Z
description: 我试图引用一个文件（application.css.scss）中的另一个（home.css.scss）中定义的混合。我尝试将应用程序导入家庭，但仍然收到“...
img: 
author: 猴子猿
category: question
answer: 1
tags: ruby-on-rails CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我试图引用一个文件（application.css.scss）中的另一个（home.css.scss）中定义的混合。</font><font style="vertical-align: inherit;">我尝试将应用程序导入家庭，但仍然收到“未定义的混合”错误。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有没有一种方法可以自动导入我的所有文件，或者最好的方法是管理文件之间的导入？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3439篇《在Rails 3.1中的scss文件之间共享mixin》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">纯轨解决方案</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">步骤1.</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重命名</font></font></p>

<pre><code>application.css -&gt; application.css.scss
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">步骤2.</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重构</font></font></p>

<pre><code>// application.css.scss<font></font>
<font></font>
/*<font></font>
 *= require_self<font></font>
*/<font></font>
<font></font>
@import "mixins.css.csss"<font></font>
@import "project.css.scss"<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
