---
layout: question
title:  Node.js引发“未定义btoa”错误
date:   2020-03-23T06:22:20.000Z
description: 在我的node.js应用程序中，我做了一个操作，npm install btoa-atob以便可以使用客户端javascript中固有的btoa（）和at...
img: 
author: JinJin猿
category: question
answer: 2
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在我的node.js应用程序中，我做了一个操作，</font></font><code>npm install btoa-atob</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以便可以使用客户端javascript中固有的btoa（）和atob（）函数，但由于某种原因未包含在node中。</font><font style="vertical-align: inherit;">新目录显示在我的node_modules文件夹中，该文件夹本身与app.js一起位于根目录中。</font><font style="vertical-align: inherit;">然后，确保将btoa-atob作为依赖项添加到根目录下的package.json文件中。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，由于某种原因，它仍然无法正常工作。</font></font></p>

<pre><code>console.log(btoa("Hello World!"));
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">^应该向控制台输出“ SGVsbG8gV29ybGQh”，但是，我收到错误消息“未定义btoa”。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我没有正确安装吗？</font><font style="vertical-align: inherit;">我忽略了什么？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2822篇《Node.js引发“未定义btoa”错误》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也许您不再需要它，但是如果有人使用节点需要它：</font><a href="https://www.npmjs.com/package/btoa" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> :
 </font></font><a href="https://www.npmjs.com/package/btoa" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//www.npmjs.com/package/btoa</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">null</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我了解这是节点应用程序的讨论点，但是出于</font><font style="vertical-align: inherit;">在节点服务器上运行</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的通用JavaScript应用程序的兴趣（</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我到达这篇文章的方式），我一直在研究通用/同构React应用程序。建筑，这个包装</font></font><a href="https://github.com/jsdom/abab" rel="nofollow noreferrer"><code>abab</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我有用。</font><font style="vertical-align: inherit;">实际上，这是我能找到的唯一可行的解​​决方案，而不是使用也提到的Buffer方法（我遇到 TypeScript问题）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（此包由</font></font><code>jsdom</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所使用，而</font></font><code>window</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包</font><font style="vertical-align: inherit;">又由该</font><font style="vertical-align: inherit;">包使用。）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">回到我的观点；</font><font style="vertical-align: inherit;">基于此，也许如果该功能已经像您提到的那样已经作为npm软件包编写，并且具有基于W3规范的自己的算法，则可以安装和使用该</font></font><code>abab</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">软件包，而不必编写自己的可能会或可能不会根据编码准确。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">- </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> -</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">今天，我开始使用package编码出现奇怪的问题（不确定为什么现在开始发生）</font></font><code>abab</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">大部分时间似乎正确编码，但有时在前端它编码不正确。</font><font style="vertical-align: inherit;">花了很长时间尝试调试，但是</font></font><code>base-64</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据建议</font><font style="vertical-align: inherit;">切换到软件包</font><font style="vertical-align: inherit;">，它立即起作用。</font><font style="vertical-align: inherit;">绝对似乎取决于的base64算法</font></font><code>abab</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
