---
layout: question
title:  NextJS在“ .next”目录中找不到有效的内部版本
date:   2020-03-23T06:39:30.000Z
description: 在问这个问题之前，我看了以下问题，但是我相信我是不同的，因为我没有使用Docker：Nextjs无法在生产node_env的'.next'目录中找到有效的...
img: 
author: Near宝儿
category: question
answer: 2
tags: node.js React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在问这个问题之前，我看了以下问题，但是我相信我是不同的，因为我没有使用Docker：</font></font><a href="https://stackoverflow.com/questions/49676338/nextjs-fails-to-find-valid-build-in-the-next-directory-in-production-node-env"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Nextjs无法在生产node_env的'.next'目录中找到有效的版本。</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我也试过</font></font><a href="https://github.com/zeit/next.js/issues/2691" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">去掉“接下来”文件夹，但是仍然得到同样的问题的方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解决了许多其他问题之后，我只能解决一个似乎无法解决的问题。</font><font style="vertical-align: inherit;">当我尝试部署到Heroku时，不断出现以下错误：</font></font></p>

<pre><code>node server.js<font></font>
<font></font>
Could not find a valid build in the '.next' directory! Try building your app with 'next build' before starting the server.<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的package.json文件： </font></font></p>

<pre><code>{<font></font>
  "name": "StarterApp",<font></font>
  "version": "1.0.0",<font></font>
  "engines": {<font></font>
    "node": "10.4.1"<font></font>
  },<font></font>
  "description": "",<font></font>
  "main": "index.js",<font></font>
  "scripts": {<font></font>
    "test": "mocha",<font></font>
    "dev": "node server.js"<font></font>
  },<font></font>
  "author": "",<font></font>
  "license": "ISC",<font></font>
  "dependencies": {<font></font>
    "express": "4.16.3",<font></font>
    "fs-extra": "^5.0.0",<font></font>
    "ganache-cli": "^6.1.3",<font></font>
    "mocha": "^5.2.0",<font></font>
    "next": "^4.2.3",<font></font>
    "next-routes": "^1.4.2",<font></font>
    "node-gyp": "^3.7.0",<font></font>
    "react": "^16.4.1",<font></font>
    "react-dom": "^16.4.1",<font></font>
    "rebuild": "^0.1.2",<font></font>
    "semantic-ui-css": "^2.3.2",<font></font>
    "semantic-ui-react": "^0.79.1",<font></font>
    "sha3": "^1.2.2",<font></font>
    "solc": "^0.4.24",<font></font>
    "truffle-hdwallet-provider": "0.0.3",<font></font>
    "web3": "^1.0.0-beta.34"<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Server.js文件：</font></font></p>

<pre><code>const { createServer } = require('http');<font></font>
const next = require('next');<font></font>
<font></font>
const app = next({<font></font>
  dev: process.env.NODE_ENV !== 'production'<font></font>
});<font></font>
<font></font>
const routes = require('./routes');<font></font>
const handler = routes.getRequestHandler(app);<font></font>
<font></font>
app.prepare().then(() =&gt; {<font></font>
  createServer(handler).listen(5000, (err) =&gt; {<font></font>
    if (err) throw err;<font></font>
    console.log('Ready on localhost:5000');<font></font>
  });<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该应用程序在本地部署没有问题，但是在部署到Heroku时出现此错误。</font><font style="vertical-align: inherit;">我究竟做错了什么？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2855篇《NextJS在“ .next”目录中找不到有效的内部版本》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长猴子</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><pre><code>npm run build
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后 </font></font></p>

<pre><code>npm run start
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解决了我的问题。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">DavaidTony宝儿</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NextJS的构建</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很大</font><font style="vertical-align: inherit;">（取决于您的项目大小），这可能会非常庞大​​，在部署过程中可能会花费您大量资金。</font><font style="vertical-align: inherit;">您可以将以下内容应用于</font></font><code>package.json</code></p>

<pre><code>{<font></font>
    "script": {<font></font>
        "build": "next build",<font></font>
        "heroku-postbuild": "npm run build",<font></font>
        "start": "next start"<font></font>
    }<font></font>
}<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
