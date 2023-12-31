---
layout: question
title:  在Node.js中加载基本HTML
date:   2020-03-23T07:21:53.000Z
description: 我正在尝试找出如何加载和呈现基本HTML文件的方法，因此不必编写类似以下的代码：response.write('...<p>blahblahblah<...
img: 
author: 小宇宙Itachi
category: question
answer: 1
tags: html Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试找出如何加载和呈现基本HTML文件的方法，因此不必编写类似以下的代码：</font></font></p>

<pre><code>response.write('...&lt;p&gt;blahblahblah&lt;/p&gt;...');
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2904篇《在Node.js中加载基本HTML》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐米亚</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我知道这是一个古老的问题，但是由于没有人提到它，所以我认为值得添加：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您确实想提供静态内容（例如“关于”页面，图像，css等），则可以使用静态内容提供模块之一，例如node-static。</font><font style="vertical-align: inherit;">（还有其他可能更好/更糟的方法-尝试search.npmjs.org。）通过一点点预处理，您就可以从静态过滤动态页面并将其发送到正确的请求处理程序。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
