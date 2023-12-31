---
layout: question
title:  如何从Node.js调用Python函数
date:   2020-03-23T13:45:33.000Z
description: 我有一个Express Node.js应用程序，但我也有一个可以在Python中使用的机器学习算法。有没有一种方法可以从Node.js应用程序中调用Pyt...
img: 
author: 蛋蛋梅古一
category: question
answer: 3
tags: python Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个Express Node.js应用程序，但我也有一个可以在Python中使用的机器学习算法。</font><font style="vertical-align: inherit;">有没有一种方法可以从Node.js应用程序中调用Python函数来利用机器学习库的功能？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3092篇《如何从Node.js调用Python函数》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿Davaid</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以将自己的python进行</font></font><a href="https://github.com/QQuick/Transcrypt" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">转换</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，然后像调用JavaScript一样对其进行调用。</font><font style="vertical-align: inherit;">我为screeps成功地做到了这一点，甚至得到它在浏览器中运行的LA </font></font><a href="https://github.com/brython-dev/brython" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">brython</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，您可以使用支持Python和Javascript的RPC库，例如</font></font><a href="https://www.zerorpc.io/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zerorpc</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从他们的首页：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js客户端</font></font></p>

<pre><code>var zerorpc = require("zerorpc");<font></font>
<font></font>
var client = new zerorpc.Client();<font></font>
client.connect("tcp://127.0.0.1:4242");<font></font>
<font></font>
client.invoke("hello", "RPC", function(error, res, more) {<font></font>
    console.log(res);<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Python服务器</font></font></p>

<pre><code>import zerorpc<font></font>
<font></font>
class HelloRPC(object):<font></font>
    def hello(self, name):<font></font>
        return "Hello, %s" % name<font></font>
<font></font>
s = zerorpc.Server(HelloRPC())<font></font>
s.bind("tcp://0.0.0.0:4242")<font></font>
s.run()<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙蛋蛋</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在节点10和子进程上</font></font><code>1.0.2</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">来自python的数据是一个字节数组，必须进行转换。</font><font style="vertical-align: inherit;">这是在python中发出http请求的另一个快速示例。</font></font></p>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点</font></font></h3>

<pre><code>const process = spawn("python", ["services/request.py", "https://www.google.com"])<font></font>
<font></font>
return new Promise((resolve, reject) =&gt;{<font></font>
    process.stdout.on("data", data =&gt;{<font></font>
        resolve(data.toString()); // &lt;------------ by default converts to utf-8<font></font>
    })<font></font>
    process.stderr.on("data", reject)<font></font>
})<font></font>
</code></pre>

<h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">request.py</font></font></h3>

<pre><code>import urllib.request<font></font>
import sys<font></font>
<font></font>
def karl_morrison_is_a_pedant():   <font></font>
    response = urllib.request.urlopen(sys.argv[1])<font></font>
    html = response.read()<font></font>
    print(html)<font></font>
    sys.stdout.flush()<font></font>
<font></font>
karl_morrison_is_a_pedant()<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ps不是一个人为的例子，因为节点的http模块不会加载我需要发出的一些请求</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
