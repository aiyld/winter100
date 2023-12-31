---
layout: question
title:  为什么Node.js的fs.readFile（）返回缓冲区而不是字符串？
date:   2020-03-18T07:24:22.000Z
description: 我正在尝试读取test.txt（位于Javascript源的同一文件夹中）的内容，并使用以下代码显示它：var fs = require("fs");...
img: 
author: 伽罗Tom猪猪
category: question
answer: 3
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试读取</font></font><code>test.txt</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（位于Javascript源的同一文件夹中）的内容，并使用以下代码显示它：</font></font></p>

<pre><code>var fs = require("fs");<font></font>
<font></font>
fs.readFile("test.txt", function (err, data) {<font></font>
    if (err) throw err;<font></font>
    console.log(data);<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的内容</font></font><code>test.txt</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">创建于</font></font><code>nano</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">测试Node.js readFile（）</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我得到这个：</font></font></p>

<pre><code>Nathan-Camposs-MacBook-Pro:node_test Nathan$ node main.js<font></font>
&lt;Buffer 54 65 73 74 69 6e 67 20 4e 6f 64 65 2e 6a 73 20 72 65 61 64 46 69 6c 65 28 29&gt;<font></font>
Nathan-Camposs-MacBook-Pro:node_test Nathan$ <font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2007篇《为什么Node.js的fs.readFile（）返回缓冲区而不是字符串？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Jim乐</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它返回一个Buffer对象。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果要以字符串形式输入，可以使用以下命令进行转换</font></font><code>data.toString()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>var fs = require("fs");<font></font>
<font></font>
fs.readFile("test.txt", function (err, data) {<font></font>
    if (err) throw err;<font></font>
    console.log(data.toString());<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易米亚</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从</font></font><a href="https://nodejs.org/docs/latest/api/fs.html#fs_fs_readfile_path_options_callback" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档：</font></font></a></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果未指定编码，则返回原始缓冲区。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这可能解释了</font></font><code>&lt;Buffer ...&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">指定一个有效的编码，例如</font></font><code>utf-8</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为文件名后的第二个参数。</font><font style="vertical-align: inherit;">如，</font></font></p>

<pre><code>fs.readFile("test.txt", "utf8", function(err, data) {...});
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神奇阿良Jim</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试 </font></font></p>

<pre><code>fs.readFile("test.txt", "utf8", function(err, data) {...});
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本上，您需要指定编码。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
