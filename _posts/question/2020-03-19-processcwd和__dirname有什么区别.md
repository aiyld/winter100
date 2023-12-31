---
layout: question
title:  process.cwd（）和__dirname有什么区别？
date:   2020-03-19T03:07:07.000Z
description: 之间有什么区别console.log(process.cwd())和console.log(__dirname);我已经看到两者都用在...
img: 
author: 古一Mandy
category: question
answer: 3
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之间有什么区别</font></font></p>

<pre><code>console.log(process.cwd())
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font></p>

<pre><code>console.log(__dirname);
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经看到两者都用在相似的上下文中。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2282篇《process.cwd（）和__dirname有什么区别？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无达蒙JinJin</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">了解</font><font style="vertical-align: inherit;">每个</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">范围</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以使事情更容易记住。</font></font></p>

<p><strong><code>process</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的全局对象，并</font></font><strong><code>.cwd()</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">返回运行节点的位置。</font></font></p>

<p><strong><code>__dirname</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是</font></font><code>module</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的属性，代表模块的文件路径。</font><font style="vertical-align: inherit;">在节点中，一个模块驻留在一个文件中。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同样，</font></font><strong><code>__filename</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是another </font></font><code>module</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的属性，其中包含模块的文件名。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐米亚</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ </font></font><code>find proj</code></p>

<pre><code>proj<font></font>
proj/src<font></font>
proj/src/index.js<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ </font></font><code>cat proj/src/index.js</code></p>

<pre><code>console.log("process.cwd() = " + process.cwd());<font></font>
console.log("__dirname = " + __dirname);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ </font></font><code>cd proj; node src/index.js</code></p>

<pre><code>process.cwd() = /tmp/proj<font></font>
__dirname = /tmp/proj/src<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Harry古一</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><a href="https://nodejs.org/docs/latest/api/process.html#process_process_cwd" rel="noreferrer"><code>process.cwd()</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 返回当前工作目录，</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">即您从中调用</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令</font><font style="vertical-align: inherit;">的目录</font><font style="vertical-align: inherit;">。</font></font></p>

<p><a href="https://nodejs.org/docs/latest/api/globals.html#globals_dirname" rel="noreferrer"><code>__dirname</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 返回包含JavaScript源代码文件的目录的目录名称</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
