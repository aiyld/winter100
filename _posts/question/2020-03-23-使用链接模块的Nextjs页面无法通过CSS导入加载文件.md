---
layout: question
title:  使用链接模块的Next.js页面无法通过CSS导入加载文件
date:   2020-03-23T13:04:29.000Z
description: 我正在将next.js（7.0.2）添加到现有项目中，无法弄清楚为什么Link模块不加载具有的页面import 'style.css'。我遵循了\` z...
img: 
author: 老丝阿飞
category: question
answer: 0
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在将next.js（7.0.2）添加到现有项目中，无法弄清楚为什么Link模块不加载具有的页面</font></font><code>import 'style.css'</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我遵循了</font></font><a href="https://github.com/zeit/next-plugins/tree/master/packages/next-css" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@ zeit / next-css</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指令以及</font></font><a href="https://nextjs.org/learn/basics/server-side-support-for-clean-urls/create-a-custom-server" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Next.js / Express</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">集成。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我安装了以下软件包</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">下一个7.0.2</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">@ zeit / next-css </font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">css-loader@1.0.1</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快报（v4）</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">next.config.js</font></font></p>

<pre><code>    // ./next.config.js file<font></font>
    const withCSS = require('@zeit/next-css')<font></font>
    module.exports = withCSS() <font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">index.js</font></font></p>

<pre><code>    // ./pages/index.js file<font></font>
    import Link from 'next/link'<font></font>
    const Index = () =&gt; (<font></font>
      &lt;div&gt;<font></font>
        &lt;p&gt;Hello Next.js&lt;/p&gt;<font></font>
        &lt;p&gt;<font></font>
          &lt;Link href="/test"&gt;&lt;a&gt;test&lt;/a&gt;&lt;/Link&gt;<font></font>
        &lt;/p&gt;<font></font>
      &lt;/div&gt;<font></font>
    )<font></font>
<font></font>
    export default Index<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">test.js</font></font></p>

<pre><code>    // ./pages/test.js file<font></font>
    import "../style.css"<font></font>
    export default () =&gt; &lt;div className="example"&gt;Hello World!&lt;/div&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">style.css </font></font></p>

<pre><code>    // ./style.css file<font></font>
      .example {<font></font>
        font-size: 50px;<font></font>
      }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">预期的行为：链接模块将使用CSS加载页面，就像加载其他页面一样。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实际行为：除具有的页面外，所有页面都将加载</font></font><code>import 'my.css'</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">我可以直接通过网址加载该页面。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">EG- </font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作品=加载</font></font><a href="http://localhost:3000/index" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http：// localhost：3000 / index</font></font></a></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Works =加载</font></font><a href="http://localhost:3000/test" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http：// localhost：3000 / test</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（并应用CSS）</font></font></li>
<li>Does NOT work = Load <a href="http://localhost:3000/index" rel="noreferrer">http://localhost:3000/index</a> and click the test link.  Nothing happens.  If I go to the Network tab on the Developer Tools (Chrome) I see test.js listed and the initiator is page-loader.js. This seems to be followed by a series of on-demand-entries-ping?page=/ but not sure what it means.</li>
</ol>

<p>Update: If I comment out the <code>import "../style.css"</code> the file loads (without CSS).  So it seems there is something in the css processing with server side routing that isn't right with my setup.</p>

<p>@Darryl - here are the relevant snippets from my express initialization file.  The entire file can be found (current iteration) at <a href="https://github.com/tagyoureit/nodejs-poolController/blob/6.0-DEV/src/lib/comms/server.js#L33" rel="noreferrer">https://github.com/tagyoureit/nodejs-poolController/blob/6.0-DEV/src/lib/comms/server.js#L33</a>.</p>

<pre><code>  function startServerAsync(type) {<font></font>
    ...<font></font>
    const _next = require('next')<font></font>
    const dev = process.env.NODE_ENV !== 'production'<font></font>
    ...<font></font>
    // servers is an object that holds http/https/socketio/mdns and other servers<font></font>
    // type='http' in current testing<font></font>
    servers[type].next = _next({ dev }) <font></font>
    servers[type].next.prepare()<font></font>
      .then(() =&gt; {<font></font>
        servers[type].app = express();<font></font>
        servers[type].server = <font></font>
        container.http.createServer(servers[type].app);<font></font>
        configExpressServer(servers[type].app, express, servers[type].next);<font></font>
        servers[type].server = servers[type].server.listen(servers[type].port, function () {<font></font>
        container.logger.verbose('Express Server ' + type + ' listening at port %d', servers[type].port);<font></font>
        container.io.init(servers[type].server, type)<font></font>
            resolve('Server ' + type + ' started.');<font></font>
      });<font></font>
    }<font></font>
<font></font>
    // assign static/api routes<font></font>
    function configExpressServer(app, express, _next) {<font></font>
      // use next as router<font></font>
      const handle = _next.getRequestHandler()<font></font>
<font></font>
      // many app.get / app.use statements<font></font>
      ...<font></font>
      // catch all to route through next<font></font>
      app.get('*', (req, res) =&gt; {<font></font>
        const { parse } = require('url')<font></font>
        const parsedUrl = parse(req.url, true)<font></font>
        const { pathname, query } = parsedUrl<font></font>
        handle(req, res, parsedUrl)<font></font>
      })<font></font>
  }<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3041篇《使用链接模块的Next.js页面无法通过CSS导入加载文件》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
