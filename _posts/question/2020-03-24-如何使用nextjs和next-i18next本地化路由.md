---
layout: question
title:  如何使用next.js和next-i18next本地化路由？
date:   2020-03-24T06:35:20.000Z
description: 更改语言时，我需要更改路线的名称。例如，我有一条路线，/en/career但是当我改用捷克语时，我需要一条路线/cs/kariera。基本上，我需要将UR...
img: 
author: 十三西门
category: question
answer: 0
tags: next.js React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更改语言时，我需要更改路线的名称。</font><font style="vertical-align: inherit;">例如，我有一条路线，</font></font><code>/en/career</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是当我改用捷克语时，我需要一条路线</font></font><code>/cs/kariera</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">基本上，我需要将URL本地化。</font><font style="vertical-align: inherit;">现在，当我打开</font></font><code>/en/career</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并将语言更改为CS时，我得到了</font></font><code>/cs/career</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">该页面根本不应该存在，当我在服务器上呈现该页面时，我正确地得到了404。我可以使用next-i18next软件包执行类似的操作吗？</font><font style="vertical-align: inherit;">如果是这样，怎么办？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我发现这个程序包</font></font><a href="https://github.com/vonschau/next-routes-with-locale" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/vonschau/next-routes-with-locale</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能完全符合我的需求，但是显然不再维护了，并且在next.js 8下不起作用。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3385篇《如何使用next.js和next-i18next本地化路由？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
