---
layout: question
title:  Next.js：修改文件后刷新页面，而无需重新运行“ npm run”
date:   2020-03-24T06:33:35.000Z
description: 我已经使用普通的LAMP堆栈和前端的javascript（和jQuery）构建网站。但我也想尝试将javascript用于后端。我刚刚开始学习next.j...
img: 
author: 梅
category: question
answer: 2
tags: JavaScript React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经使用普通的LAMP堆栈和前端的javascript（和jQuery）构建网站。</font><font style="vertical-align: inherit;">但我也想尝试将javascript用于后端。</font><font style="vertical-align: inherit;">我刚刚开始学习next.js。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在旧的方法上，如果我修改了php文件，要查看效果，我可以刷新Web浏览器。</font><font style="vertical-align: inherit;">但是我注意到，使用next.js不能立即看到更改。</font><font style="vertical-align: inherit;">我必须停止npm脚本，重新运行“ npm run xxx”命令，然后刷新浏览器。</font><font style="vertical-align: inherit;">这很费时间。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有没有办法使这个过程自动化？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3384篇《Next.js：修改文件后刷新页面，而无需重新运行“ npm run”》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里神奇</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在开发模式下，默认情况下，Next.js将热重新加载所有更改，您甚至无需刷新浏览器。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，如果您添加了自定义服务器，则不会对它进行热重载更改。</font><font style="vertical-align: inherit;">您可以使用nodemon来监视并重新启动服务器：</font><a href="https://github.com/remy/nodemon" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/remy/nodemon" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/remy/nodemon</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@Rudi的答案是正确的，我还要补充一点，您要确保最终运行的命令</font></font><code>next</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不是</font></font><code>next start</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">区别在于</font></font><code>next</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于开发模式，而</font></font><code>next start</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于生产模式。</font><font style="vertical-align: inherit;">在生产模式下，它不会监视文件的更改。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通常，在package.json的脚本部分中引用了以下命令：</font></font></p>

<pre><code>{<font></font>
  "scripts": {<font></font>
    "dev": "next",<font></font>
    "build": "next build",<font></font>
    "start": "next start"<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您实际键入并运行的命令将</font></font><code>npm run dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于本地开发或</font></font><code>npm run build; npm run start</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生产模式。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果这不适合您的使用，并且即使在开发模式下也必须重新启动服务器，则可能是您的设置有问题。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
