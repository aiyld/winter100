---
layout: question
title:  如何在sass中将.css文件导入为.scss文件？
date:   2020-03-24T09:13:57.000Z
description: 我正在使用gulp作为任务运行程序，scss为我合并和缩小文件。在这种情况下，如果我尝试导入常规CSS文件，它将编译import为如下的css 语句：...
img: 
author: 斯丁
category: question
answer: 0
tags: CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用gulp作为任务运行程序，</font></font><code>scss</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为我</font><font style="vertical-align: inherit;">合并和缩小</font><font style="vertical-align: inherit;">文件。</font><font style="vertical-align: inherit;">在这种情况下，如果我尝试导入常规</font></font><code>CSS</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件，它将编译</font></font><code>import</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为如下</font><font style="vertical-align: inherit;">的css </font><font style="vertical-align: inherit;">语句：</font></font></p>

   <pre class="lang-css prettyprint-override"><code>/* style.scss */<font></font>
@import "../../bower_components/animate.css/animate.css";<font></font>
<font></font>
/* style.css */<font></font>
@import url(../../bower_components/animate.css/animate.css);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么，如何导入该常规css文件，以</font><font style="vertical-align: inherit;">使其在</font><font style="vertical-align: inherit;">just </font><font style="vertical-align: inherit;">语句中</font><font style="vertical-align: inherit;">具有</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编译后的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">版本</font><font style="vertical-align: inherit;">？</font></font><code>style.css</code><font style="vertical-align: inherit;"></font><code>css @import</code><font style="vertical-align: inherit;"></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3537篇《如何在sass中将.css文件导入为.scss文件？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
