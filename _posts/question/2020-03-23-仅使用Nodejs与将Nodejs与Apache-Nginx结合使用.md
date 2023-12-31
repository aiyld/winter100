---
layout: question
title:  仅使用Node.js与将Node.js与Apache / Nginx结合使用
date:   2020-03-23T03:43:55.000Z
description: 在哪种情况下，应该更喜欢只在实际部署中将Node.js用作服务器？当一个人不希望只使用Node.js的，有什么用Node.js的发挥更好？Apache...
img: 
author: 伽罗Gil
category: question
answer: 3
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在哪种情况下，应该更喜欢只在实际部署中将Node.js用作服务器？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当一个人</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望只使用Node.js的，有什么用Node.js的发挥更好？</font><font style="vertical-align: inherit;">Apache还是Nginx？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2745篇《仅使用Node.js与将Node.js与Apache / Nginx结合使用》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">古一逆天</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我相信，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只要您知道自己在做什么，就</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以在所有情况下使用Node服务静态文件</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">使用应用服务器来服务于静态文件无疑是一种新的范例，因为许多（每一个？）竞争技术（PHP，Ruby，Python等）都需要在应用服务器之前使用HTTPD或Nginx之类的Web服务器。 。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我曾经阅读过的反对使用Node服务静态文件的客观原因都围绕着使用您最了解的知识或使用经过更好测试/更稳定的知识的想法。</font><font style="vertical-align: inherit;">从实践上讲，这是非常有效的原因，但几乎没有技术上的相关性。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">除非您发现经典Web服务器无法使用Node所具有的功能（我怀疑您会做到），否则请选择您最了解的知识或希望使用的方法，因为这两种方法都很好。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">至于Nginx与Apache的关系，它们将与Node相同。</font><font style="vertical-align: inherit;">您应该比较它们而不考虑Node。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐Stafan卡卡西</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个额外的功能：如果您需要反向代理，例如在同一端口上执行Websocket服务器，或者混合使用某些技术（用NodeJS响应某些请求，用PHP响应某些其他请求，等等），这也很重要。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只是为了给pauljz的答案增加一个原因，我使用了前端服务器，这样当我重新启动后端服务器或由于某种原因崩溃时，它可以提供502个错误页面。</font><font style="vertical-align: inherit;">这使您的用户永远不会收到有关无法建立连接的错误。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
