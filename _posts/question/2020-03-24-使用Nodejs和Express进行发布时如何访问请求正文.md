---
layout: question
title:  使用Node.js和Express进行发布时如何访问请求正文？
date:   2020-03-24T09:05:15.000Z
description: 我有以下Node.js代码：var express = require('express');var app = express.createSer...
img: 
author: 西门Davaid
category: question
answer: 5
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有以下Node.js代码：</font></font></p>

<pre><code>var express = require('express');<font></font>
var app = express.createServer(express.logger());<font></font>
app.use(express.bodyParser());<font></font>
<font></font>
app.post('/', function(request, response) {<font></font>
    response.write(request.body.user);<font></font>
    response.end();<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，如果我发布类似的内容：</font></font></p>

<pre><code>curl -d user=Someone -H Accept:application/json --url http://localhost:5000
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我得到</font></font><code>Someone</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">了预期的结果。</font><font style="vertical-align: inherit;">现在，如果我想获得完整的请求正文怎么办？</font><font style="vertical-align: inherit;">我尝试这样做，</font></font><code>response.write(request.body)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是Node.js抛出一个异常，说“ </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一个参数必须是字符串或Buffer</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ”，然后转到“无限循环”，并出现异常，指出“ </font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">发送标头后不能设置标头</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ”。</font><font style="vertical-align: inherit;">即使我</font></font><code>var reqBody = request.body;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">再写了</font><font style="vertical-align: inherit;">也是这样</font></font><code>response.write(reqBody)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里有什么问题？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，我可以不使用而直接获得原始请求</font></font><code>express.bodyParser()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3525篇《使用Node.js和Express进行发布时如何访问请求正文？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我绝对不是JS和ES的新手，但似乎对我有用的就是：</font></font></p>

<pre><code>JSON.stringify(req.body)
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">让我知道它有什么问题！</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙西里</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您使用以下代码记录发布数据：</font></font></p>

<pre><code>router.post("/users",function(req,res){<font></font>
    res.send(JSON.stringify(req.body, null, 4));<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱小胖Mandy</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您足够懒惰以读取大块的发布数据。</font><font style="vertical-align: inherit;">您可以简单地将以下行粘贴以读取json。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以下是针对TypeScript的代码，也可以对JS进行类似操作。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">应用程序</font></font></strong></p>

<pre><code> import bodyParser from "body-parser";<font></font>
 // support application/json type post data<font></font>
 this.app.use(bodyParser.json());<font></font>
 // support application/x-www-form-urlencoded post data<font></font>
 this.app.use(bodyParser.urlencoded({ extended: false }));<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在收到POST呼叫的任何控制器之一中，如下所示</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">userController.ts</font></font></strong></p>

<pre><code> public async POSTUser(_req: Request, _res: Response) {<font></font>
   try {<font></font>
          const onRecord = &lt;UserModel&gt;_req.body;<font></font>
           /* Your business logic */<font></font>
           _res.status(201).send("User Created");<font></font>
        }<font></font>
    else{<font></font>
           _res.status(500).send("Server error");<font></font>
           }        <font></font>
   };<font></font>
</code></pre>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">_req.body应该将json数据解析为TS模型。</font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小卤蛋</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您声称已“尝试执行”的操作正是您在使用curl调用时按“预期”工作的代码中编写的内容。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您收到的错误似乎与您显示给我们的任何代码都不相关。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果要获取原始请求，请</font></font><code>request</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为</font></font><code>data</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>end</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件</font><font style="vertical-align: inherit;">设置处理程序</font><font style="vertical-align: inherit;">为开</font><font style="vertical-align: inherit;">（当然，还应删除的所有调用</font></font><code>express.bodyParser()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font><font style="vertical-align: inherit;">请注意，</font></font><code>data</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件将以块的形式发生，并且除非您为</font></font><code>data</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">事件</font><font style="vertical-align: inherit;">设置编码，否则</font><font style="vertical-align: inherit;">这些块将是缓冲区而不是字符串。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝梅神乐</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试这个：</font></font></p>

<pre><code>response.write(JSON.stringify(request.body));
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这将采用</font></font><code>bodyParser</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为您创建</font><font style="vertical-align: inherit;">的对象，</font><font style="vertical-align: inherit;">然后将其转换为字符串并将其写入响应。</font><font style="vertical-align: inherit;">如果您想要确切的请求正文（具有相同的空格等），则需要</font><font style="vertical-align: inherit;">在请求之前附加</font></font><code>data</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>end</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">侦听器，并逐块构建字符串，如在</font></font><a href="https://github.com/senchalabs/connect/blob/master/lib/middleware/json.js#L50" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">connect中从json解析源代码中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">看到的那样</font><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
