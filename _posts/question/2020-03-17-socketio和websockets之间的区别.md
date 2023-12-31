---
layout: question
title:  socket.io和websockets之间的区别
date:   2020-03-17T09:00:17.000Z
description: node.js中的socket.io和websockets有什么区别？它们都是服务器推送技术吗？我唯一感到的是socket.io允许我通过指定事件...
img: 
author: 神乐Green
category: question
answer: 5
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node.js中的socket.io和websockets有什么区别？</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
它们都是服务器推送技术吗？</font><font style="vertical-align: inherit;">我唯一感到的是</font></font></p>

<ol>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">socket.io允许我通过指定事件名称来发送/发送消息。</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于socket.io，来自服务器的消息将到达所有客户端，但是对于websockets中的消息，我被迫保留所有连接的数组并循环遍历，以将消息发送给所有客户端。</font></font></p></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，我想知道为什么Web检查器（例如Chrome / firebug / fiddler）无法从服务器捕获这些消息（来自socket.io/websocket）？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请澄清一下。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1914篇《socket.io和websockets之间的区别》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">L十三</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">即使现代的浏览器现在支持WebSockets，我也认为没有必要丢弃SocketIO，并且它在当今的任何项目中仍然占有一席之地。</font><font style="vertical-align: inherit;">这很容易理解，而且个人而言，由于SocketIO，我了解了WebSockets的工作方式。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如本主题所述，有许多用于Angular，React等的集成库以及用于TypeScript和其他编程语言的定义类型。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我要添加到Socket.io和WebSockets之间的区别的另一点是，使用Socket.io进行群集并不是什么大问题。</font><font style="vertical-align: inherit;">Socket.io提供</font><font style="vertical-align: inherit;">了可用于将其与Redis链接以增强可伸缩性的</font></font><a href="https://socket.io/docs/using-multiple-nodes/#passing-events-between-nodes" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">适配器</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">例如，您有</font></font><a href="https://github.com/luin/ioredis" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ioredis</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://github.com/socketio/socket.io-redis" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">socket.io-redis</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是的，我知道，</font></font><a href="https://github.com/SocketCluster/socketcluster" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SocketCluster</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">存在，但这是题外话。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">HarryItachi</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Socket.IO使用WebSocket，当WebSocket不可用时，使用后备算法进行实时连接。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">前端古一</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用Socket.IO基本上类似于使用jQuery-您想要支持旧版浏览器，需要编写更少的代码，并且该库将提供后备功能。</font><font style="vertical-align: inherit;">Socket.io使用websockets技术（如果可用），如果不可用，则检查可用的最佳通信类型并使用它。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙Tom</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我将提供一个反对使用socket.io的论点。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为仅使用socket.io是因为它具有后备并不是一个好主意。</font><font style="vertical-align: inherit;">让IE8 RIP。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">过去，在许多情况下，新版本的NodeJS破坏了socket.io。</font><font style="vertical-align: inherit;">您可以查看这些列表中的示例... </font></font><a href="https://github.com/socketio/socket.io/issues?q=install+error"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/socketio/socket.io/issues?q=install+error</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您要开发一个Android应用程序或需要与现有应用程序一起使用的东西，则可能马上就可以使用WS，socket.io可能会给您带来一些麻烦...</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">再加上Node.JS的WS模块非常易于使用。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小十三</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它的优点是，它简化了如＃2中所述的WebSockets的使用，并且可能更重要的是，如果浏览器或服务器上不支持WebSockets，它可以将故障转移到其他协议。</font><font style="vertical-align: inherit;">我将避免直接使用WebSocket，除非您非常熟悉WebSockets在什么环境下不起作用，并且您能够解决这些限制。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这对WebSockets和Socket.IO都是不错的阅读。</font></font></p>

<p><a href="http://davidwalsh.name/websocket" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://davidwalsh.name/websocket</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
