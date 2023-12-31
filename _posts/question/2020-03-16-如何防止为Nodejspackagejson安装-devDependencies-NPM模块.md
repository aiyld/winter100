---
layout: question
title:  如何防止为Node.js（package.json）安装“ devDependencies” NPM模块？
date:   2020-03-16T06:38:39.000Z
description: 我的package.json文件中有此文件（简化版）：{  "name"  "a-module",  "version"  "0.0.1",  ...
img: 
author: JimLEYHarry
category: question
answer: 13
tags: Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的package.json文件中有此文件（简化版）：</font></font></p>

<pre><code>{<font></font>
  "name": "a-module",<font></font>
  "version": "0.0.1",<font></font>
  "dependencies": {<font></font>
    "coffee-script":      "&gt;= 1.1.3"<font></font>
  },<font></font>
  "devDependencies": {<font></font>
    "stylus":             "&gt;= 0.17.0"<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在Mac 10.6.8上使用NPM 1.1.1版本。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我从项目根目录运行以下命令时，它将同时安装</font></font><code>dependencies</code> <em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font></em> <code>devDependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>npm install
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我觉得这个命令安装了</font></font><code>devDependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>npm install --dev
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我如何做到</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只安装</font></font><code>dependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（这样生产环境只获取那些模块），而同时</font></font><code>npm install --dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装</font></font><code>dependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>devDependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">呢？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1763篇《如何防止为Node.js（package.json）安装“ devDependencies” NPM模块？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅A飞云</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，如果您的package-lock.json和npm 5+一起出现了问题。</font><font style="vertical-align: inherit;">您必须先删除它，然后才能使用</font></font><code>npm install --production</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomStafan</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><pre><code>npm install --dev will install dev dependencies
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且，根据仅安装依赖项的问题，以下命令将有所帮助</font></font></p>

<pre><code>npm install --prod will install dependencies
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva阳光</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">需要添加到选择的答案：到目前为止，</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在软件包目录中（包含</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）将安装devDependencies，而</font></font><code>npm install -g</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不会安装它们。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋伽罗猿</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><code>npm install --production</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是安装生产所需的节点模块的正确方法。</font><font style="vertical-align: inherit;">查看文档以获取更多详细信息</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长逆天</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>npm install packageName --save</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将增加包</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的依赖关系</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，如果你用</font></font><code>npm install packageName --save-dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么它</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">devDependencies</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><code>npm install packageName --save-dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">应该用于添加软件包以用于开发目的。</font><font style="vertical-align: inherit;">就像添加TDD包（Chai，mocha等）一样。</font><font style="vertical-align: inherit;">用于开发而不用于生产。  </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神乐神无</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">值得一提的是，您可以使用</font></font><code>NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">环境变量来达到相同的结果。</font><font style="vertical-align: inherit;">如果要对Node应用程序（例如Docker）进行容器化，则特别有用。</font></font></p>

<pre class="lang-sh prettyprint-override"><code>NODE_ENV=production npm install
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上面的代码将安装除dev以外的所有依赖项（即</font></font><code>devDependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您需要使用环境变量，</font></font><code>Dockerfile</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以在</font></font><a href="https://docs.docker.com/engine/reference/builder/#environment-replacement" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">找到更多信息</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">环境变量很容易在需要时被覆盖（例如，如果要在Travis CI上运行测试套件）。</font><font style="vertical-align: inherit;">如果是这种情况，您可以执行以下操作：</font></font></p>

<pre class="lang-sh prettyprint-override"><code>docker run -v $(pwd):/usr/src/app --rm -it -e NODE_ENV=production node:8 npm install
</code></pre>

<p><a href="https://docs.npmjs.com/misc/config#production" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NPM文档在这里</font></font></a></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生产</font></font></p>
  
  <ul>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">默认值：false</font></font></li>
  <li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">类型：布尔值设置为true以在“生产”模式下运行。</font></font></p>
  
  <ol>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在运行不带任何参数的本地npm install时，不会在最高级别安装devDependencies。</font></font></li>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为生命周期脚本设置NODE_ENV =“ production”。</font></font></li>
  </ol></li>
  </ul>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快乐的集装箱化</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">=）</font></font></strong></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LJinJin</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从软件包内部安装时（如果</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当前目录中</font><font style="vertical-align: inherit;">有一个）</font><font style="vertical-align: inherit;">，</font><font style="vertical-align: inherit;">npm将安装dev依赖项</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果它来自另一个位置（npm注册表，git repo，文件系统上的其他位置），则仅安装依赖项。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞LSam</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您已经安装了所有依赖项，并且希望避免再次从NPM下载生产软件包，则只​​需键入：</font></font></p>

<pre><code>npm prune --production
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将从您的</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹中</font><font style="vertical-align: inherit;">删除您的开发依赖项</font><font style="vertical-align: inherit;">，这在您尝试自动执行两步过程（例如，</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用开发依赖项对我的项目进行Webpack</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅使用生产模块构建Docker映像</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"></font><code>npm prune</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在两者之间</font><font style="vertical-align: inherit;">运行</font><font style="vertical-align: inherit;">将使您不必重新安装所有内容！</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村凯</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用“ npm install”时，模块将被加载并在整个应用程序中可用，无论它们是“ devDependencies”还是“ dependencies”。</font><font style="vertical-align: inherit;">这个想法的总和：package.json定义为依赖项（任何类型）的所有内容都将安装到node_modules。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">依赖项/ devDependencies / optionalDependencies之间的区别的目的是代码的使用者可以使用npm来安装这些资源。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据文档：</font></font><a href="https://npmjs.org/doc/json.html"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> : </font><a href="https://npmjs.org/doc/json.html"><font style="vertical-align: inherit;">//npmjs.org/doc/json.html</font></a><font style="vertical-align: inherit;"> ...</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果有人计划在其程序中下载和使用您的模块，那么他们可能不希望或不需要下载并构建您使用的外部测试或文档框架。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这种情况下，最好在devDependencies哈希中列出这些其他项。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只要设置了--dev配置标志，这些东西就会被安装。</font><font style="vertical-align: inherit;">当执行npm link或从软件包的根目录进行npm install时，此标志会自动设置，并且可以像其他npm配置参数一样进行管理。</font><font style="vertical-align: inherit;">有关该主题的更多信息，请参见config（1）。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，要解决此问题，如果只想使用npm安装“依赖项”，则以下命令是：</font></font></p>

<pre><code>npm install --production
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这可以通过查看添加了此过滤器的Git提交来确认（以及其他一些提供此功能的过滤器[在下面列出]）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm可以使用的替代过滤器：</font></font></p>

<pre><code>--save          =&gt; updates dependencies entries in the {{{json}}} file<font></font>
--force         =&gt; force fetching remote entries if they exist on disk <font></font>
--force-latest  =&gt; force latest version on conflict<font></font>
--production    =&gt; do NOT install project devDependencies<font></font>
--no-color      =&gt; do not print colors<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@dmarr尝试使用npm install --production</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Jim老丝猪猪</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我也遇到了这个问题！</font><font style="vertical-align: inherit;">npm install有点令人困惑，Web帖子不断引入-d /-dev标志，就好像有一个明确的“开发”安装模式一样。</font></font></p>

<ul>
<li><p><strong><code>npm install</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将同时安装“ </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">dependencies</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ”和“ </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">devDependencies</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ”</font></font></p></li>
<li><p><strong><code>npm install --production</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将只安装“ </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">依赖项</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ”</font></font></p></li>
<li><p><strong><code>npm install --dev</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将只安装“ </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">devDependencies</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ”</font></font></p></li>
</ul></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁小宇宙猿</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新选项是：</font></font></p>

<pre><code>npm install --only=prod
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您只想安装devDependencies：</font></font></p>

<pre><code>npm install --only=dev
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门神奇</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当在开发环境（默认）中的软件包目录中运行时，</font><font style="vertical-align: inherit;">该</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令将与</font></font><code>devDependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其他</font><font style="vertical-align: inherit;">命令</font><font style="vertical-align: inherit;">一起</font><font style="vertical-align: inherit;">安装</font></font><code>dependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>npm install --only=prod</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（或</font></font><code>--only=production</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅</font></font></strong> <font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装</font></font><code>dependencies</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，而不</font></font><code>devDependencies,</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">考虑</font></font><code>NODE_ENV</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">环境变量</font><font style="vertical-align: inherit;">的值</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">资料来源：</font></font><a href="https://docs.npmjs.com/cli/install" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm docs</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在npm（2015-08-13）v3.3.0之前，该选项称为</font></font><code>--production</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，即</font></font><code>npm install --production</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一斯丁</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您在2016年阅读了此POST，请通过使用实现您想要的</font></font></p>

<pre><code>--only={prod[uction]|dev[elopment]} 
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参数将导致仅安装devDependencies或仅安装非devDependencies，而与NODE_ENV无关。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来自：</font><a href="https://docs.npmjs.com/cli/install" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://docs.npmjs.com/cli/install" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//docs.npmjs.com/cli/install</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
