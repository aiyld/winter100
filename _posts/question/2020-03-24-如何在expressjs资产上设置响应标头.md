---
layout: question
title:  如何在express.js资产上设置响应标头
date:   2020-03-24T11:08:03.000Z
description: 我需要将CORS设置为在express服务的脚本上启用。如何在这些返回的公共/资产响应中设置标题？...
img: 
author: Gil伽罗小宇宙
category: question
answer: 2
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我需要将CORS设置为在express服务的脚本上启用。</font><font style="vertical-align: inherit;">如何在这些返回的公共/资产响应中设置标题？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3707篇《如何在express.js资产上设置响应标头》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony凯</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm上至少有一个中间件用于处理Express中的CORS：</font></font><a href="https://github.com/troygoode/node-cors" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">cors</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简短答案：</font></font></strong> </p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">res.setHeaders-</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">调用本地Node方法</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">res.set-</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">设置标题</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">res.headers</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> - </font><strong><font style="vertical-align: inherit;">res.set</font></strong><font style="vertical-align: inherit;">的别名</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
