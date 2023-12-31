---
layout: question
title:  如何使用节点的fs.mkdirSync创建完整路径？
date:   2020-04-03T02:35:02.000Z
description: 我正在尝试创建完整路径（如果不存在）。代码如下：var fs = require('fs');if (\!fs.existsSync(newDes...
img: 
author: Near达蒙
category: question
answer: 4
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试创建完整路径（如果不存在）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码如下：</font></font></p>

<pre><code>var fs = require('fs');<font></font>
if (!fs.existsSync(newDest)) fs.mkdirSync(newDest); <font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只要只有一个子目录（例如“ dir1”之类的newDest），此代码就可以很好地工作，但是当存在一个目录路径（“ dir1 / dir2”）时，它将失败并显示 
 </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">错误：ENOENT，没有这样的文件或目录</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我希望能够用最少的代码行来创建完整路径。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我读到fs上有一个递归选项，并像这样尝试过</font></font></p>

<pre><code>var fs = require('fs');<font></font>
if (!fs.existsSync(newDest)) fs.mkdirSync(newDest,'0777', true);<font></font>
</code></pre>

<p>I feel like it should be that simple to recursively create a directory that doesn't exist. Am I missing something or do I need to parse the path and check each directory and create it if it doesn't already exist?</p>

<p>I'm pretty new to Node. Maybe I'm using an old version of FS?</p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3894篇《如何使用节点的fs.mkdirSync创建完整路径？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Itachi</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以简单地递归检查路径中是否存在文件夹，并在检查文件夹是否不存在时对其进行设置。</font><font style="vertical-align: inherit;">（</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有外部图书馆</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>

<pre><code>function checkAndCreateDestinationPath (fileDestination) {<font></font>
    const dirPath = fileDestination.split('/');<font></font>
    dirPath.forEach((element, index) =&gt; {<font></font>
        if(!fs.existsSync(dirPath.slice(0, index + 1).join('/'))){<font></font>
            fs.mkdirSync(dirPath.slice(0, index + 1).join('/')); <font></font>
        }<font></font>
    });<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Gil</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在</font></font><code>10.12.0</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font><a href="https://nodejs.org/api/fs.html#fs_fs_mkdirsync_path_options" rel="nofollow noreferrer"><font style="vertical-align: inherit;">NodeJS</font></a><font style="vertical-align: inherit;"> &gt; = </font><font style="vertical-align: inherit;">，您可以使用</font></font><code>fs.mkdirSync(path, { recursive: true })</code> <a href="https://nodejs.org/api/fs.html#fs_fs_mkdirsync_path_options" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">fs.mkdirSync</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此功能已在10.12.0版中添加到node.js中，因此就像将选项</font></font><code>{recursive: true}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为第二个参数传递给</font></font><code>fs.mkdir()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">调用一样简单。</font><font style="vertical-align: inherit;">请参阅</font></font><a href="https://nodejs.org/api/fs.html#fs_fs_mkdir_path_options_callback" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">官方文档中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font><a href="https://nodejs.org/api/fs.html#fs_fs_mkdir_path_options_callback" rel="noreferrer"><font style="vertical-align: inherit;">示例</font></a><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需外部模块或您自己的实现。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">fs-extra添加了本机fs模块中未包含的文件系统方法。</font><font style="vertical-align: inherit;">它代替了fs。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装 </font></font><code>fs-extra</code></p>

<p><code>$ npm install --save fs-extra</code></p>

<pre><code>const fs = require("fs-extra");<font></font>
// Make sure the output directory is there.<font></font>
fs.ensureDirSync(newDest);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有同步和异步选项。</font></font></p>

<p><a href="https://github.com/jprichardson/node-fs-extra/blob/master/docs/ensureDir.md" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/jprichardson/node-fs-extra/blob/master/docs/ensureDir.md</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
