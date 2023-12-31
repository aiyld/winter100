---
layout: question
title:  为什么“ npm install”会重写package-lock.json？
date:   2020-03-16T06:37:58.000Z
description: 我最近才升级到npm \` 5。我现在有一个package-lock.json文件，其中包含package.json中的所有内容。我希望，当我运行npm i...
img: 
author: 小宇宙斯丁宝儿
category: question
answer: 8
tags: Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我最近才升级到npm @ 5。</font><font style="vertical-align: inherit;">我现在有一个package-lock.json文件，其中包含package.json中的所有内容。</font><font style="vertical-align: inherit;">我希望，当我运行</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该依赖项版本时，会将其从锁定文件中拉出，以确定应该在我的node_modules目录中安装什么。</font><font style="vertical-align: inherit;">奇怪的是，它实际上最终修改并重写了package-lock.json文件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，锁定文件的TypeScript指定为版本2.1.6。</font><font style="vertical-align: inherit;">然后，在</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令之后，版本更改为2.4.1。</font><font style="vertical-align: inherit;">这似乎破坏了锁定文件的全部目的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想念什么？</font><font style="vertical-align: inherit;">如何让npm真正尊重我的锁定文件？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1762篇《为什么“ npm install”会重写package-lock.json？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猿阳光</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在他们的github页面上有一个未解决的问题：</font><a href="https://github.com/npm/npm/issues/18712" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/npm/npm/issues/18712" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/npm/npm/issues/18712</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当开发人员使用不同的操作系统时，此问题最严重。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LEY老丝樱</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑：名称“锁”是一个棘手的人，其NPM试图赶上纱线。</font><font style="vertical-align: inherit;">它不是一个锁定的文件。</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是用户固定的文件，“安装”后将生成node_modules文件夹树，然后将该树写入</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">因此，您将看到相反的结果-依赖关系版本将</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一如既往地</font><font style="vertical-align: inherit;">被删除</font><font style="vertical-align: inherit;">，</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">应调用</font></font><code>package-tree.json</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（希望经过这么多次否决后，我的回答才能更加清晰）</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个简单的答案：</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">像往常一样保持依赖关系，而这</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是“一个精确的，更重要的是可重现的node_modules树”（取自</font></font><a href="https://docs.npmjs.com/files/package-locks" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm docs本身</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">至于棘手的名称，其NPM试图赶上Yarn。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Stafan</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">看来此问题已在npm v5.4.2中修复</font></font></p>

<p><a href="https://github.com/npm/npm/issues/17979" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/npm/npm/issues/17979</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（向下滚动到线程中的最后一条注释）</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新资料</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实际在5.6.0中已修复。</font><font style="vertical-align: inherit;">5.4.2中存在一个跨平台错误，导致该问题仍然存在。</font></font></p>

<p><a href="https://github.com/npm/npm/issues/18712" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/npm/npm/issues/18712</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新2</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里看到我的答案：</font><a href="https://stackoverflow.com/a/53680257/1611058"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> :
 </font></font><a href="https://stackoverflow.com/a/53680257/1611058"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//stackoverflow.com/a/53680257/1611058</font></font></a></p>

<p><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 是现在安装现有项目时应使用的命令。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Stafan</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令代替</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“ ci”代表“持续集成”。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它将基于package-lock.json文件而不是宽松的package.json文件依赖项安装项目依赖项。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它会为您的队友生成相同的版本，并且速度也更快。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以在此博客文章中阅读有关此内容的更多信息：</font><a href="https://blog.npmjs.org/post/171556855892/introducing-npm-ci-for-faster-more-reliable" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> :
 </font></font><a href="https://blog.npmjs.org/post/171556855892/introducing-npm-ci-for-faster-more-reliable" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//blog.npmjs.org/post/171556855892/introducing-npm-ci-for-faster-more-reliable</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无LEYMandy</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将来，您将能够使用</font></font><code>--from-lock-file</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（或类似的）标志</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅从</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行安装</font><font style="vertical-align: inherit;">，而</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需对其进行修改。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这对于CI等可重现构建很重要的环境很有用。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请参阅</font></font><a href="https://github.com/npm/npm/issues/18286" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/npm/npm/issues/18286</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以跟踪功能。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长小哥理查德</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用新推出的</font></font></p>

<pre><code>npm ci
</code></pre>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm ci承诺将为大型团队带来最大的利益。</font><font style="vertical-align: inherit;">使开发人员能够“退出”软件包锁定功能可以促进大型团队之间更有效的协作，并且完全安装锁定文件中的内容的功能可以每月节省数十甚至数百个开发人员的时间，从而释放团队花更多的时间来建造和运送令人惊奇的东西。</font></font></p>
</blockquote>

<p><a href="https://blog.npmjs.org/post/171556855892/introducing-npm-ci-for-faster-more-reliable" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引入</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更快，更可靠的构建</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Harry小小</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我发现将会有一个新版本的npm </font></font><a href="https://github.com/npm/npm/releases/tag/v5.7.1" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">5.7.1</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和新命令</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它将</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅从</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新的npm ci命令仅从锁定文件安装。</font><font style="vertical-align: inherit;">如果您的package.json和锁定文件不同步，则它将报告错误。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它可以通过丢弃您的node_modules并从头开始创建它来工作。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">除了保证您仅获得锁定文件中的内容外，如果不使用node_modules进行启动，它也比npm install快得多（2x-10x！）。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可能会从名称中得知，我们希望它对持续集成环境大有裨益。</font><font style="vertical-align: inherit;">我们还希望从git标签进行生产部署的人们会从中受益匪浅。</font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙小卤蛋Tom</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简短答案：</font></font></strong></p>

<ul>
<li><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 仅当满足package.json的要求时，才尊重package-lock.json。 </font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果不满足这些要求，则更新软件包并覆盖软件包锁定。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您宁愿使构建失败，也不愿在发生这种情况时重写package-lock，请使用</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
</ul>

<hr>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个可以解释问题的方案（已通过NPM 6.3.0验证）</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您在package.json中声明一个依赖项，例如：</font></font></p>

<pre><code>"depA": "^1.0.0"
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您将执行以下操作，</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将生成一个package-lock.json：</font></font></p>

<pre><code>"depA": "1.0.0"
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">几天后，发布了较新的次要版本“ depA”，如“ 1.1.0”，则以下内容成立：</font></font></p>

<pre><code>npm ci       # respects only package-lock.json and installs 1.0.0<font></font>
<font></font>
npm install  # also, respects the package-lock version and keeps 1.0.0 installed <font></font>
             # (i.e. when package-lock.json exists, it overrules package.json)<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">接下来，您手动将package.json更新为：</font></font></p>

<pre><code>"depA": "^1.1.0"
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后重新运行：</font></font></p>

<pre><code>npm ci      # will try to honor package-lock which says 1.0.0<font></font>
            # but that does not satisfy package.json requirement of "^1.1.0" <font></font>
            # so it would throw an error <font></font>
<font></font>
npm install # installs "1.1.0" (as required by the updated package.json)<font></font>
            # also rewrites package-lock.json version to "1.1.0"<font></font>
            # (i.e. when package.json is modified, it overrules the package-lock.json)<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
