---
layout: question
title:  如何在Node.js Web应用程序中管理MongoDB连接？
date:   2020-03-19T04:33:47.000Z
description: 我在MongoDB中使用node-mongodb-native驱动程序来编写网站。我对如何管理连接有一些疑问：仅使用一个MongoDB连接就可以...
img: 
author: 猴子Itachi
category: question
answer: 5
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在</font><font style="vertical-align: inherit;">MongoDB中</font><font style="vertical-align: inherit;">使用</font></font><a href="https://github.com/mongodb/node-mongodb-native" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node-mongodb-native</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">驱动程序来编写网站。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我对如何管理连接有一些疑问：</font></font></p>

<ol>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅使用一个MongoDB连接就可以处理所有请求是否足够？</font><font style="vertical-align: inherit;">有性能问题吗？</font><font style="vertical-align: inherit;">如果没有，是否可以设置全局连接以在整个应用程序中使用？</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果不是，请问在请求到达时打开一个新连接，并在处理请求时将其关闭，这会很好吗？</font><font style="vertical-align: inherit;">打开和关闭连接是否昂贵？</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我应该使用全局连接池吗？</font><font style="vertical-align: inherit;">我听说驱动程序具有本地连接池。</font><font style="vertical-align: inherit;">这是一个好选择吗？</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果使用连接池，应使用多少个连接？</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还有其他我应该注意的事情吗？</font></font></p></li>
</ol></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2361篇《如何在Node.js Web应用程序中管理MongoDB连接？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony梅</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><a href="http://mongoosejs.com/docs/api.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://mongoosejs.com/docs/api.html</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">查看猫鼬的来源。</font><font style="vertical-align: inherit;">他们打开一个连接并将其绑定到Model对象，因此当需要Model Object时，将与数据库建立连接。</font><font style="vertical-align: inherit;">驱动程序负责连接池。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西里古一</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您应该将连接创建为服务，然后在需要时重用它。</font></font></p>

<pre><code>// db.service.js<font></font>
import { MongoClient } from "mongodb";<font></font>
import database from "../config/database";<font></font>
<font></font>
const dbService = {<font></font>
  db: undefined,<font></font>
  connect: callback =&gt; {<font></font>
    MongoClient.connect(database.uri, function(err, data) {<font></font>
      if (err) {<font></font>
        MongoClient.close();<font></font>
        callback(err);<font></font>
      }<font></font>
      dbService.db = data;<font></font>
      console.log("Connected to database");<font></font>
      callback(null);<font></font>
    });<font></font>
  }<font></font>
};<font></font>
<font></font>
export default dbService;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的App.js示例</font></font></p>

<pre><code>// App Start<font></font>
dbService.connect(err =&gt; {<font></font>
  if (err) {<font></font>
    console.log("Error: ", err);<font></font>
    process.exit(1);<font></font>
  }<font></font>
<font></font>
  server.listen(config.port, () =&gt; {<font></font>
    console.log(`Api runnning at ${config.port}`);<font></font>
  });<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并在任何需要的地方使用</font></font></p>

<pre><code>import dbService from "db.service.js"<font></font>
const db = dbService.db<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅番长</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我一直在我的应用程序中使用带有Redis连接的通用池-我强烈推荐它。</font><font style="vertical-align: inherit;">它是通用的，我当然知道它可以与mysql一起使用，所以我认为您和mongo不会遇到任何问题</font></font></p>

<p><a href="https://github.com/coopernurse/node-pool" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/coopernurse/node-pool</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐Jim</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您拥有Express.js，则可以使用</font></font><a href="https://github.com/floatdrop/express-mongo-db" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">express-mongo-db</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在没有池的情况下在请求之间缓存和共享MongoDB连接（因为接受的答案说这是共享连接的正确方法）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果不是，您可以查看其源代码并在另一个框架中使用它。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">ALEYHarry</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><a href="https://groups.google.com/d/msg/node-mongodb-native/mSGnnuG8C1o/Hiaqvdu1bWoJ" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node-mongodb-native的主要提交者说</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您的应用程序启动并重新使用db对象时，只需打开一次do MongoClient.connect。</font><font style="vertical-align: inherit;">每个.connect都不是一个单例连接池。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，要直接回答您的问题，请</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重复使用产生的db对象</font></font><a href="http://mongodb.github.io/node-mongodb-native/driver-articles/mongoclient.html#mongoclient-connect" rel="nofollow noreferrer"><code>MongoClient.connect()</code></a></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">与每个数据库操作上的打开/关闭连接相比，这可以为您提供缓冲，并可以显着提高速度。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
