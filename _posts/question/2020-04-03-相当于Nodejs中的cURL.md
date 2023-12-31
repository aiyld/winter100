---
layout: question
title:  相当于Node.js中的cURL？
date:   2020-04-03T02:39:43.000Z
description: 我希望使用来自Node.js的HTTP请求中的信息（即，调用远程Web服务并将响应回显到客户端）。在PHP中，我会使用cURL来做到这一点。Node的...
img: 
author: 伽罗
category: question
answer: 7
tags: 卷曲 Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我希望使用来自Node.js的HTTP请求中的信息（即，调用远程Web服务并将响应回显到客户端）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在PHP中，我会使用cURL来做到这一点。</font><font style="vertical-align: inherit;">Node的最佳做法是什么？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3900篇《相当于Node.js中的cURL？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以尝试使用POSTMAN Chrome应用进行请求，并可以从中生成节点js代码 </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Request npm模块</font></font><a href="https://www.npmjs.com/package/request" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Request节点</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块</font><font style="vertical-align: inherit;">很好用，它具有用于get / post请求的选项设置，并且它也广泛用于生产环境中。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Gil伽罗小宇宙</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我最终使用了</font></font><a href="https://github.com/sindresorhus/grunt-shell" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">grunt-shell</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">库。</font></font></p>

<p><a href="https://gist.github.com/gnitnuj/aba5e09f1fa6a98be803#file-readme-md" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是我为考虑使用EdgeCast API的任何其他人而完全实施的Grunt任务的源代码。</font><font style="vertical-align: inherit;">您会在我的示例中发现，我使用grunt-shell执行执行清除CDN的curl命令。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我花了数小时试图使HTTP请求在Node中工作后的结果。</font><font style="vertical-align: inherit;">我能够使用Ruby和Python进行工作，但不满足该项目的要求。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">DavaidTony宝儿</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">好吧，如果您真的需要等同的卷曲度，可以尝试 </font></font><a href="https://github.com/jiangmiao/node-curl" rel="noreferrer"><code>node-curl</code></a>  </p>

<pre><code>npm install node-curl
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可能需要添加</font></font><code>libcurl4-gnutls-dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云番长番长</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上面的示例可以正常工作，但并不能真正处理一个真实的示例（例如，当您处理多个块中的数据时。您需要确保的一件事是，您需要一个“ on chunk”处理程序将数据推送到一个数组中（在JS中完成此操作的最快方法）和一个“ on end”处理程序，将它们全部连接在一起，以便您可以返回它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当您处理大请求（5000多个行）并且服务器向您发送大量数据时，这尤其必要。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的一个程序（咖啡脚本）中的示例：</font><a href="https://gist.github.com/1105888"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> ://gist.github.com/1105888 
</font></font><a href="https://gist.github.com/1105888"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如</font></font><a href="https://github.com/joyent/node/wiki/modules#wiki-tcp" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/joyent/node/wiki/modules#wiki-tcp</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">怎么样</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">快速总结=&gt;</font></font></p>

<ul>
<li><a href="https://github.com/visionmedia/superagent" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/visionmedia/superagent</font></font></a></li>
<li><a href="https://github.com/mikeal/request" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/mikeal/request</font></font></a> </li>
</ul></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy</span>
            <span class="discuss-time">2020.04.03</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关完整示例，请参见HTTP模块的文档：</font></font></p>

<p><a href="https://nodejs.org/api/http.html#http_http_request_options_callback" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://nodejs.org/api/http.html#http_http_request_options_callback</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
