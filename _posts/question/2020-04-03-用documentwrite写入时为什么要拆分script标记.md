---
layout: question
title:  用document.write（）写入时，为什么要拆分<script>标记？
date:   2020-04-03T02:20:48.000Z
description: 为什么某些网站（或为客户提供JavaScript代码的广告商）采用在呼叫内拆分<script>和/或</script>标签的技术document.writ...
img: 
author: Stafan
category: question
answer: 1
tags: JavaScript HTML
topic: HTML
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为什么某些网站（或为客户提供JavaScript代码的广告商）采用</font><font style="vertical-align: inherit;">在</font><font style="vertical-align: inherit;">呼叫</font><font style="vertical-align: inherit;">内</font><font style="vertical-align: inherit;">拆分</font></font><code>&lt;script&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和/或</font></font><code>&lt;/script&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">标签</font><font style="vertical-align: inherit;">的技术</font></font><code>document.write()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我注意到亚马逊也这样做，例如：</font></font></p>

<pre><code>&lt;script type='text/javascript'&gt;<font></font>
  if (typeof window['jQuery'] == 'undefined') document.write('&lt;scr'+'ipt type="text/javascript" src="http://z-ecx.images-amazon.com/images/G/01/javascripts/lib/jquery/jquery-1.2.6.pack._V265113567_.js"&gt;&lt;/sc'+'ript&gt;');<font></font>
&lt;/script&gt;<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3883篇《用document.write（）写入时，为什么要拆分<script>标记？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为这是为了防止浏览器的HTML解析器将&lt;script&gt;（主要是&lt;/ script&gt;）解释为实际脚本的结束标记，但是我不认为使用document.write是评估脚本的好主意。块，为什么不使用DOM ...</font></font></p>

<pre><code>var newScript = document.createElement("script");<font></font>
...<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
