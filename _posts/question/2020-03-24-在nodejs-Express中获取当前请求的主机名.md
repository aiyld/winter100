---
layout: question
title:  在node.js Express中获取当前请求的主机名
date:   2020-03-24T07:22:42.000Z
description: 因此，我在这里可能遗漏了一些简单的东西，但是我似乎无法找到一种方法来获取向其发送响应的请求对象的主机名。是否可以找出用户当前从node.js访问的主机...
img: 
author: 阿飞
category: question
answer: 5
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，我在这里可能遗漏了一些简单的东西，但是我似乎无法找到一种方法来获取向其发送响应的请求对象的主机名。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是否可以找出用户当前从node.js访问的主机名？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3436篇《在node.js Express中获取当前请求的主机名》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是另一种</font></font></p>

<pre><code>req.hostname
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font></font><a href="http://expressjs.com/en/api.html#req.hostname" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Express Docs中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">了解它</font><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯小胖</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用os模块：</font></font></p>

<pre><code>var os = require("os");<font></font>
os.hostname();<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请参阅</font></font><a href="http://nodejs.org/docs/latest/api/os.html#os_os_hostname" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://nodejs.org/docs/latest/api/os.html#os_os_hostname</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意事项：</font></font></p>

<ol>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果可以使用IP地址-机器可能有多个网卡，并且除非您指定它，否则节点将侦听所有这些网卡，因此您不知道请求进入哪个NIC才进入。 </font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主机名是DNS问题-不要忘记多个DNS别名可以指向同一台计算机。</font></font></p></li>
</ol></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果需要完全限定的域名且没有HTTP请求，则在Linux上，可以使用：</font></font></p>

<pre><code>var child_process = require("child_process");<font></font>
<font></font>
child_process.exec("hostname -f", function(err, stdout, stderr) {<font></font>
  var hostname = stdout.trim();<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猪猪Green</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，在提供答案之前，我想先了解一下以下事实：通过信任标头，您可以打开网络钓鱼等安全漏洞的大门。</font><font style="vertical-align: inherit;">因此，出于重定向目的，在未首先验证URL是否得到授权之前，请勿使用标头中的值。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您的操作系统主机名可能不一定与DNS匹配。</font><font style="vertical-align: inherit;">实际上，一个IP可能具有多个DNS名称。</font><font style="vertical-align: inherit;">因此，出于HTTP目的，不能保证在操作系统配置中分配给计算机的主机名是可用的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我能想到的最佳选择是获取HTTP侦听器公共IP并通过DNS解析其名称。</font><font style="vertical-align: inherit;">有关</font></font><code>dns.reverse</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更多信息，</font><font style="vertical-align: inherit;">请参见</font><font style="vertical-align: inherit;">方法。</font><font style="vertical-align: inherit;">但是，请再次注意，一个IP可能具有多个与之关联的名称。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖Gil</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您正在谈论HTTP请求，则可以在以下位置找到请求主机：</font></font></p>

<pre><code>request.headers.host
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但这取决于传入的请求。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关更多信息，请访问</font></font><a href="http://nodejs.org/docs/v0.4.12/api/http.html#http.ServerRequest" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://nodejs.org/docs/v0.4.12/api/http.html#http.ServerRequest</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果要查找机器/本机信息，请尝试使用过程对象。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
