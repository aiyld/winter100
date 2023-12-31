---
layout: question
title:  Express.js中res.send和res.json之间的区别
date:   2020-03-23T11:59:40.000Z
description: 两者之间的实际区别是什么，res.send并且res.json两者似乎都执行相同的响应客户端的操作。...
img: 
author: 乐米亚
category: question
answer: 2
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">两者之间的实际区别是什么，</font></font><code>res.send</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且</font></font><code>res.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">两者似乎都执行相同的响应客户端的操作。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3006篇《Express.js中res.send和res.json之间的区别》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">查看发送的标头... </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
res.send使用content-type：text / html </font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
res.json使用content-type：application / json</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><a href="https://github.com/visionmedia/express/blob/ee228f7aea6448cf85cc052697f8d831dce785d5/lib/response.js#L174" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/visionmedia/express/blob/ee228f7aea6448cf85cc052697f8d831dce785d5/lib/response.js#L174</font></font></a></p>

<p><code>res.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最终致电</font></font><code>res.send</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但在此之前</font><font style="vertical-align: inherit;">致电</font><font style="vertical-align: inherit;">：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尊重</font></font><code>json spaces</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>json replacer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">应用设置</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保响应将具有utf8字符集和application / json内容类型</font></font></li>
</ul></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
