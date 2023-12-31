---
layout: question
title:  password.js RESTful身份验证
date:   2020-03-24T10:11:18.000Z
description: 如何使用RESTful API（而不是通过Web界面）使用passport.js处理身份验证（例如本地和Facebook）？与使用典型的res.sen...
img: 
author: 梅猿
category: question
answer: 2
tags: Node.js的 Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用RESTful API（而不是通过Web界面）使用passport.js处理身份验证（例如本地和Facebook）？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与使用典型的res.send（{data：req.data}）相比，要处理从回调到RESTful响应（JSON）的数据传递，设置初始的/ login端点以重定向到Facebook（/ login不能是通过AJAX访问，因为它不是JSON响应-它是通过​​回调重定向到Facebook的）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经找到</font></font><a href="https://github.com/halrobertson/test-restify-passport-facebook"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/halrobertson/test-restify-passport-facebook</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但是我很难理解。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，passport.js如何存储身份验证凭据？</font><font style="vertical-align: inherit;">服务器（或者它是服务？）由MongoDB支持，我希望凭据（pw的登录名和盐化哈希值）存储在此处，但是我不知道passport.js是否具有这种功能。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3622篇《password.js RESTful身份验证》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村L</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我非常感谢@Miguel在每种情况下的完整流程说明，但我想在Facebook身份验证部分添加一些内容。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Facebook提供了一个</font></font><a href="https://developers.facebook.com/docs/facebook-login/getting-started-web/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Javascript SDK</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，您可以使用它直接在客户端上获取访问令牌，然后将其传递到服务器，并用于进一步从Facebook中提取所有用户信息。</font><font style="vertical-align: inherit;">因此，您基本上不需要任何重定向。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此外，您也可以为移动应用程序使用相同的API端点。</font><font style="vertical-align: inherit;">只需使用用于Facebook的Android / iOS SDK，在客户端上获取Facebook access_token并将其传递给服务器即可。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关于</font><font style="vertical-align: inherit;">所说明</font><font style="vertical-align: inherit;">的</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无状态性质</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，当使用get_access_token生成令牌并传递给客户端时，此令牌也存储在服务器上。</font><font style="vertical-align: inherit;">所以它和会话令牌一样好，我相信这使它有状态吗？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就是我的两分钱 </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">JinJin小宇宙</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我发现这是一篇很棒的文章，可以帮助您进行身份验证：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">脸书</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">推特</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谷歌</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本地认证</font></font></li>
</ul>

<p><a href="https://scotch.io/tutorials/easy-node-authentication-setup-and-local" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简易节点身份验证：设置和本地</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
