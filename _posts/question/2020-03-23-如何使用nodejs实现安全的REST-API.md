---
layout: question
title:  如何使用node.js实现安全的REST API
date:   2020-03-23T07:22:50.000Z
description: I start planning a REST API with node.js ,express and mongodb. The API provid...
img: 
author: 达蒙阳光乐
category: question
answer: 5
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p>I start planning a REST API with node.js ,express and mongodb. The API provides data for a website (public and private area) and maybe later a mobile app. The frontend will be developed with AngularJS.</p>

<p>For some days I read a lot about securing REST APIs, but I don’t get to a final solution. As far as I understand is to use HTTPS to provide a basic security. But how I can protect the API in that use cases:</p>

<ul>
<li><p>Only visitors/users of  the website/app are allowed to get data for the public area of the website/app</p></li>
<li><p>Only authenticated and authorized users are allowed to get data for private area (and only data, where the user granted permissions)</p></li>
</ul>

<p>At the moment I think about to only allow users with a active session to use the API. To authorize the users I will use passport and for permission I need to implement something for myself. All on the top of HTTPS.</p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有人可以提供一些最佳实践或经验吗？</font><font style="vertical-align: inherit;">我的“体系结构”是否缺乏？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2906篇《如何使用node.js实现安全的REST API》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您想保护您的应用程序安全，</font></font><strong><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么绝对应该从使用HTTPS而不是HTTP开始</font></font></em></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这可以确保在您和用户之间创建安全的通道，从而防止嗅探来回发送给用户的数据并有助于保留数据。交换了机密。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用JWT（JSON Web令牌）来保护RESTful API</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，与服务器端会话相比，这有很多好处，主要包括：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">1-更具可扩展性，因为您的API服务器将不必为每个用户维护会话（当您有很多会话时，这可能是一个沉重的负担）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">2-JWT是自包含的，并且具有定义用户角色的声明，例如，他可以在日期和到期日访问和发布的内容（此日期之后，JWT将无效）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">3-更易于处理负载均衡器，并且如果您有多个API服务器，因为您不必共享会话数据，也无需配置服务器将会话路由到同一服务器，那么只要JWT的请求碰到任何服务器，就可以对其进行身份验证和授权</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">4-减轻了数据库负担，也不必为每个请求不断存储和检索会话ID和数据</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">5-如果您使用强键对JWT进行签名，则JWT不会被篡改，因此您可以信任随请求一起发送的JWT中的声明，而无需检查用户会话以及他是否被授权，您只需检查JWT，然后就可以知道该用户可以执行的操作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">许多库提供了使用大多数编程语言创建和验证JWT的简便方法，例如：在node.js中，最受欢迎的一种是</font></font><a href="https://www.npmjs.com/package/jsonwebtoken" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">jsonwebtoken</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于REST API通常旨在使服务器保持无状态，因此JWT与该概念更加兼容，因为每个请求都是使用自包含</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（JWT）的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">授权令牌发送的，</font><font style="vertical-align: inherit;">而与服务器会话相比，服务器不必跟踪用户会话服务器是有状态的，以便记住用户及其角色，但是，会话也被广泛使用并具有其优点，您可以根据需要进行搜索。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">需要注意的重要一件事是，您必须使用HTTPS将JWT安全地交付给客户端，并将其保存在安全的地方（例如，本地存储中）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以</font><a href="https://jwt.io/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">从此链接</font></a><font style="vertical-align: inherit;">了解有关JWT的更多信息。</font></font><a href="https://jwt.io/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我遇到了与您描述的问题相同的问题。</font><font style="vertical-align: inherit;">我正在建立的网站可以通过手机和浏览器访问，因此我需要一个API来允许用户注册，登录和执行某些特定任务。</font><font style="vertical-align: inherit;">此外，我需要支持可伸缩性，同一代码运行在不同的进程/机器上。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">由于用户可以创建资源（也称为POST / PUT操作），因此需要保护api。</font><font style="vertical-align: inherit;">您可以使用oauth或构建自己的解决方案，但请记住，如果密码很容易发现，则所有解决方案都可能被破坏。</font><font style="vertical-align: inherit;">基本思想是使用用户名，密码和令牌（即apitoken）对用户进行身份验证。</font><font style="vertical-align: inherit;">可以使用</font></font><a href="https://github.com/broofa/node-uuid" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node-uuid</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生成此apitoken，</font><font style="vertical-align: inherit;">并可以使用</font><a href="http://nodejs.org/api/crypto.html#crypto_crypto_pbkdf2_password_salt_iterations_keylen_callback" rel="noreferrer"><font style="vertical-align: inherit;">pbkdf2</font></a><font style="vertical-align: inherit;">哈希密码</font></font><a href="http://nodejs.org/api/crypto.html#crypto_crypto_pbkdf2_password_salt_iterations_keylen_callback" rel="noreferrer"><font style="vertical-align: inherit;"></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您需要将会话保存在某个地方。</font><font style="vertical-align: inherit;">如果将其保存在一个普通对象的内存中，如果您杀死服务器并再次重新启动它，则会话将被破坏。</font><font style="vertical-align: inherit;">同样，这是不可扩展的。</font><font style="vertical-align: inherit;">如果使用haproxy在计算机之间进行负载平衡，或者仅使用worker，则此会话状态将存储在单个进程中，因此，如果将同一用户重定向到另一个进程/计算机，则需要再次进行身份验证。</font><font style="vertical-align: inherit;">因此，您需要将会话存储在一个公共位置。</font><font style="vertical-align: inherit;">通常使用redis完成此操作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">验证用户身份（用户名+密码+ apitoken）后，为会话生成另一个令牌，也称为accesstoken。</font><font style="vertical-align: inherit;">同样，使用node-uuid。</font><font style="vertical-align: inherit;">向用户发送访问令牌和用户标识。</font><font style="vertical-align: inherit;">用户ID（密钥）和访问令牌（值）存储在redis中并带有到期时间，例如1h。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，每次用户使用rest api进行任何操作时，都需要发送userid和accesstoken。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您允许用户使用其余的api注册，则需要使用admin apitoken创建一个管理员帐户并将其存储在移动应用中（加密用户名+密码+ apitoken），因为新用户在以下情况下将没有apitoken他们注册。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">网络上也使用此api，但您无需使用apitokens。</font><font style="vertical-align: inherit;">您可以对redis存储区使用express，也可以使用与上述相同的技术，但是绕过apitoken检查并向用户返回cookie中的userid + accesstoken。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您有私人区域，则在验证用户名时将其与允许的用户进行比较。</font><font style="vertical-align: inherit;">您还可以将角色应用于用户。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">摘要：</font></font></p>

<p><img src="https://i.stack.imgur.com/Kbttf.png" alt="顺序图"></p>

<p>An alternative without apitoken would be to use HTTPS and to send the username and password in the Authorization header and cache the username in redis.</p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Itachi</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您希望Web应用程序具有完全锁定的区域，而该区域只能由公司的管理员访问，则可以为您提供SSL授权。</font><font style="vertical-align: inherit;">这将确保没有人可以连接到服务器实例，除非他们在浏览器中安装了授权证书。</font><font style="vertical-align: inherit;">上周，我写了一篇有关如何设置服务器的</font><a href="https://gist.github.com/ExxKA/5169211" rel="nofollow"><font style="vertical-align: inherit;">文章</font></a><font style="vertical-align: inherit;">：</font></font><a href="https://gist.github.com/ExxKA/5169211" rel="nofollow"><font style="vertical-align: inherit;"></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是您将找到的最安全的设置之一，因为其中不涉及用户名/密码，因此除非您的用户之一将密钥文件交给潜在的黑客，否则任何人都无法获得访问权限。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关于SO的REST身份验证模式有很多问题。</font><font style="vertical-align: inherit;">这些与您的问题最相关：</font></font></p>

<ul>
<li><a href="https://stackoverflow.com/questions/9119648/securing-my-node-js-apps-rest-api"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">保护我的Node.js应用程序的REST API？</font></font></a></li>
<li><a href="https://stackoverflow.com/questions/319530/restful-authentication"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">RESTful身份验证</font></font></a></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本上，您需要选择使用API​​密钥（最不安全，因为密钥可能被未经授权的用户发现），应用程序密钥和令牌组合（中）或完整的OAuth实施（最安全）之间进行选择。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯西里</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我刚刚完成了一个示例应用程序，该应用程序以一种非常基本但清晰的方式进行了此操作。</font><font style="vertical-align: inherit;">它使用mongoose和mongodb来存储用户和护照以进行身份​​验证管理。  </font></font></p>

<p><a href="https://github.com/Khelldar/Angular-Express-Train-Seed"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/Khelldar/Angular-Express-Train-Seed</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
