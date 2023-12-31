---
layout: question
title:  是否提交由npm 5创建的package-lock.json文件？
date:   2020-03-13T08:08:19.000Z
description: npm 5今天发布，其中一项新功能包括确定性安装和package-lock.json文件创建。该文件应该保留在源代码管理中吗？我假设它类似于yar...
img: 
author: 
category: question
answer: 7
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><a href="http://blog.npmjs.org/post/161081169345/v500" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm 5今天发布</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，其中一项新功能包括确定性安装和</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件</font><font style="vertical-align: inherit;">创建</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该文件应该保留在源代码管理中吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我假设它类似于</font></font><a href="https://stackoverflow.com/questions/39990017/should-i-commit-the-yarn-lock-file-and-what-is-it-for"><code>yarn.lock</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://stackoverflow.com/questions/12896780/should-composer-lock-be-committed-to-version-control"><code>composer.lock</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这两个都应该保留在源代码管理中。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1434篇《是否提交由npm 5创建的package-lock.json文件？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猿阳光</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">全局禁用package-lock.json</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在终端中输入以下内容：</font></font></p>

<pre><code>npm config set package-lock false
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这真的像魔术一样对我有用</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小仲羽</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，您可以提交此文件。</font><font style="vertical-align: inherit;">来自</font></font><a href="https://docs.npmjs.com/files/package-lock.json" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm的官方文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">会为</font></font><code>npm</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">修改</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">树或的</font><font style="vertical-align: inherit;">任何操作自动生成</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它描述了生成的确切树，因此无论中间依赖项更新如何，后续安装都可以生成相同的树。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该文件旨在提交到源存储库中。</font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门JinJin</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不在项目中提交此文件。</font><font style="vertical-align: inherit;">重点是什么 ？</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它产生了</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是使用gitlab-ci.yml构建的gitlab中SHA1代码完整性错误的原因</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管的确我从来没有在package.json的lib中使用^，因为我对此有不好的经验。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德十三Davaid</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的你应该：</font></font></p>

<ol>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提交</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></strong></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不是</font></font><code>npm install</code></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在CI和本地开发计算机上构建应用程序时</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">工作流程</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">需要</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的存在</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令的</font><font style="vertical-align: inherit;">一个很大的缺点</font><font style="vertical-align: inherit;">是它的意外行为，它可能会使突变</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，而</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅使用锁定文件中指定的版本并产生错误</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不同步</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">缺少a。</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，在</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本地</font><font style="vertical-align: inherit;">运行</font><font style="vertical-align: inherit;">，尤其是。</font><font style="vertical-align: inherit;">在具有多个开发人员的大型团队中，可能会导致内的许多冲突，</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而开发人员决定完全删除该</font><font style="vertical-align: inherit;">冲突</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，有一个强大的用例可以信任项目的依赖项在不同机器上以可靠的方式重复解决。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从中</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以确切地得到：一个已知的工作状态。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">过去，我有没有</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">/ </font></font><code>npm-shrinkwrap.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">/ </font></font><code>yarn.lock</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件的</font><font style="vertical-align: inherit;">项目，</font><font style="vertical-align: inherit;">由于随机依赖项的最新更新，其构建将有一天失败。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这些问题很难解决，因为您有时不得不猜测上一个工作版本是什么。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果要添加新的依赖项，则仍然可以运行</font></font><code>npm install {dependency}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果要升级，请使用</font></font><code>npm update {dependency}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>npm install ${dependendency}@{version}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并提交更改的</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果升级失败，则可以恢复到上一个​​已知的工作状态</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要</font></font><a href="https://docs.npmjs.com/files/package-locks" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引用文档NPM</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p>It is highly recommended you commit the generated package lock to
  source control: this will allow anyone else on your team, your
  deployments, your CI/continuous integration, and anyone else who runs
  npm install in your package source to get the exact same dependency
  tree that you were developing on. Additionally, the diffs from these
  changes are human-readable and will inform you of any changes npm has
  made to your node_modules, so you can notice if any transitive
  dependencies were updated, hoisted, etc.</p>
</blockquote>

<p>And in regards to the <a href="https://docs.npmjs.com/cli/ci" rel="noreferrer">difference between <code>npm ci</code> vs <code>npm install</code></a>:</p>

<blockquote>
  <ul>
  <li>The project must have an existing package-lock.json or    npm-shrinkwrap.json.</li>
  <li>If dependencies in the package lock do not match    those in package.json, <code>npm ci</code> will exit with an error, instead of    updating
  the package lock. </li>
  <li><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 一次只能安装整个项目：不能使用此命令添加单个依赖项。</font></font></li>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">已经存在，它将在</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">开始安装</font><font style="vertical-align: inherit;">之前自动删除</font><font style="vertical-align: inherit;">。</font></font></li>
  <li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它将永远不会写入</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或执行任何软件包锁：安装实际上是冻结的。</font></font></li>
  </ul>
</blockquote>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：我在</font><a href="https://stackoverflow.com/a/48524475/457268"><font style="vertical-align: inherit;">这里</font></a><font style="vertical-align: inherit;">发布了类似的答案</font></font><a href="https://stackoverflow.com/a/48524475/457268"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">逆天小卤蛋Green</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，最佳做法是办理登机手续（是，请办理登机手续）</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我同意在看到差异时会引起很多噪音或冲突。</font><font style="vertical-align: inherit;">但是好处是：</font></font></p>

<ol>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">保证每个软件包的版本完全相同</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">在不同时间，不同环境中构建时，此部分最重要。</font><font style="vertical-align: inherit;">您可以</font></font><code>^1.2.3</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在中</font><font style="vertical-align: inherit;">使用</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是</font><font style="vertical-align: inherit;">您</font><font style="vertical-align: inherit;">如何确保每次</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">都能在开发机和构建服务器中使用相同的版本，尤其是那些间接依赖包？</font><font style="vertical-align: inherit;">好吧，</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将确保这一点。</font><font style="vertical-align: inherit;">（借助</font></font><code>npm ci</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它可以基于锁定文件安装软件包）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它改善了安装过程。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它有助于新的审核功能</font></font><code>npm audit fix</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（我认为审核功能来自npm版本6）。</font></font></li>
</ol></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">伽罗理查德</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，它打算被签入。我想建议它获得自己的唯一提交。</font><font style="vertical-align: inherit;">我们发现它为我们的差异增加了很多噪音。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LEYStafan</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">旨在被检查到源代码管理中。</font><font style="vertical-align: inherit;">如果您使用的是npm 5，则可能会在命令行上看到：</font></font><code>created a lockfile as package-lock.json. You should commit this file.</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据</font></font><a href="https://github.com/npm/npm/blob/v5.0.0/doc/files/package-lock.json.md" rel="noreferrer"><code>npm help package-lock.json</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">会为npm修改</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">树或的</font><font style="vertical-align: inherit;">任何操作自动生成</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它描述了生成的确切树，因此无论中间依赖项更新如何，后续安装都可以生成相同的树。</font></font></p>
  
  <p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该文件旨在提交到源存储库中</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并具有多种用途：</font></font></p>
  
  <ul>
  <li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">描述一个依赖关系树的单一表示，这样可以确保队友，部署和持续集成安装完全相同的依赖关系。</font></font></p></li>
  <li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为用户提供一种工具，使其可以“时间旅行”到以前的状态，</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不必提交目录本身。</font></font></p></li>
  <li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了通过可读的源代码控制差异更好地了解树的变化。</font></font></p></li>
  <li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并允许npm跳过以前安装的软件包的重复元数据解析，从而优化安装过程。</font></font></p></li>
  </ul>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关于</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它的</font><font style="vertical-align: inherit;">一个关键细节</font><font style="vertical-align: inherit;">是它无法发布，并且如果在顶级软件包之外的任何地方找到它，它将被忽略。</font><font style="vertical-align: inherit;">它与npm-shrinkwrap.json（5）共享一种格式，该格式本质上是相同的文件，但允许发布。</font><font style="vertical-align: inherit;">除非部署CLI工具或使用发布过程来生产生产软件包，否则不建议这样做。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font><font style="vertical-align: inherit;">软件包的根目录中</font><font style="vertical-align: inherit;">同时</font><font style="vertical-align: inherit;">存在</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>npm-shrinkwrap.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>package-lock.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将被完全忽略。</font></font></p>
</blockquote></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
