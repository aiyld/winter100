---
layout: question
title:  如何在Netbeans 8.0.1中使用SASS
date:   2020-03-23T02:39:26.000Z
description: 我正在尝试在Netbeans 8.0.1中使用SASS。根据ruby -v的反馈，我已经正确设置了Ruby和SASS。我有一个Web应用程序，在Pro...
img: 
author: 猴子村村
category: question
answer: 1
tags: netbeans CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试在Netbeans 8.0.1中使用SASS。</font><font style="vertical-align: inherit;">根据ruby -v的反馈，我已经正确设置了Ruby和SASS。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个Web应用程序，在Project \ Web Pages \ resources下设置了css和scss文件夹。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的输入和输出分别设置为/ scss和/ css，并且选中了“保存时编译Sass文件”。</font><font style="vertical-align: inherit;">我创建了一个styles.scss文件，并添加了一些SASS / CSS。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我保存styles.scss文件时，是否应该生成一个styles.css？</font><font style="vertical-align: inherit;">保存或编译项目时什么也没有发生。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是否有人遇到类似问题或对如何调试此问题有建议？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提前致谢！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2664篇《如何在Netbeans 8.0.1中使用SASS》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，保存文件时，应创建/更新css。</font><font style="vertical-align: inherit;">我认为您对输入/输出目录的映射错误。</font><font style="vertical-align: inherit;">路径必须相对于站点根目录/网站根目录。</font><font style="vertical-align: inherit;">我不确定您的项目是什么（HTML5或PHP或Java Web或其他？），但是如果您有Java Web项目，则路径必须为</font></font></p>

<pre><code>resources/scss -&gt; resources/css
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
