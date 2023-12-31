---
layout: question
title:  如何通过https运行Vue.js开发服务？
date:   2020-03-12T02:27:15.000Z
description: 我正在使用Vue-cli通过Webpack模板创建vue项目。如何在开发中使用https来运行它npm run dev？...
img: 
author: 神无LEYMandy
category: question
answer: 3
tags: https Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用Vue-cli通过Webpack模板创建vue项目。</font><font style="vertical-align: inherit;">如何在开发中使用https来运行它</font></font><code>npm run dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第887篇《如何通过https运行Vue.js开发服务？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝村村</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在chrome或edge中运行时，您仍然会收到警告，因为该证书不是经过严格认证的证书。</font><font style="vertical-align: inherit;">但是，通过设置以下标志，可以在运行站点时切换问题：</font></font></p>

<pre><code>chrome://flags/#allow-insecure-localhost
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在最新Edge中也可以使用</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙神奇飞云</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最简单的方法是进入package.json并将“ dev”更改为 </font></font></p>

<pre><code> "dev": "webpack-dev-server --inline --progress  --https --config build/webpack.dev.conf.js",
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它仍然会</font><font style="vertical-align: inherit;">在控制台中的</font></font><a href="http://localhost" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http：// localhost</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上运行该消息，</font><font style="vertical-align: inherit;">但是您可以在</font><a href="https://localhost" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https：// localhost</font></a><font style="vertical-align: inherit;">上访问该站点</font></font><a href="https://localhost" rel="nofollow noreferrer"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">A飞云</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在中</font></font><code>/build/webpack.dev.conf.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，要</font></font><code>devWepackConfig</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在中</font></font><code>devServer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，添加</font></font></p>

<pre><code>https: true
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
