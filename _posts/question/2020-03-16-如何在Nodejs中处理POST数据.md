---
layout: question
title:  如何在Node.js中处理POST数据？
date:   2020-03-16T03:30:21.000Z
description: 如何form\[method="post"\]从Node.js中的HTTP POST方法提取表单数据（）和文件上传？我已经阅读了文档，谷歌搜索并没有发现任...
img: 
author: 阿飞宝儿猴子
category: question
answer: 8
tags: Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何</font></font><code>form[method="post"]</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从</font><a href="http://en.wikipedia.org/wiki/Node.js"><font style="vertical-align: inherit;">Node.js中</font></a><font style="vertical-align: inherit;">的HTTP </font></font><code>POST</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font><font style="vertical-align: inherit;">提取表单数据（</font><font style="vertical-align: inherit;">）和文件上传</font><font style="vertical-align: inherit;">？</font></font><a href="http://en.wikipedia.org/wiki/Node.js"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经阅读了文档，谷歌搜索并没有发现任何东西。</font></font></p>

<pre><code>function (request, response) {<font></font>
    //request.post????<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有图书馆还是黑客？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1694篇《如何在Node.js中处理POST数据？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋伽罗猿</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果希望表单数据在req.body中可用，则需要使用bodyParser（）。</font><font style="vertical-align: inherit;">body-parser解析您的请求，并将其转换为一种格式，您可以从中轻松提取可能需要的相关信息。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，假设您在前端有一个注册表单。</font><font style="vertical-align: inherit;">您正在填充它，并请求服务器将详细信息保存在某处。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果使用body-parser，从请求中提取用户名和密码将变得非常简单。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">……………………………………………………。</font></font></p>

<pre><code>var loginDetails = {<font></font>
<font></font>
username : request.body.username,<font></font>
<font></font>
password : request.body.password<font></font>
<font></font>
};<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小哥小卤蛋</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">限制POST大小，避免淹没您的节点应用程序。</font><font style="vertical-align: inherit;">有一个很棒的</font></font><a href="https://github.com/stream-utils/raw-body" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">原始</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块，适用于快速连接和连接，可以帮助您通过大小和长度来限制请求。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门逆天</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><b><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快递v4.17.0</font></font></b> <br> </p>

<pre><code>app.use(express.urlencoded( {extended: true} ))
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神奇神奇Near</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而且，如果您不想使用Express等整个框架，但还需要其他形式的表单，包括上载，那么</font></font><a href="https://github.com/rootslab/formaline" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">福尔马林</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能是一个不错的选择。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它在</font><a href="https://github.com/joyent/node/wiki/modules" rel="nofollow"><font style="vertical-align: inherit;">Node.js模块中</font></a><font style="vertical-align: inherit;">列出</font></font><a href="https://github.com/joyent/node/wiki/modules" rel="nofollow"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿樱</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您不想将数据与</font></font><code>data</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">回调</font><font style="vertical-align: inherit;">一起分块，则</font><font style="vertical-align: inherit;">可以始终使用如下</font></font><code>readable</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">回调：</font></font></p>

<pre><code>// Read Body when Available<font></font>
request.on("readable", function(){<font></font>
  request.body = '';<font></font>
  while (null !== (request.body += request.read())){}<font></font>
});<font></font>
<font></font>
// Do something with it<font></font>
request.on("end", function(){<font></font>
  request.body //-&gt; POST Parameters as String<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这种方法修改了传入的请求，但是一旦您完成响应，该请求就会被垃圾回收，因此这不会成为问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您担心身材庞大，则一种高级方法是首先检查身体大小。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GreenTom</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有多种方法可以做到这一点。</font><font style="vertical-align: inherit;">但是，我知道最快的方法是将Express.js库与body-parser一起使用。</font></font></p>

<pre><code>var express = require("express");<font></font>
var bodyParser = require("body-parser");<font></font>
var app = express();<font></font>
<font></font>
app.use(bodyParser.urlencoded({extended : true}));<font></font>
<font></font>
app.post("/pathpostdataissentto", function(request, response) {<font></font>
  console.log(request.body);<font></font>
  //Or<font></font>
  console.log(request.body.fieldName);<font></font>
});<font></font>
<font></font>
app.listen(8080);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这可以用于字符串，但是如果POST数据包含JSON数组，则可以将bodyParser.urlencoded更改为bodyParser.json。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更多信息：</font><a href="http://www.kompulsa.com/how-to-accept-and-parse-post-requests-in-node-js/" rel="nofollow"><font style="vertical-align: inherit;">http</font></a><font style="vertical-align: inherit;"> : </font></font><a href="http://www.kompulsa.com/how-to-accept-and-parse-post-requests-in-node-js/" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//www.kompulsa.com/how-to-accept-and-parse-post-requests-in-node-js/</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Gil小哥</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果使用</font></font><a href="https://en.wikipedia.org/wiki/Express.js" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Express.js</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则必须先添加中间件bodyParser，然后才能访问req.body：</font></font></p>

<pre><code>app.use(express.bodyParser());
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那你可以要求</font></font></p>

<pre><code>req.body.user
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙阳光</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您使用</font></font><a href="https://github.com/felixge/node-formidable" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node-formidable，</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以按照以下方法进行操作</font><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>var formidable = require("formidable");<font></font>
<font></font>
var form = new formidable.IncomingForm();<font></font>
form.parse(request, function (err, fields) {<font></font>
    console.log(fields.parameter1);<font></font>
    console.log(fields.parameter2);<font></font>
    // ...<font></font>
});<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
