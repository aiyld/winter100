---
layout: question
title:  与Node.js一起使用哪个websocket库？\[关闭\]
date:   2020-03-17T09:04:46.000Z
description:                                                                          ...
img: 
author: 神无宝儿达蒙
category: question
answer: 2
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><aside class="s-notice s-notice__info js-post-notice mb16" aria-hidden="false" role="status">
            <div class="grid fd-column fw-nowrap"> 
                <div class="grid fw-nowrap">
                    <div class="grid--cell fl1 lh-lg">
                        <div class="grid--cell fl1 lh-lg">
                            <b><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关闭。</font></font></b><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个问题是</font></font><a href="/help/closed-questions"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">题外话</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它当前不接受答案。
                            
                        </font></font></div>
                    </div>
                </div>
                            </div>
                                <hr class="my12 outline-none baw0 bb bc-powder-2">
                <div class="grid fw-nowrap fc-black-600">
                        <div class="grid--cell mr8">
                            <svg aria-hidden="true" class="svg-icon iconLightbulb" width="18" height="18" viewBox="0 0 18 18"><path d="M9.5.5a.5.5 0 0 0-1 0v.25a.5.5 0 0 0 1 0V.5zm5.6 2.1a.5.5 0 0 0-.7-.7l-.25.25a.5.5 0 0 0 .7.7l.25-.25zM1 7.5c0-.28.22-.5.5-.5H2a.5.5 0 0 1 0 1h-.5a.5.5 0 0 1-.5-.5zm14.5 0c0-.28.22-.5.5-.5h.5a.5.5 0 0 1 0 1H16a.5.5 0 0 1-.5-.5zM2.9 1.9c.2-.2.5-.2.7 0l.25.25a.5.5 0 1 1-.7.7L2.9 2.6a.5.5 0 0 1 0-.7z" fill-opacity=".4"></path><path opacity=".4" d="M7 16h4v1a1 1 0 0 1-1 1H8a1 1 0 0 1-1-1v-1z" fill="#3F3F3F"></path><path d="M15 8a6 6 0 0 1-3.5 5.46V14a1 1 0 0 1-1 1h-3a1 1 0 0 1-1-1v-.54A6 6 0 1 1 15 8zm-4.15-3.85a.5.5 0 0 0-.7.7l2 2a.5.5 0 0 0 .7-.7l-2-2z" fill="#FFC166"></path></svg>
                        </div>
                    <div class="grid--cell lh-md">
                        <p class="mb0">
                            <b><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">想改善这个问题吗？</font></font></b> <a href="/posts/16392260/edit"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新问题</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，使其</font><font style="vertical-align: inherit;">成为Stack Overflow </font></font><a href="/help/on-topic"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的主题</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。
                        </font></font></p>
                        <p class="mb0 mt6"><font style="vertical-align: inherit;"></font><span title="2017-02-07 09：07：15Z" class="relativetime"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">3年前</font></font></span><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关闭</font><font style="vertical-align: inherit;">。</font></font></p>
                                                                                            </div>
                </div>
        </aside>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当前，有</font></font><a href="http://npmjs.org/keyword/websocket"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">大量</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于node.js </font><a href="http://npmjs.org/keyword/websocket"><font style="vertical-align: inherit;">的Websocket库</font></a><font style="vertical-align: inherit;">，最受欢迎的似乎是：</font></font></p>

<ul>
<li><a href="https://github.com/Worlize/WebSocket-Node"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/Worlize/WebSocket-Node</font></font></a></li>
<li><a href="https://github.com/einaros/ws"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/einaros/ws</font></font></a></li>
<li><a href="https://github.com/LearnBoost/engine.io"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/LearnBoost/engine.io</font></font></a></li>
<li><a href="https://github.com/learnboost/socket.io"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/learnboost/socket.io</font></font></a></li>
<li><a href="https://github.com/sockjs"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/sockjs</font></font></a></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是我找不到它们之间的任何可靠的具体比较……显然Socket.io很棒，但是已经过时并且构建失败。</font><font style="vertical-align: inherit;">ws和websocket-node都声称它们是最快的。</font><font style="vertical-align: inherit;">而且engine.io似乎是新的，但比轻巧的武器要重得多。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果我们或某人能够汇总一个答案，作为使用哪个套接字库以及何时使用以及它们之间的比较的指南，那将是惊人的。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1918篇《与Node.js一起使用哪个websocket库？\[关闭\]》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙神乐</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过这个</font></font><a href="https://meta.stackexchange.com/q/11740/149978"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">社区Wiki</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">答案获得成功。</font><font style="vertical-align: inherit;">随时</font><font style="vertical-align: inherit;">根据您的改进</font><font style="vertical-align: inherit;">来</font></font><a href="https://stackoverflow.com/posts/16393046/edit"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑我</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<ul>
<li><p><a href="https://github.com/einaros/ws" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ws</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
WebSocket服务器和node.js的客户端。</font><font style="vertical-align: inherit;">最快的库之一，即使不是最快的库。</font></font></p></li>
<li><p><a href="https://github.com/Worlize/WebSocket-Node" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">websocket-node</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
WebSocket服务器和node.js的客户端</font></font></p></li>
<li><p><a href="https://github.com/faye/websocket-driver-node" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">websocket-driver-node</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> WebSocket服务器和客户端协议解析器node.js-在faye-websocket-node中使用</font></font></p></li>
<li><p><a href="https://github.com/faye/faye-websocket-node" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">faye-websocket-node</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用于Node.js的WebSocket服务器和客户端-在faye和sockjs中使用</font></font></p></li>
<li><p><a href="https://github.com/learnboost/socket.io" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">socket.io</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
用于node.js的WebSocket服务器和客户端+用于浏览器的客户端+（v0具有最新到最旧的后备，Socket.io的v1使用engine.io）+通道-用于stack.io。</font><font style="vertical-align: inherit;">客户端库尝试在断开连接时重新连接。</font></font></p></li>
<li><p><a href="https://github.com/sockjs/sockjs-client" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">sockjs</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
WebSocket服务器和node.js等客户端和其他客户端+浏览器客户端+最新到最旧的后备</font></font></p></li>
<li><p><a href="http://faye.jcoglan.com/node.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">faye</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> WebSocket服务器和node.js等客户端和客户端+浏览器客户端+后备+支持其他服务器端语言</font></font></p></li>
<li><p><a href="https://deepstream.io/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">deepstream.io可集群</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实时服务器，处理WebSocket和TCP连接，并提供数据同步，发布/ </font><a href="https://deepstream.io/" rel="noreferrer"><font style="vertical-align: inherit;">订阅</font></a><font style="vertical-align: inherit;">和请求/响应</font></font></p></li>
<li><p><a href="https://github.com/topcloud/socketcluster" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">socketcluster</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> WebSocket服务器群集，它利用计算机上的所有CPU内核。</font><font style="vertical-align: inherit;">例如，如果您要使用具有32个内核的xlarge Amazon EC2实例，则您将能够处理单个实例几乎32倍的流量。</font></font></p></li>
<li><p><a href="https://github.com/primus/primus" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">primus</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为上述大多数库提供一个通用API，以实现所有库的轻松切换和稳定性改进。</font></font></p></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">何时使用：</font></font></p>

<ul>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当您要在客户端上使用本机WebSocket实现时，请使用基本的WebSocket服务器，请注意</font></font><a href="https://github.com/sockjs/sockjs-client#supported-transports-by-browser-html-served-from-http-or-https" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">浏览器不兼容</font></font></a></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在关注浏览器后备时使用后备库</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在关注频道时使用功能齐全的库</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当您不知道要使用什么时，可以使用primus；当由于项目需求变化或需要额外的连接稳定性而需要切换框架时，则不打算重写应用程序。</font></font></p></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在哪里测试：</font></font></p>

<p><a href="https://chrome.google.com/webstore/detail/firecamp/eajaahbjpnhghjcdaclbkeamlkepinbl" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Firecamp</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是针对SocketIO，WS和所有主要实时技术的GUI测试环境。</font><font style="vertical-align: inherit;">在开发实时事件时对其进行调试。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易神奇猪猪</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新：此后，由于提到的较新版本的库已发布，此答案已过时。</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Socket.IO v0.9已过时且有故障，而Engine.IO是其后继产品。</font><font style="vertical-align: inherit;">Socket.IO v1.0（即将发布）将使用Engine.IO，并且比v0.9更好。</font><font style="vertical-align: inherit;">我建议您使用Engine.IO，直到Socket.IO v1.0发布为止。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“ ws”不支持回退，因此，如果客户端浏览器不支持websockets，它将不起作用，这与Socket.IO和Engine.IO不同，后者在Websockets不可用时会使用长轮询等。</font><font style="vertical-align: inherit;">但是，“ ws”似乎是目前最快的库。</font></font></p>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参见我比较Socket.IO，Engine.IO和Primus的文章：</font><a href="https://medium.com/p/b63bfca0539"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> ://medium.com/p/b63bfca0539
  </font></font><a href="https://medium.com/p/b63bfca0539"><font style="vertical-align: inherit;"></font></a></p>
</blockquote></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
