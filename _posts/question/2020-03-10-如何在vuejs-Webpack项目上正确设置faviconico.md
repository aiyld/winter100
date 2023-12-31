---
layout: question
title:  如何在vue.js Webpack项目上正确设置favicon.ico？
date:   2020-03-10T03:29:05.000Z
description: 我使用创建了一个vue webpack项目vue-cli。vue init webpack myproject然后在dev模式下运行项目：n...
img: 
author: 神奇伽罗Itachi
category: question
answer: 2
tags: html HTML
topic: HTML
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我使用创建了一个</font></font><code>vue webpack</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">项目</font></font><code>vue-cli</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<pre><code>vue init webpack myproject
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后在</font></font><code>dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模式下</font><font style="vertical-align: inherit;">运行项目</font><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>npm run dev
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我收到此错误：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">加载资源失败：服务器响应状态为404（未找到）</font></font><a href="http://localhost:8080/favicon.ico" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http：// localhost：8080 / favicon.ico</font></font></a></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么在webpack中，如何</font></font><code>favicon.ico</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正确</font><font style="vertical-align: inherit;">导入</font><font style="vertical-align: inherit;">？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第452篇《如何在vue.js Webpack项目上正确设置favicon.ico？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神奇古一</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Laravel 5.x的小更新，将您的</font></font><code>favicon.ico</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>favicon.png</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">放入</font></font><code>/public</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹中，并使用以下方式引用它</font></font><code>index.html</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>&lt;head&gt;<font></font>
    &lt;meta charset="utf-8"&gt;<font></font>
    &lt;link rel="shortcut icon" type="image/png" href="/favicon.png"/&gt;<font></font>
    &lt;title&gt;My Vue.js app&lt;/title&gt;<font></font>
    ...<font></font>
&lt;/head&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望能帮助到你 ！</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里前端Tom</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">查看webpack模板的项目结构：</font><a href="https://vuejs-templates.github.io/webpack/structure.html" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> ://vuejs-templates.github.io/webpack/structure.html</font></font><a href="https://vuejs-templates.github.io/webpack/structure.html" rel="noreferrer"><font style="vertical-align: inherit;"></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意，有一个静态的文件夹，连同</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>src</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">等等。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您将某些图片放入</font></font><code>static</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹中，例如</font></font><code>favicon.png</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它将在</font></font><a href="http://localhost:8080/static/favicon.png" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http：// localhost：8080 / static / favicon.png中提供</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是静态资产的文档：</font><a href="https://vuejs-templates.github.io/webpack/static.html" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://vuejs-templates.github.io/webpack/static.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//vuejs-templates.github.io/webpack/static.html</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于您的网站图标问题，可以将</font></font><code>favicon.ico</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>favicon.png</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">放入</font></font><code>static</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹中，</font></font><code>&lt;head&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并按如下所示</font><font style="vertical-align: inherit;">引用</font><font style="vertical-align: inherit;">index.html的：</font></font></p>

<pre class="lang-html prettyprint-override"><code>&lt;head&gt;<font></font>
    &lt;meta charset="utf-8"&gt;<font></font>
    &lt;link rel="shortcut icon" type="image/png" href="/static/favicon.png"/&gt;<font></font>
    &lt;title&gt;My Vue.js app&lt;/title&gt;<font></font>
    ...<font></font>
&lt;/head&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果你没有定义</font></font><code>favicon.ico</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在你的</font></font><code>index.html</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，那么浏览器就会从网站的根目录（默认行为）一个图标请求。</font><font style="vertical-align: inherit;">如果您如上所述指定图标，则不会再看到该404。</font><font style="vertical-align: inherit;">该图标也将开始显示在浏览器选项卡中。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">附带说明一下，这就是为什么我更喜欢PNG而不是ICO文件的原因：</font></font></p>

<p><a href="https://stackoverflow.com/questions/1344122/favicon-png-vs-favicon-ico-why-should-i-use-png-instead-of-ico"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">favicon.png vs favicon.ico-为什么我应该使用PNG而不是ICO？</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
