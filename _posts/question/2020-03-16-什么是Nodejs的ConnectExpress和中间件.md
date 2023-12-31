---
layout: question
title:  什么是Node.js的Connect，Express和“中间件”？
date:   2020-03-16T03:19:34.000Z
description: 尽管非常了解JavaScript，但我对Node.js生态系统中的这三个项目的确切用途感到困惑。像Rails的架子吗？有人可以解释一下吗？...
img: 
author: 伽罗Pro
category: question
answer: 7
tags: Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管非常了解JavaScript，但我对</font><font style="vertical-align: inherit;">Node.js生态系统中的这三个项目的</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确切</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用途</font><font style="vertical-align: inherit;">感到困惑</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">像Rails的架子吗？</font><font style="vertical-align: inherit;">有人可以解释一下吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1691篇《什么是Node.js的Connect，Express和“中间件”？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅樱</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中间件顾名思义，中间件实际上位于中间之间。中间是什么？</font><font style="vertical-align: inherit;">请求和响应的中间.. </font><font style="vertical-align: inherit;">
在此图片中</font></font><a href="https://i.stack.imgur.com/98HUh.png" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，请求，响应，快速服务器如何位于快速应用程序</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中，您可以看到请求是来自客户端的，然后快速服务器将为那些请求提供服务。这样，整个快递服务器的整个任务就变成了小的单独任务。
</font></font><a href="https://i.stack.imgur.com/Q0tG1.png" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中间件如何位于请求和响应之间</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">小服务器部分执行某项特定任务并将请求传递给下一个..最终完成了所有任务的响应。所有中间件都可以访问请求对象，响应对象和请求的下一个功能响应周期</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是在中间件Express </font><a href="https://www.youtube.com/watch?v=iBkOz9WLZRM&amp;t=543s" rel="nofollow noreferrer"><font style="vertical-align: inherit;">youtube视频中</font></a><font style="vertical-align: inherit;">解释中间件的好例子</font></font><a href="https://www.youtube.com/watch?v=iBkOz9WLZRM&amp;t=543s" rel="nofollow noreferrer"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">杜大爷</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">愚蠢的简单答案</font></font></h1>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Connect和Express是Node.js的Web服务器。</font><font style="vertical-align: inherit;">与Apache和IIS不同，它们都可以使用相同的模块，称为“中间件”。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">SamGreen十三</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相关信息，尤其是在使用NTVS与Visual Studio IDE配合使用时。</font><font style="vertical-align: inherit;">NTVS在Visual Studio 2012、2013中添加了NodeJS和Express工具，脚手架，项目模板。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，调用ExpressJS或Connect作为“ WebServer”的语言不正确。</font><font style="vertical-align: inherit;">您可以创建带有或不带有它们的基本WebServer。</font><font style="vertical-align: inherit;">基本的NodeJS程序也可以使用http模块来处理http请求，从而成为基本的Web服务器。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖古一</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><code>Node.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本身提供了一个HTTP模块，其</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">createServer</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法返回一个可用于响应HTTP请求的对象。</font><font style="vertical-align: inherit;">该对象继承了</font></font><code>http.Server</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">原型。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西达蒙西里</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Connect为常见的HTTP服务器功能（例如会话管理，身份验证，日志记录等）提供了“更高级别”的API。</font><font style="vertical-align: inherit;">Express是在具有高级（类似于Sinatra）功能的Connect之上构建的。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙JinJinHarry</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node.js</font></font></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js是服务器端的JavaScript引擎。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
除了所有js功能之外，它还包括联网功能（如HTTP）和对文件系统的访问。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
这与客户端js不同，在客户端js中，网络任务由浏览器垄断，并且出于安全原因，禁止访问文件系统。  </font></font></p>

<h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为网络服务器的nod​​e.js：表达</font></font></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在服务器中运行的东西可以理解HTTP，并且可以访问文件，就像Web服务器一样。</font><font style="vertical-align: inherit;">但这不是一个。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
为了使node.js像Web服务器一样工作，必须对其进行编程：处理传入的HTTP请求并提供适当的响应。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
Express就是这样做的：这是js中Web服务器的实现。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
因此，实现网站就像配置Express路由，并对网站的特定功能进行编程一样。  </font></font></p>

<h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中间件和连接</font></font></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">服务页面涉及许多任务。</font><font style="vertical-align: inherit;">这些任务中的许多是众所周知的且非常常见，因此节点的</font></font><a href="http://www.senchalabs.org/connect/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Connect</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块（可在节点下运行的许多模块之一）实现了这些任务。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
查看当前令人印象深刻的产品：</font></font></p>

<ul>
<li><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">           具有自定义格式支持的</font><strong><font style="vertical-align: inherit;">记录器</font></strong><font style="vertical-align: inherit;">请求记录器</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">csrf</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">              跨站点请求伪造保护</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">压缩</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">          Gzip压缩中间件</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">basicAuth</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">         基本的http认证</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">bodyParser</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">        可扩展请求主体解析器</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">json</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">              应用程序/ json解析器</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">urlencoded</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">        应用程序/ x-www-form-urlencoded解析器</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">多</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">         部分</font><strong><font style="vertical-align: inherit;">多</font></strong><font style="vertical-align: inherit;">部分/表单数据解析器</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">超时</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">           请求超时</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">cookieParser</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">      cookie解析器</font></font></li>
<li><strong><font style="vertical-align: inherit;"></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">          捆绑的MemoryStore支持</font><strong><font style="vertical-align: inherit;">会话</font></strong><font style="vertical-align: inherit;">会话管理</font></font></li>
<li><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">cookieSession</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">     基于cookie的会话支持</font></font></li>
<li><strong>methodOverride</strong>   faux HTTP method support</li>
<li><strong>responseTime</strong>     calculates response-time and exposes via X-Response-Time</li>
<li><strong>staticCache</strong>      memory cache layer for the static() middleware</li>
<li><strong>static</strong>           streaming static file server supporting Range and more</li>
<li><strong>directory</strong>        directory listing middleware</li>
<li><strong>vhost</strong>            virtual host sub-domain mapping middleware</li>
<li><strong>favicon</strong>          efficient favicon server (with default icon)</li>
<li><strong>limit</strong>            limit the bytesize of request bodies</li>
<li><strong>query</strong>            automatic querystring parser, populating req.query</li>
<li><strong>errorHandler</strong>     flexible error handler</li>
</ul>

<p>Connect is the framework and through it you can pick the (sub)modules you need.<br>
The <a href="https://github.com/senchalabs/connect/wiki" rel="noreferrer">Contrib Middleware</a> page enumerates a long list of additional <em>middlewares</em>.<br>
Express itself comes with the most common Connect middlewares.  </p>

<h2>What to do?</h2>

<p>Install node.js.<br>
Node comes with <em>npm</em>, the <em>node package manager</em>.<br>
The command <code>npm install -g express</code> will download and install express globally (check the <a href="http://expressjs.com/guide.html" rel="noreferrer">express guide</a>).<br>
Running <code>express foo</code> in a command line (not in node) will create a ready-to-run application named foo. Change to its (newly created) directory and run it with node with the command <code>node &lt;appname&gt;</code>, then open <code>http://localhost:3000</code> and see.
Now you are in. </p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">A小胖</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">[ </font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从4.0版本开始，Express不再使用Connect。</font><font style="vertical-align: inherit;">但是，Express仍与为Connect编写的中间件兼容。</font><font style="vertical-align: inherit;">我的原始答案如下。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我很高兴您提出这个问题，因为对于那些关注Node.js的人们来说，这无疑是一个常见的困惑点。</font><font style="vertical-align: inherit;">这是我最好的解释：</font></font></p>

<ul>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js本身提供了一个</font></font><a href="http://nodejs.org/docs/v0.4.2/api/all.html#hTTP" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模块，该模块的</font></font><code>createServer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法返回一个对象，您可以使用该对象来响应HTTP请求。</font><font style="vertical-align: inherit;">该对象继承了</font></font><code>http.Server</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">原型。</font></font></p></li>
<li><p><a href="http://senchalabs.github.com/connect/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Connect</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还提供了一种</font></font><code>createServer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法，该方法返回继承了扩展版本的对象</font></font><code>http.Server</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">Connect的扩展主要用于简化</font></font><a href="https://github.com/senchalabs/connect/wiki" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中间件的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">插入</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这就是为什么Connect将自己描述为“中间件框架”的原因，并且通常类似于Ruby的Rack。</font></font></p></li>
<li><p><a href="http://expressjs.com/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Express</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确实做到了Connect对http模块所做的连接：它提供了</font></font><code>createServer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一种扩展Connect </font></font><code>Server</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">原型的方法。</font><font style="vertical-align: inherit;">因此，这里提供了Connect的所有功能，</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以及</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">视图渲染和用于描述路线的便捷DSL。</font><font style="vertical-align: inherit;">Ruby的Sinatra是一个很好的类比。</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后还有其他框架可以扩展Express！</font><font style="vertical-align: inherit;">例如</font></font><a href="https://github.com/mauricemach/zappa" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Zappa</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它集成了对CoffeeScript，服务器端jQuery和测试的支持。</font></font></p></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是“中间件”含义的具体示例：开箱即用，以上都不为您提供静态文件。</font><font style="vertical-align: inherit;">但是，只需</font></font><code>connect.static</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">插入（配置为Connect附带的中间件），该中间件配置为指向目录，您的服务器即可提供对该目录中文件的访问。</font><font style="vertical-align: inherit;">请注意，Express还提供了Connect的中间件。</font></font><code>express.static</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与相同</font></font><code>connect.static</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">（两者都被称为</font></font><code>staticProvider</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">直到最近。）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的印象是，如今，大多数“真正的” Node.js应用都是使用Express开发的。</font><font style="vertical-align: inherit;">它添加的功能非常有用，并且如果需要，所有较低级别的功能仍然存在。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
