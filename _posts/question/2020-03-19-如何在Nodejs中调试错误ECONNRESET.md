---
layout: question
title:  如何在Node.js中调试错误ECONNRESET？
date:   2020-03-19T04:32:40.000Z
description: 我正在使用Socket.io运行Express.js应用程序用于聊天Web应用程序，并且在24小时内大约5次随机收到以下错误。节点进程将被永久封装，并立即...
img: 
author: LGil
category: question
answer: 9
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用Socket.io运行Express.js应用程序用于聊天Web应用程序，并且在24小时内大约5次随机收到以下错误。</font><font style="vertical-align: inherit;">节点进程将被永久封装，并立即重新启动。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题是重新启动Express将我的用户踢出他们的房间，没人希望这样做。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Web服务器由HAProxy代理。</font><font style="vertical-align: inherit;">仅使用websockets和flashsockets传输就没有套接字稳定性问题。</font><font style="vertical-align: inherit;">我无法有意复制此内容。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是Node的错误</font></font><code>v0.10.11</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>    events.js:72<font></font>
            throw er; // Unhandled 'error' event<font></font>
                  ^<font></font>
    Error: read ECONNRESET     //alternatively it s a 'write'<font></font>
        at errnoException (net.js:900:11)<font></font>
        at TCP.onread (net.js:555:19)<font></font>
    error: Forever detected script exited with code: 8<font></font>
    error: Forever restarting script for 2 time<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑（2013-07-22）</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">添加了socket.io客户端错误处理程序和未捕获的异常处理程序。</font><font style="vertical-align: inherit;">似乎此错误捕获了：</font></font></p>

<pre><code>    process.on('uncaughtException', function (err) {<font></font>
      console.error(err.stack);<font></font>
      console.log("Node NOT Exiting...");<font></font>
    });<font></font>
</code></pre>

<p>So I suspect it's not a Socket.io issue but an HTTP request to another server 
that I do or a MySQL/Redis connection. The problem is that the error stack 
doesn't help me identify my code issue. Here is the log output:</p>

<pre><code>    Error: read ECONNRESET<font></font>
        at errnoException (net.js:900:11)<font></font>
        at TCP.onread (net.js:555:19)<font></font>
</code></pre>

<p>How do I know what causes this? How do I get more out of the error?</p>

<p>Ok, not very verbose but here's the stacktrace with Longjohn:</p>

<pre><code>    Exception caught: Error ECONNRESET<font></font>
    { [Error: read ECONNRESET]<font></font>
      code: 'ECONNRESET',<font></font>
      errno: 'ECONNRESET',<font></font>
      syscall: 'read',<font></font>
      __cached_trace__:<font></font>
       [ { receiver: [Object],<font></font>
           fun: [Function: errnoException],<font></font>
           pos: 22930 },<font></font>
         { receiver: [Object], fun: [Function: onread], pos: 14545 },<font></font>
         {},<font></font>
         { receiver: [Object],<font></font>
           fun: [Function: fireErrorCallbacks],<font></font>
           pos: 11672 },<font></font>
         { receiver: [Object], fun: [Function], pos: 12329 },<font></font>
         { receiver: [Object], fun: [Function: onread], pos: 14536 } ],<font></font>
      __previous__:<font></font>
       { [Error]<font></font>
         id: 1061835,<font></font>
         location: 'fireErrorCallbacks (net.js:439)',<font></font>
         __location__: 'process.nextTick',<font></font>
         __previous__: null,<font></font>
         __trace_count__: 1,<font></font>
         __cached_trace__: [ [Object], [Object], [Object] ] } }<font></font>
</code></pre>

<p>Here I serve the flash socket policy file:</p>

<pre><code>    net = require("net")<font></font>
    net.createServer( (socket) =&gt;<font></font>
      socket.write("&lt;?xml version=\"1.0\"?&gt;\n")<font></font>
      socket.write("&lt;!DOCTYPE cross-domain-policy SYSTEM \"http://www.macromedia.com/xml/dtds/cross-domain-policy.dtd\"&gt;\n")<font></font>
      socket.write("&lt;cross-domain-policy&gt;\n")<font></font>
      socket.write("&lt;allow-access-from domain=\"*\" to-ports=\"*\"/&gt;\n")<font></font>
      socket.write("&lt;/cross-domain-policy&gt;\n")<font></font>
      socket.end()<font></font>
    ).listen(843)<font></font>
</code></pre>

<p>Can this be the cause?</p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2360篇《如何在Node.js中调试错误ECONNRESET？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">飞云A小宇宙</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我遇到了同样的问题，看来Node.js版本就是问题所在。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我安装了以前版本的Node.js（10.14.2），使用nvm一切正常（允许您安装Node.js的多个版本，并迅速从一个版本切换到另一个版本）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这不是一个“干净”的解决方案，但可以为您提供临时服务。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">EvaDavaid</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我只需</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">连接到另一个网络</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就解决了这个问题</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">那是可能的问题之一。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如上所述，</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ECONNRESET</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">表示TCP会话突然关闭了其连接的末端。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您的互联网连接可能会阻止您连接到某些服务器。</font><font style="vertical-align: inherit;">就我而言，我试图连接到mLab（托管MongoDB数据库的云数据库服务）。</font><font style="vertical-align: inherit;">而且我的ISP阻止了它。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">ProDavaid</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经通过以下方法解决了这个问题：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关闭我的wifi /以太网连接，然后再打开。 </font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我</font></font><code>npm update</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在终端</font><font style="vertical-align: inherit;">输入：</font><font style="vertical-align: inherit;">更新npm。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我尝试从会话中注销并再次登录</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在那之后，我尝试了相同的npm命令，好在它解决了。</font><font style="vertical-align: inherit;">我不确定是否那么简单。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用CENTOS 7</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">A番长</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我也遇到了这个错误，经过几天的调试和分析，我能够解决它：</font></font></p>

<h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的解决方案</font></font></h1>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我来说，VirtualBox（对于Docker）是个问题。</font><font style="vertical-align: inherit;">我在VM上配置了端口转发，并且该错误仅在转发的端口上发生。</font></font></p>

<h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一般结论</font></font></h1>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以下观察结果可能会节省您不得不投资的工作时间：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我来说，问题仅发生在一个端口上从本地主机到本地主机的连接上。</font><font style="vertical-align: inherit;">-&gt;检查更改任何这些常数即可解决问题。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我来说，问题仅发生在我的机器上-&gt;让其他人尝试一下。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我来说，该问题仅在一段时间后发生，无法可靠地重现</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的问题无法用任何节点或表达（调试）工具进行检查。</font><font style="vertical-align: inherit;">-&gt;不要在此浪费时间</font></font></li>
</ul>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-&gt;弄清您的网络（设置）是否混乱，例如VM，防火墙等，这可能是问题的原因。</font></font></strong></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚L</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在开发过程中也遇到ECONNRESET错误，解决问题的方法是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用nodemon来启动服务器，而只是使用</font></font><code>"node server.js"</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">启动服务器来解决问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很奇怪，但是对我有用，现在我再也看不到ECONNRESET错误。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长小胖</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">今天遇到了同样的问题。</font><font style="vertical-align: inherit;">经过研究，我发现了一个非常有用的</font></font><a href="https://nodejs.org/api/cli.html#cli_abort_on_uncaught_exception" rel="noreferrer"><code>--abort-on-uncaught-exception</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node.js选项</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它不仅提供了更多详细和有用的错误堆栈跟踪，而且还保存了应用程序崩溃时的核心文件，允许进一步调试。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Sam小哥逆天</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我用于提供Flash策略文件的一个简单的TCP服务器导致了此问题。</font><font style="vertical-align: inherit;">我现在可以使用处理程序来捕获错误：</font></font></p>

<pre><code># serving the flash policy file<font></font>
net = require("net")<font></font>
<font></font>
net.createServer((socket) =&gt;<font></font>
  //just added<font></font>
  socket.on("error", (err) =&gt;<font></font>
    console.log("Caught flash policy server socket error: ")<font></font>
    console.log(err.stack)<font></font>
  )<font></font>
<font></font>
  socket.write("&lt;?xml version=\"1.0\"?&gt;\n")<font></font>
  socket.write("&lt;!DOCTYPE cross-domain-policy SYSTEM \"http://www.macromedia.com/xml/dtds/cross-domain-policy.dtd\"&gt;\n")<font></font>
  socket.write("&lt;cross-domain-policy&gt;\n")<font></font>
  socket.write("&lt;allow-access-from domain=\"*\" to-ports=\"*\"/&gt;\n")<font></font>
  socket.write("&lt;/cross-domain-policy&gt;\n")<font></font>
  socket.end()<font></font>
).listen(843)<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomGO</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一种可能的情况（但很少见）可能是您具有服务器到服务器的通信并且设置</font></font><code>server.maxConnections</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为非常低的值。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在节点的核心库</font></font><a href="https://github.com/nodejs/node/blob/c9b59e8387b08dab20936f32d2b290804718f688/lib/net.js#L1432-L1435" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">net.js中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它将调用</font></font><code>clientHandle.close()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这也会导致错误ECONNRESET：</font></font></p>

<pre><code>if (self.maxConnections &amp;&amp; self._connections &gt;= self.maxConnections) {<font></font>
  clientHandle.close(); // causes ECONNRESET on the other end<font></font>
  return;<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神奇Tony古一</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我遇到了同样的问题，但通过放置以下内容缓解了它：</font></font></p>

<pre><code>server.timeout = 0;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之前</font></font><code>server.listen</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><code>server</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是这里的HTTP服务器。</font><font style="vertical-align: inherit;">根据</font></font><a href="http://nodejs.org/api/http.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">API文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，默认超时为2分钟</font><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
