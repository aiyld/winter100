---
layout: question
title:  命令行上的Node.js版本？（不是REPL）
date:   2020-03-16T06:40:11.000Z
description: 我想在命令行上获取Node.js的版本。我期望运行类似的命令：node -version但这不起作用。有人知道命令行是什么吗？（即不是REPL）...
img: 
author: YOC69983874
category: question
answer: 11
tags: Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想在命令行上获取Node.js的版本。</font><font style="vertical-align: inherit;">我期望运行类似的命令：</font></font></p>

<pre><code>node -version
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但这不起作用。</font><font style="vertical-align: inherit;">有人知道命令行是什么吗？</font><font style="vertical-align: inherit;">（即不是REPL）</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1766篇《命令行上的Node.js版本？（不是REPL）》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞番长</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在运行Debian Stretch的Arm7（armhf）设备上，我必须发出以下任一命令：</font></font></p>

<pre><code>$ nodejs -v<font></font>
$ nodejs -h<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以下无效：</font></font></p>

<pre><code>$ node -v<font></font>
$ node -h<font></font>
$ apm -v<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望这对其他人有帮助。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪飞云</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">打开node.js命令提示符</font></font></strong><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行此命令</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点-v</font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一凯</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以通过键入以下命令检查是否安装了Node和Npm：</font></font></p>

<p><code>$node --version &amp;&amp; npm --version</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TonyStafan</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需</font></font><code>npm version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在命令行中</font><font style="vertical-align: inherit;">键入</font><font style="vertical-align: inherit;">，它将显示有关节点，npm，v8引擎等的所有版本详细信息。</font></font></p>

<p><a href="https://i.stack.imgur.com/NWv1S.png" rel="nofollow noreferrer"><img src="https://i.stack.imgur.com/NWv1S.png" alt="在此处输入图片说明"></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tom阳光</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您正在使用Atom编辑器，那么一个不错的提示。 </font></font></p>

<pre><code>$ apm -v<font></font>
apm  1.12.5<font></font>
npm  3.10.5<font></font>
node 4.4.5<font></font>
python 2.7.12<font></font>
git 2.7.4<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它不仅会返回节点版本，还会返回其他一些内容。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪小小小哥</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">默认情况下，节点包是nodejs，因此请使用 </font></font></p>

<pre><code>$ nodejs -v
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要么</font></font></p>

<pre><code>$ nodejs --version 
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用以下链接</font></font></p>

<pre><code>$ sudo ln -s /usr/bin/nodejs /usr/bin/node
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后你可以使用 </font></font></p>

<pre><code>$ node --version
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要么 </font></font></p>

<pre><code>$ node -v
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Harry蛋蛋Eva</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试   </font></font><code>nodejs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不只是</font></font><code>node</code></p>

<pre class="lang-none prettyprint-override"><code>$ nodejs -v<font></font>
v0.10.25<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小猪猪</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您引用的是shell命令行，则可以使用以下两种方法之一：</font></font></p>

<pre><code>node -v<font></font>
<font></font>
node --version<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅仅键入</font></font><code>node version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将导致node.js尝试加载名为版本的模块，除非您喜欢使用混淆的模块名称，否则该模块将不存在。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一小宇宙</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><blockquote>
  <blockquote>
    <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用Repl命令查找Nodejs版本</font></font></p>
  </blockquote>
</blockquote>

<pre><code>$node<font></font>
&gt;process.version<font></font>
`v8.x`<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅Harry米亚</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<p><code>node --version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 要么 </font></font><code>node -v</code></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<p><code>npm --version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 要么 </font></font><code>npm -v</code></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">V8引擎版本</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>node -p process.versions.v8
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令行是：</font></font></p>

<pre><code>node -v
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要么</font></font></p>

<pre><code>node --version
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>node -v</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不行，但行得通，</font></font><code>nodejs -v</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">则说明您的系统上的某些设置不正确。</font><font style="vertical-align: inherit;">有关</font><font style="vertical-align: inherit;">解决方法，</font><font style="vertical-align: inherit;">请参阅</font></font><a href="https://stackoverflow.com/questions/18130164/nodejs-vs-node-on-ubuntu-12-04"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此其他问题</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
