---
layout: question
title:  我可以用Node.js替换Apache吗？
date:   2020-03-26T08:49:29.000Z
description: 我有一个使用常见嫌疑犯（Apache，MySQL和PHP）在CentOS上运行的网站。自从该网站最初启动以来，它已经发展了很多，现在我想用它做更奇妙的事情...
img: 
author: 小宇宙
category: question
answer: 5
tags: apache Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个使用常见嫌疑犯（Apache，MySQL和PHP）在CentOS上运行的网站。</font><font style="vertical-align: inherit;">自从该网站最初启动以来，它已经发展了很多，现在我想用它做更奇妙的事情-即实时通知。</font><font style="vertical-align: inherit;">根据我的阅读，Apache处理得很差。</font><font style="vertical-align: inherit;">我想知道是否可以仅用Node.js替换Apache（所以不是“ </font></font><a href="http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LAMP</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ”，而是“ LNMP”）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我尝试过在线搜索解决方案，但没有找到解决方案。</font><font style="vertical-align: inherit;">如果我正确地解释了我已经读过的东西，似乎大多数人都在说Node.js可以同时取代Apache和PHP。</font><font style="vertical-align: inherit;">不过，我有很多现有的PHP代码，因此我希望保留它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果还不很清楚，我会很困惑，可以使用一些启示。</font><font style="vertical-align: inherit;">非常感谢！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3783篇《我可以用Node.js替换Apache吗？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Harry乐Harry</span>
            <span class="discuss-time">2020.03.26</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如今，它的LAMP对MEAN。</font><font style="vertical-align: inherit;">要进行直接比较，请参见</font></font><a href="http://tamas.io/what-is-the-mean-stack" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://tamas.io/what-is-the-mean-stack</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当然，M，E和A有所变化。</font><font style="vertical-align: inherit;">例如，最近的</font></font><a href="https://github.com/koajs/koa" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Koa</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能会取代（E）xpress。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，仅用Node.js替换Apache可能不是使Web堆栈现代化的正确方法。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan番长</span>
            <span class="discuss-time">2020.03.26</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我相信Node.js是Web服务的未来，但是如果您有很多现有的PHP代码，那么Apache / MySQL是您的最佳选择。</font><font style="vertical-align: inherit;">可以将Apache配置为代理对Node.js的请求，或者将Node.js代理对Apache的请求，但是我认为这两种情况都会降低性能，尤其是在第一种情况下。</font><font style="vertical-align: inherit;">不过，如果您没有运行一个流量很高的网站，那也没什么大不了的。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我刚刚注册了stackoverflow，现在还无法评论已接受的答案，但是今天我创建了一个简单的Node.js脚本，该脚本实际上使用sendfile（）通过HTTP协议提供文件。</font><font style="vertical-align: inherit;">（接受的答案链接到的现有示例仅使用裸TCP协议发送文件，而我找不到HTTP的示例，因此我自己编写了该示例。）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所以我认为有人可能会觉得这很有用。</font><font style="vertical-align: inherit;">通过sendfile（）操作系统调用提供文件的速度不一定比通过“用户土地”复制数据时更快，但是最终却减少了对CPU和RAM的利用，因此与传统方式相比，它能够处理更多的连接。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">链接：</font><a href="https://gist.github.com/1350901" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;">：</font></font><a href="https://gist.github.com/1350901" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//gist.github.com/1350901</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy</span>
            <span class="discuss-time">2020.03.26</span>
          </div>
          <div class="discuss-comment"><p><a href="https://stackoverflow.com/questions/4641632/node-js-running-alongside-apache-php"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之前的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> SO帖子准确描述了我在说什么（php + socket.io +节点）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为您可以使用socket.io在somehost：8000上建立节点服务器，并将socket.io客户端代码拍打成标签，并且只需最少的工作就可以使您现有的应用与socket.io（实时宝贝）一起摇摇欲坠。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">虽然节点可以是您唯一的后端服务器，但请记住该节点喜欢辜负它的名称并成为一个节点。</font><font style="vertical-align: inherit;">不久前，我查看了Ryan Dahl给PHP用户小组的一次谈话，他提到了名称节点，该名称节点涉及到多个节点进程在工作并相互交谈的愿景。  </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱</span>
            <span class="discuss-time">2020.03.26</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js的事件/非阻塞架构可能会比Apache更快，但是您可能无法找到替代某些Apache功能的模块/库。 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js本身是一个轻量级的低级框架，使您能够相对快速地构建Web应用程序的服务器端内容和实时部分，但是Apache提供了更广泛的配置选项和面向“经典” Web服务器的功能。 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我要说的是，除非您想用基于node.js的Web应用程序框架（例如express.js）替换PHP，否则您应该留在Apache上（或者，如果遇到性能问题，请考虑迁移到Nginx）。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LJinJin</span>
            <span class="discuss-time">2020.03.26</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您准备使用JavaScript重新编写PHP，那么可以，Node.js可以替换您的Apache。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果在服务器和客户端之间放置以反向代理模式运行的Apache或NGINX实例，则可以处理Node.js上的JavaScript中的某些请求以及Apache托管的PHP中的某些请求，直到可以完全替换所有PHP。使用JavaScript代码。</font><font style="vertical-align: inherit;">这可能是一个快乐的媒介：您的WebSockets是否可以在Node.js中工作，而平常的工作是否可以在Apache + PHP中工作。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
