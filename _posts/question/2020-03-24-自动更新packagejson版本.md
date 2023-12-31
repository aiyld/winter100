---
layout: question
title:  自动更新package.json版本
date:   2020-03-24T07:16:03.000Z
description: 在做一个小版本发布并标记它之前，我想更新package.json以反映该程序的新版本。有没有一种方法可以package.json自动编辑文件？需要...
img: 
author: 斯丁前端
category: question
answer: 8
tags: git Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在做一个小版本发布并标记它之前，我想更新package.json以反映该程序的新版本。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有没有一种方法可以</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自动</font><font style="vertical-align: inherit;">编辑文件</font><font style="vertical-align: inherit;">？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">需要</font></font><code>git pre-release hook</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">帮助吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3428篇《自动更新package.json版本》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，您需要了解升级版本号的规则。</font><font style="vertical-align: inherit;">您可以</font><font style="vertical-align: inherit;">在此处</font><font style="vertical-align: inherit;">阅读有关</font></font><a href="https://flaviocopes.com/npm-semantic-versioning/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语义版本的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更多信息</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">每个版本都有xyz版本，其中定义了不同的用途，如下所示。</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">x-major，当您有重大更改且发生更改的差异很大时，请向上移动。 </font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">y-次要，当您具有新功能或增强功能时，此功能会增加。 </font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">z-修补程序，当您已修复错误或在较早版本上还原更改时，请进行修补。</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要运行脚本，可以在package.json中定义它。</font></font></p>

<pre><code>"script": {<font></font>
    "buildmajor": "npm version major &amp;&amp; ng build --prod",<font></font>
    "buildminor": "npm version minor &amp;&amp; ng build --prod",<font></font>
    "buildpatch": "npm version patch &amp;&amp; ng build --prod"<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在您的终端中，您只需要根据需要运行npm </font></font></p>

<pre><code>npm run buildpatch
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果在git repo中运行它，则默认的git-tag-version为true；如果您不想这样做，则可以在脚本中添加以下命令：</font></font></p>

<pre><code>--no-git-tag-version
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如： </font></font><code>"npm --no-git-tag-version version major &amp;&amp; ng build --prod"</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我创建了一个</font></font><a href="https://github.com/GetchaDEAGLE/eagle-versioner" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">工具</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，可以根据提交消息中的标记（称为更改类型）完成自动语义版本控制。</font><font style="vertical-align: inherit;">这紧随Angular Commit消息约定以及语义版本控制规范。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用此工具来使用故宫CLI中的package.json自动更改版本（这被描述</font></font><a href="https://github.com/GetchaDEAGLE/eagle-versioner#versioning-automation" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，它可以根据这些提交创建一个更改日志，并且还具有一个菜单（带有用于提交消息的拼写检查器），用于根据更改类型创建提交。</font><font style="vertical-align: inherit;">我强烈建议您检查一下并阅读文档，以查看可以完成的所有操作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我写这个工具是因为找不到适合我的CICD Pipeline自动进行语义版本控制的需求的东西。</font><font style="vertical-align: inherit;">我宁愿将重点放在实际的更改上，而不是在版本上，这是我的工具节省时间的地方。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关该工具原理的更多信息，请</font></font><a href="https://danieleagle.com/2020/01/introducing-eagle-versioner/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参见this</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想为这个问题得到的答案增加一些清晰度。</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">即使认为这里有一些答案可以正确解决问题并提供解决方案，也不是正确的答案。</font><font style="vertical-align: inherit;">这个问题的正确答案是使用</font></font><code>npm version</code></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有没有一种方法可以自动编辑文件package.json？</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，你可以做什么来实现这一目标，即运行</font></font><code>npm version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在需要时命令，你可以阅读更多关于它</font></font><a href="https://docs.npmjs.com/cli/version.html" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里NPM版本</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但基本的用法是</font></font><code>npm version patch</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它会在您添加的第三个数字顺序</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">版本（1.0 </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">X</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用git pre-release hook有帮助吗？</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以根据需要配置</font></font><code>npm version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在预发行版本的挂钩上</font><font style="vertical-align: inherit;">运行</font><font style="vertical-align: inherit;">命令，但这取决于CD / CI管道中是否需要此</font></font><code>npm version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令</font><font style="vertical-align: inherit;">，但是如果没有该</font><font style="vertical-align: inherit;">命令，</font></font><code>git pre-release</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">挂钩将无法“轻松”执行任何操作与</font></font><code>package.json</code> </p>

<p><strong><font style="vertical-align: inherit;"></font><code>npm version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正确答案</font><font style="vertical-align: inherit;">的原因</font><font style="vertical-align: inherit;">如下：</font></font></strong></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果用户正在使用他所在的文件夹结构，</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则</font></font><code>npm</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果他正在使用</font></font><code>npm</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则可以访问</font></font><code>npm scripts</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果他有权访问，则</font></font><code>npm scripts</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">他有权访问</font></font><code>npm version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用此命令，他不需要在计算机或CD / CI管道中安装任何其他东西，从长远来看，这将减少项目的可维护性，并有助于设置</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">建议使用其他工具的其他答案是错误的。</font></font></p>

<p><code>gulp-bump</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 可行，但需要另一个额外的程序包，这可能会长期产生问题（我的答案的第3点）</font></font></p>

<p><code>grunt-bump</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 可行，但需要另一个额外的程序包，这可能会长期产生问题（我的答案的第3点）</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙JinJin路易</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">给出最新的方法。</font></font></p>

<h3><code>package.json</code></h3>

<pre class="lang-json prettyprint-override"><code>  "scripts": {<font></font>
    "eslint": "eslint index.js",<font></font>
    "pretest": "npm install",<font></font>
    "test": "npm run eslint",<font></font>
    "preversion": "npm run test",<font></font>
    "version": "",<font></font>
    "postversion": "git push &amp;&amp; git push --tags &amp;&amp; npm publish"<font></font>
  }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后运行它：</font></font></p>

<pre class="lang-sh prettyprint-override"><code>npm version minor --force -m "Some message to commit"
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将：</font></font></p>

<ol>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">...运行测试...</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将您的</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">版本</font><font style="vertical-align: inherit;">更改</font><font style="vertical-align: inherit;">为下一个次要版本（例如：1.8.1至1.9.0）</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">推动你的改变</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">创建一个新的git tag版本，</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">发布您的npm软件包。</font></font></p></li>
</ol>

<p><code>--force</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是为了表明谁是老板！</font><font style="vertical-align: inherit;">除了笑话，请参阅</font></font><a href="https://github.com/npm/npm/issues/8620" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/npm/npm/issues/8620</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐泡芙</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您使用纱线，则可以使用 </font></font></p>

<pre><code>yarn version --patch
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过patch更新版本</font></font><code>(0.0.x)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，提交并用格式标记它</font></font><code>v0.0.0</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">同样，您可以使用</font></font><code>--minor</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font><font style="vertical-align: inherit;">更改次要或主要版本</font></font><code>--major</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">推送到git时，请确保您也使用 </font></font><code>--follow-tags</code></p>

<pre><code>git push --follow-tags
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您也可以为其创建脚本</font></font></p>

<pre><code>    "release-it": "yarn version --patch &amp;&amp; git push --follow-tags"
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需输入以下内容即可运行 </font></font><code>yarn release-it</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，</font><font style="vertical-align: inherit;">如果您想要版本变更但不添加标签或提交新内容，则</font></font><code>npm version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以使用该</font></font><code>--no-git-tag-version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">标志：</font></font></p>

<pre><code>npm --no-git-tag-version version patch
</code></pre>

<p><a href="https://docs.npmjs.com/cli/version" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://docs.npmjs.com/cli/version</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomDavaid</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这通常是我对项目所做的：</font></font></p>

<pre><code>npm version patch<font></font>
git add *;<font></font>
git commit -m "Commit message"<font></font>
git push<font></font>
npm publish<font></font>
</code></pre>

<p>The first line, <code>npm version patch</code>, will increase the patch version by 1 (x.x.1 to x.x.2) in <code>package.json</code>. Then you add all files -- including <code>package.json</code> which at that point has been modified.
Then, the usual <code>git commit</code> and <code>git push</code>, and finally <code>npm publish</code> to publish the module.</p>

<p>I hope this makes sense...</p>

<p>Merc.</p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁逆天</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><code>npm version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能是正确的答案。</font><font style="vertical-align: inherit;">只给一个替代我建议</font></font><a href="https://github.com/vojtajina/grunt-bump"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">咕噜凸点</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它由angular.js的一名成员维护。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用法：</font></font></p>

<pre><code>grunt bump<font></font>
&gt;&gt; Version bumped to 0.0.2<font></font>
<font></font>
grunt bump:patch<font></font>
&gt;&gt; Version bumped to 0.0.3<font></font>
<font></font>
grunt bump:minor<font></font>
&gt;&gt; Version bumped to 0.1.0<font></font>
<font></font>
grunt bump<font></font>
&gt;&gt; Version bumped to 0.1.1<font></font>
<font></font>
grunt bump:major<font></font>
&gt;&gt; Version bumped to 1.0.0<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果仍然使用grunt，那可能是最简单的解决方案。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
