---
layout: question
title:  用express.js代理
date:   2020-03-24T10:08:38.000Z
description: 为了避免同域AJAX问题，我希望我的node.js Web服务器将所有从URL的请求转发/api/BLABLA到另一台服务器，例如other_domain...
img: 
author: Harry小胖
category: question
answer: 0
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了避免同域AJAX问题，我希望我的node.js Web服务器将所有从URL的请求转发</font></font><code>/api/BLABLA</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到另一台服务器，例如</font></font><code>other_domain.com:3000/BLABLA</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，并透明地将与该远程服务器返回的相同的内容返回给用户。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有其他网址（位于旁</font></font><code>/api/*</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）均应直接提供，不能进行代理。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用node.js + express.js实现此目的？</font><font style="vertical-align: inherit;">您可以举一个简单的代码示例吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（Web服务器和远程</font></font><code>3000</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">服务器都在我的控制下，都运行带有express.js的node.js）</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">到目前为止，我已经找到了这个</font></font><a href="https://github.com/http-party/node-http-proxy" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/http-party/node-http-proxy</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是阅读那里的文档并没有使我更加明智。</font><font style="vertical-align: inherit;">我最终以</font></font></p>

<pre><code>var proxy = new httpProxy.RoutingProxy();<font></font>
app.all("/api/*", function(req, res) {<font></font>
    console.log("old request url " + req.url)<font></font>
    req.url = '/' + req.url.split('/').slice(2).join('/'); // remove the '/api' part<font></font>
    console.log("new request url " + req.url)<font></font>
    proxy.proxyRequest(req, res, {<font></font>
        host: "other_domain.com",<font></font>
        port: 3000<font></font>
    });<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但没有任何内容返回到原始Web服务器（或最终用户），因此没有运气。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3618篇《用express.js代理》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
