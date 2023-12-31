---
layout: question
title:  如何在node.js中更改process.env.PORT的值？
date:   2020-04-07T03:37:02.000Z
description: 我想更改的值process.env.PORT，我该怎么做？我正在运行Ubuntu 12.04。...
img: 
author: 小小Stafan宝儿
category: question
answer: 4
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想更改的值</font></font><code>process.env.PORT</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，我该怎么做？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在运行Ubuntu 12.04。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4089篇《如何在node.js中更改process.env.PORT的值？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅运行一次（从unix shell提示符）：</font></font></p>

<pre><code>$ PORT=1234 node app.js
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更永久地：</font></font></p>

<pre><code>$ export PORT=1234<font></font>
$ node app.js<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><a href="http://msdn.microsoft.com/en-us/library/windows/desktop/bb776899%28v=vs.85%29.aspx"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Windows中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>set PORT=1234
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Windows </font></font><a href="http://technet.microsoft.com/en-us/library/ff730964.aspx"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">PowerShell中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>$env:PORT = 1234
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Gil</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据@sshow的注释，如果您试图在端口80上运行节点应用程序，则以下不是最佳方法。</font><font style="vertical-align: inherit;">这是一个更好的答案：</font></font><a href="https://stackoverflow.com/questions/6109089/how-do-i-run-node-js-on-port-80/27805105#27805105"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何在端口80上运行Node.js？</font></font></a></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">原始答案：</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您要在端口80上运行此命令（或想</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更永久</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">地设置env变量</font><font style="vertical-align: inherit;">），</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">打开您的bash个人资料
</font></font><code>vim ~/.bash_profile</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将环境变量添加到文件 </font></font><code>export PORT=80</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">打开sudoers配置文件 </font></font><code>sudo visudo</code></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将以下行完全添加到文件中 </font></font><code>Defaults        env_keep +="PORT"</code></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，当您运行</font></font><code>sudo node app.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它</font><font style="vertical-align: inherit;">时，</font><font style="vertical-align: inherit;">它应该可以正常工作。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony凯</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用以下命令在运行节点JS程序时在节点进程中设置端口号：</font></font></p>

<pre><code>set PORT =3000 &amp;&amp; node file_name.js
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">设置的端口可以在代码中访问为 </font></font></p>

<pre><code>process.env.PORT 
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱小胖Mandy</span>
            <span class="discuss-time">2020.04.07</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用跨平台解决方案</font></font><a href="https://www.npmjs.com/package/cross-env" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://www.npmjs.com/package/cross-env</font></font></a></p>

<pre><code>$ cross-env PORT=1234
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
