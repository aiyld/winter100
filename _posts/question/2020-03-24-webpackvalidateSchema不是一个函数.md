---
layout: question
title:  webpack.validateSchema不是一个函数
date:   2020-03-24T07:45:39.000Z
description: Webpack突然抛出此错误：  TypeError：webpack.validateSchema不是一个函数星期五一切正常，今天不工作。自周...
img: 
author: 梅
category: question
answer: 8
tags: JavaScript Webpack
topic: Webpack
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Webpack突然抛出此错误：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TypeError：webpack.validateSchema不是一个函数</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">星期五一切正常，今天不工作。</font><font style="vertical-align: inherit;">自周五以来，没有新的提交要掌握。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">修剪了无效的NPM，删除了NPM文件夹并重新安装，没有骰子。</font><font style="vertical-align: inherit;">检出过一个星期未从Master重新定级的以前的分支机构。</font><font style="vertical-align: inherit;">还是一样。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有人有主意吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3465篇《webpack.validateSchema不是一个函数》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德小胖</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我遇到了这个问题，因为我安装了一个较旧的全局版本的webpack，这在某种程度上与项目特定的webpack冲突。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我首先通过运行以下命令卸载了全局（旧）webpack：</font></font></p>

<pre><code>npm uninstall webpack -g
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，我运行了特定于项目的Webpack。</font><font style="vertical-align: inherit;">在Windows上，webpack.cmd驻留在node_modules.bin \中，但是如果您通过npm任务运行webpack，则npm将自动搜索.bin文件夹，因此无需显式指定该路径。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">package.json中正在运行的npm run任务如下所示：</font></font></p>

<pre><code>  "scripts": {<font></font>
      "webpack": "webpack -w --config ./config/dev.js --progress"<font></font>
  }<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长樱梅</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我们将angular / cli升级到1.6.3并测试ng -v时，遇到了同样的问题，导致webpack出现错误。</font><font style="vertical-align: inherit;">因此，我们碰巧卸载了webpack，清理了缓存，然后再次在全局范围内安装了webpack。</font><font style="vertical-align: inherit;">它解决了问题</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">前端猿小哥</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我通过运行以下命令使其工作：</font></font></p>

<pre><code>npm install --save-dev webpack-dev-server@beta webpack@beta
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长Near</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我这样做时，它对我有用：</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">卸载以下软件包：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm卸载webpack webpack-dev-server --save -dev</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装以下软件包：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm install --save -dev webpack@3.10.0</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm install --save -dev webpack-cli@2.0.10</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm install --save -dev webpack-dev-server@2.9.7</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅蛋蛋</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我也遇到同样的错误。</font><font style="vertical-align: inherit;">我将我的webpack-dev-server版本锁定在package.json文件中，这防止了错误的发生。</font><font style="vertical-align: inherit;">但这并不能解决错误的根本问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我正在使用的webpack-dev-server的版本，但我确定以后的版本也能正常工作：“ webpack-dev-server”：“ 2.1.0-beta.9”，</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我删除^并使用确切的版本时，它对我有用。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从 </font></font></p>

<pre><code>"webpack": "2.1.0-beta.25",<font></font>
"webpack-dev-middleware": "^1.6.1",<font></font>
"webpack-dev-server": "^2.1.0-beta.9",<font></font>
"webpack-md5-hash": "^0.0.5",<font></font>
"webpack-merge": "^0.14.1"<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">至 </font></font></p>

<pre><code>"webpack": "2.1.0-beta.25",<font></font>
"webpack-dev-middleware": "1.6.1",<font></font>
"webpack-dev-server": "2.1.0-beta.9",<font></font>
"webpack-md5-hash": "0.0.5",<font></font>
"webpack-merge": "0.14.1"<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GOL</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">看起来像npm bug，因为</font></font><code>webpack-dev-server@2.1.0-beta.11</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">需要</font></font><code>webpack@^2.1.0-beta.26</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但npm无法安装它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无需过多更新即可避免该问题的最简单方法是将package.json中的依赖项更改为</font></font></p>

<pre><code>  "webpack-dev-server": "2.1.0-beta.10",
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不是像</font></font></p>

<pre><code>  "webpack-dev-server": "^2.1.0-beta.9",
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">版本前的“ ^”字符表示“与...兼容”。</font><font style="vertical-align: inherit;">删除它完全符合该版本。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不要忘记跑步</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>npm update</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之后。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯达蒙</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">今天，我几乎与您同时遇到了这个问题，事实证明webpack再次被更新了。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我所做的修复工作：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先我跑</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>npm update</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，看看有什么结果。</font><font style="vertical-align: inherit;">我运行这两个命令是因为npm有一种怪异的方式来报告未满足的依赖关系，有时是错误的，当您重新运行the </font></font><code>npm update</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或the时</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，您将意识到未满足的依赖关系不再是问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行这些命令后，我注意到剩下的唯一消息是警告：</font></font></p>

<p><code>npm WARN webpack-dev-server@2.1.0-beta.11 requires a peer of webpack@^2.1.0-beta.26 but none was installed.</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了解决这个问题，我将</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件</font><font style="vertical-align: inherit;">更改</font><font style="vertical-align: inherit;">为read </font></font><code>"webpack": "2.1.0-beta.26"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>"webpack": "2.1.0-beta.25"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后运行另一个文件</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此后，当我尝试运行时遇到另一个错误，该错误</font></font><code>npm start</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">表明我的webpack配置文件存在问题。</font><font style="vertical-align: inherit;">就我而言，我转到开发环境的webpack配置文件（因为我尚未投入生产），我发现了罪魁祸首，这是一个无效参数，称为“ outputPath”。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我注释掉了那条线，现在一切正常。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望这会有所帮助，暂时可能只是一个hack，但希望这是朝正确方向迈出的一步。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">好的，所以我对一切“正常工作”都有些不对。</font><font style="vertical-align: inherit;">事实证明，我的某些装载机无法正常工作。</font><font style="vertical-align: inherit;">Bootstrap和其他一些东西没有正确加载，破坏了我的风格。</font><font style="vertical-align: inherit;">因此，为了使其恢复到以前的状态，我删除了</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹并在中</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用以下命令</font><font style="vertical-align: inherit;">运行</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>"webpack": "2.1.0-beta.25",<font></font>
"webpack-dashboard": "^0.1.8",<font></font>
"webpack-dev-middleware": "^1.6.1",<font></font>
"webpack-dev-server": "2.1.0-beta.9",<font></font>
"webpack-md5-hash": "^0.0.5",<font></font>
"webpack-merge": "^0.15.0",<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望像这样的讨论将帮助我们弄清楚如何正确发布新版的webpack。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
