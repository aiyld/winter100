---
layout: question
title:  在Windows 8.1中用gem安装sass的错误
date:   2020-03-24T10:15:24.000Z
description: 我正在Windows 8.1 Pro中安装rubyruby 2.1.3p242 (2014-09-19 revision 47630) \[x64-mi...
img: 
author: 村村
category: question
answer: 2
tags: 红宝石 CSS
topic: CSS
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在Windows 8.1 Pro中安装ruby</font></font></p>

<pre><code>ruby 2.1.3p242 (2014-09-19 revision 47630) [x64-mingw32]
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和宝石版</font></font></p>

<pre><code>2.2.2
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在执行gem安装时抛出此错误：</font></font></p>

<pre><code>ERROR:  Loading command: install (ArgumentError)<font></font>
        unknown encoding name - CP720<font></font>
ERROR:  While executing gem ... (NoMethodError)<font></font>
    undefined method `invoke_with_build_args' for nil:NilClass<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3635篇《在Windows 8.1中用gem安装sass的错误》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy路易</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此命令将修复它-您需要更改当前终端的代码页。</font></font></p>

<pre><code>chcp 1252
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试卸载ruby并重新安装以前的版本。</font><font style="vertical-align: inherit;">曾经为我工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一个解决方案是在cmd中键入：      </font></font><code>set = HTTP_proxy http://10.1.143.126:3128</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">     然后重试</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不要忘记以管理员身份运行cmd。 </font></font></li>
</ul></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
