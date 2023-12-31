---
layout: question
title:  如何在package.json中指定所需的Node.js版本？
date:   2020-03-23T02:33:52.000Z
description: 我有一个需要节点版本12或更高版本的Node.js项目。有没有办法在packages.json文件中指定此名称，以便安装程序将自动检查并通知用户是否需要升...
img: 
author: 神乐
category: question
answer: 4
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个需要节点版本12或更高版本的Node.js项目。</font><font style="vertical-align: inherit;">有没有办法在packages.json文件中指定此名称，以便安装程序将自动检查并通知用户是否需要升级？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2658篇《如何在package.json中指定所需的Node.js版本？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝Jim猴子</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还有另一种更简单的方法：</font></font></p>

<ol>
<li><code>npm install Node@8</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> （将Node 8保存为package.json中的依赖项）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您的应用程序将使用Node 8面向</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">任何人</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行</font><font style="vertical-align: inherit;">-即使是Yarn用户！</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之所以有效，</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是</font><font style="vertical-align: inherit;">因为</font><font style="vertical-align: inherit;">它只是一个将节点作为其二进制程序包提供的程序包。</font><font style="vertical-align: inherit;">它仅包含为node_module / .bin，这意味着它仅使节点可用于程序包脚本。</font><font style="vertical-align: inherit;">不是主壳。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在此处查看Twitter上的讨论：</font><a href="https://twitter.com/housecor/status/962347301456015360" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;">：</font></font><a href="https://twitter.com/housecor/status/962347301456015360" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//twitter.com/housecor/status/962347301456015360</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猴子</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">至 </font></font><code>package.json</code></p>

<pre><code>  "engines": {<font></font>
    "node": "&gt;=10.0.0",<font></font>
    "npm": "&gt;=6.0.0"<font></font>
  },<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到文件</font></font><code>.npmrc</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（靠近</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，相同目录）</font></font></p>

<pre><code>engine-strict=true
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为您可以使用“引擎”字段：</font></font></p>

<pre><code>{ "engines" : { "node" : "&gt;=0.12" } }
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正如您所说的那样，您的代码绝对不能与任何较低版本一起使用，您可能也希望“ engineStrict”标志：</font></font></p>

<pre><code>{ "engineStrict" : true }
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可</font><a href="https://docs.npmjs.com/files/package.json#engines" rel="noreferrer"><font style="vertical-align: inherit;">在npmjs网站上</font></a><font style="vertical-align: inherit;">找到package.json文件的文档</font></font><a href="https://docs.npmjs.com/files/package.json#engines" rel="noreferrer"><font style="vertical-align: inherit;"></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新资料</font></font></strong></p>

<p><code>engineStrict</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在已弃用，因此只会发出警告。</font><font style="vertical-align: inherit;">现在，取决于用户</font></font><code>npm config set engine-strict true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是否愿意</font><font style="vertical-align: inherit;">运行</font><font style="vertical-align: inherit;">它。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新2</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如下所述，</font><font style="vertical-align: inherit;">在Node的版本不兼容的</font><font style="vertical-align: inherit;">情况下，</font></font><code>.npmrc</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在项目的根目录（与package.json文件处于同一级别）</font><font style="vertical-align: inherit;">创建</font><font style="vertical-align: inherit;">文件</font></font><code>engine-strict=true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将在安装过程中产生错误。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tom凯</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><strong><code>.nvmrc</code></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您可能正在</font></font><a href="https://askubuntu.com/questions/594656/how-to-install-the-latest-versions-of-nodejs-and-npm/971612#971612"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用这样的NVM</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则可以在git跟踪的</font></font><code>.nvmrc</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件中</font><font style="vertical-align: inherit;">指示给定项目所需的nodejs版本</font><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>echo v10.15.1 &gt; .nvmrc
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这不会自动对生效</font></font><code>cd</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这是理智的：用户然后必须执行以下操作：</font></font></p>

<pre><code>nvm use
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在该节点版本将用于当前shell。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以列出拥有的节点的版本：</font></font></p>

<pre><code>nvm list
</code></pre>

<p><code>.nvmrc</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">记录在：</font><a href="https://github.com/creationix/nvm/tree/02997b0753f66c9790c6016ed022ed2072c22603#nvmrc" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/creationix/nvm/tree/02997b0753f66c9790c6016ed022ed2072c22603#nvmrc" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/creationix/nvm/tree/02997b0753f66c9790c6016ed022ed2072c22603#nvmrc</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在以下</font></font><code>cd</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">位置询问</font><font style="vertical-align: inherit;">如何自动选择该节点版本</font><font style="vertical-align: inherit;">：</font></font><a href="https://stackoverflow.com/questions/29653036/automatically-switch-to-correct-version-of-node-based-on-project"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据项目自动切换到正确的Node版本</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用NVM 0.33.11测试。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
