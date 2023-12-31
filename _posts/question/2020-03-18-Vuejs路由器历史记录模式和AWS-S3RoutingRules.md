---
layout: question
title:  Vue.js路由器：历史记录模式和AWS S3（RoutingRules）
date:   2020-03-18T11:14:12.000Z
description: 我有一个Vue.js应用程序，并与Amazon S3和Cloudflare一起运行。当我打开索引并浏览到/ dashboard时，一切正常。但是，当我...
img: 
author: A神无Harry
category: question
answer: 4
tags: 亚马逊S3 Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个Vue.js应用程序，并与Amazon S3和Cloudflare一起运行。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我打开索引并浏览到/ dashboard时，一切正常。</font><font style="vertical-align: inherit;">但是，当我直接在新标签页中打开仪表板之类的路线或刷新页面时，我从S3返回以下错误：</font></font></p>

<pre><code>404 Not Found<font></font>
<font></font>
Code: NoSuchKey<font></font>
Message: The specified key does not exist.<font></font>
Key: unternehmen<font></font>
RequestId: 6514F8A1F4C29235<font></font>
HostId: +BVrPLJSGdzSYogzWZ4GMBXkgkdSJWRVJVhcSs4EI/lmMUR422aCtCxpBGU6AMe5VkS1UbEn/Lc=<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需阅读一下问题就是Vue.js历史记录模式：</font><a href="https://router.vuejs.org/de/essentials/history-mode.html" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> ://router.vuejs.org/de/essentials/history-mode.html</font></font><a href="https://router.vuejs.org/de/essentials/history-mode.html" rel="noreferrer"><font style="vertical-align: inherit;"></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想用Amazon S3存储桶中的路由规则解决问题。</font><font style="vertical-align: inherit;">Apache RewriteRule如何查找S3？</font></font></p>

<pre><code>&lt;IfModule mod_rewrite.c&gt;<font></font>
  RewriteEngine On<font></font>
  RewriteBase /<font></font>
  RewriteRule ^index\.html$ - [L]<font></font>
  RewriteCond %{REQUEST_FILENAME} !-f<font></font>
  RewriteCond %{REQUEST_FILENAME} !-d<font></font>
  RewriteRule . /index.html [L]<font></font>
&lt;/IfModule&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试了以下操作，但不起作用：</font></font></p>

<pre><code>&lt;RoutingRules&gt;<font></font>
  &lt;RoutingRule&gt;<font></font>
    &lt;Condition&gt;<font></font>
      &lt;HttpErrorCodeReturnedEquals&gt;404&lt;/HttpErrorCodeReturnedEquals&gt;<font></font>
    &lt;/Condition&gt;<font></font>
    &lt;Redirect&gt;<font></font>
      &lt;HostName&gt;domain.com&lt;/HostName&gt;<font></font>
      &lt;ReplaceKeyWith&gt;index.html&lt;/ReplaceKeyWith&gt;<font></font>
    &lt;/Redirect&gt;<font></font>
  &lt;/RoutingRule&gt;<font></font>
&lt;/RoutingRules&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果我那样做，我只会渲染我的页眉和页脚，仅此而已。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谢谢！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2174篇《Vue.js路由器：历史记录模式和AWS S3（RoutingRules）》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝神奇</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您在AWS S3上使用静态托管，并且这是SPA应用程序（React，Vue，Angular等），则应将index.html设置为错误页面：
</font></font><a href="https://i.stack.imgur.com/A9Zhs.png" rel="nofollow noreferrer"><img src="https://i.stack.imgur.com/A9Zhs.png" alt="在此处输入图片说明"></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯卡卡西</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我知道这个答案来得很晚，但是如果其他人正在云中寻找其他方法来解决这个问题，则无需在s3上创建自定义页面，当找不到页面时会重定向用户。</font><font style="vertical-align: inherit;">代替这样做，可以在cloudfront中为分发创建自定义错误响应。</font></font></p>

<p><a href="https://i.stack.imgur.com/8l6Be.png" rel="noreferrer"><img src="https://i.stack.imgur.com/8l6Be.png" alt="自定义错误"></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>/index.html</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">找不到文件，</font><font style="vertical-align: inherit;">它将始终重定向到</font><font style="vertical-align: inherit;">，</font><font style="vertical-align: inherit;">这将</font><font style="vertical-align: inherit;">触发应用程序路由。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁AJinJin</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用“静态网站托管”托管S3中Vue中制作的静态PWA，它可以按预期工作。</font><font style="vertical-align: inherit;">我所做的非常简单-我添加了以下内容：</font></font></p>

<pre><code>&lt;RoutingRules&gt;<font></font>
  &lt;RoutingRule&gt;<font></font>
    &lt;Condition&gt;<font></font>
      &lt;HttpErrorCodeReturnedEquals&gt;403&lt;/HttpErrorCodeReturnedEquals&gt;<font></font>
    &lt;/Condition&gt;<font></font>
    &lt;Redirect&gt;<font></font>
      &lt;ReplaceKeyWith&gt;&lt;/ReplaceKeyWith&gt;<font></font>
    &lt;/Redirect&gt;<font></font>
  &lt;/RoutingRule&gt;<font></font>
&lt;/RoutingRules&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">S3存储桶的属性。</font><font style="vertical-align: inherit;">见下图：
</font></font><a href="https://i.stack.imgur.com/P8GqK.png" rel="nofollow noreferrer"><img src="https://i.stack.imgur.com/P8GqK.png" alt="S3属性"></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于我的S3存储桶，每次尝试访问不存在的文件时，您都会收到403（禁止访问）而不是404。这就是为什么我将HttpErrorCodeReturnedEquals更改为403的原因。我还用替换了ReplaceKeyWith一个空字符串，如“ index.html”，表示未触发正确的路由。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望对您有所帮助。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">干杯，亚历克斯</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐米亚</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在历史记录模式下进行路由而不使用CloudFront的一种方法是创建您的URI指向的文件。</font><font style="vertical-align: inherit;">因此，假设您使用index.html作为入口点，并且只有另一个页面提供了page2.html路径。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您应该调整构建和部署过程以执行以下操作：</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将您的资源构建到生产发行版中（例如，使用</font></font><code>npm run build</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确保为路由器链接按路径创建一个文件，该文件是原始文件的副本。</font><font style="vertical-align: inherit;">在本例中，我提到它将创建“ dist / index.html”到“ dist / page2.html”的副本</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将dist文件夹内容复制到S3存储桶</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意，步骤1和2的顺序很重要。</font><font style="vertical-align: inherit;">这可以通过发布您的网站的脚本轻松完成。</font><font style="vertical-align: inherit;">我刚刚将这种方法用于想要的结果。</font><font style="vertical-align: inherit;">允许刷新页面并在新标签页中打开链接。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我看到的缺点是：-存储文件副本的开销-必须确保是否添加页面，不要忘记更新构建和部署脚本。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
