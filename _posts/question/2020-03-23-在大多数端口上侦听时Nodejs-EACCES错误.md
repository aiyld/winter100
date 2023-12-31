---
layout: question
title:  在大多数端口上侦听时，Node.js EACCES错误
date:   2020-03-23T01:19:09.000Z
description: 我正在测试一个应用程序（希望可以在heroku上运行，但是在本地也有问题）。它在运行http.Server.listen（）时给我一个EACCES错误-但...
img: 
author: 凯米亚
category: question
answer: 11
tags: http Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在测试一个应用程序（希望可以在heroku上运行，但是在本地也有问题）。</font><font style="vertical-align: inherit;">它在运行http.Server.listen（）时给我一个EACCES错误-但它仅在某些端口上发生。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，我正在本地运行：</font></font></p>

<pre><code>joe@joebuntu:~$ node<font></font>
&gt; var h = require('http').createServer();<font></font>
&gt; h.listen(900);<font></font>
Error: EACCES, Permission denied<font></font>
    at Server._doListen (net.js:1062:5)<font></font>
    at net.js:1033:14<font></font>
    at Object.lookup (dns.js:132:45)<font></font>
    at Server.listen (net.js:1027:20)<font></font>
    at [object Context]:1:3<font></font>
    at Interface.&lt;anonymous&gt; (repl.js:150:22)<font></font>
    at Interface.emit (events.js:42:17)<font></font>
    at Interface._onLine (readline.js:132:10)<font></font>
    at Interface._line (readline.js:387:8)<font></font>
    at Interface._ttyWrite (readline.js:564:14)<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在900端口（或我尝试过的其他20个端口中的任何一个）上没有任何运行，因此这应该可以工作。</font><font style="vertical-align: inherit;">奇怪的是它</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确实</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在某些端口</font><strong><font style="vertical-align: inherit;">上</font></strong><font style="vertical-align: inherit;">工作。</font><font style="vertical-align: inherit;">例如，端口3000可以正常工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是什么原因造成的？  </font></font></p>

<h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新1：</font></font></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我发现在我的本地计算机上，EACCES错误来了，因为我必须以root用户身份运行节点才能绑定到这些特定端口。</font><font style="vertical-align: inherit;">我不知道为什么会这样，但是使用sudo可以解决。</font><font style="vertical-align: inherit;">但是，这并不能解释我将如何在Heroku上修复它。</font><font style="vertical-align: inherit;">无法在Heroku上以root用户身份运行，那么如何在80端口监听？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2580篇《在大多数端口上侦听时，Node.js EACCES错误》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在尝试了许多不同的方法之后，在我的Windows上重新安装IIS解决了该问题。 </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长猴子</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">仅通过更改server.js中的端口号即可解决我的错误 </font></font></p>

<pre><code>const port = process.env.PORT || 8085;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我将端口号从8080更改为8085。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望能帮助到你。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">LGil</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试authbind：</font></font></p>

<p><a href="http://manpages.ubuntu.com/manpages/hardy/man1/authbind.1.html" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://manpages.ubuntu.com/manpages/hardy/man1/authbind.1.html</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装后，可以在以下文件夹中添加要使用端口号的文件：/ etc / authbind / byport /</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用chmod授予它500个权限，并将所有权更改为您要在其下运行程序的用户。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之后，以您的项目中的该用户身份执行“ authbind node ...”。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙Tom</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在Mac上收到此错误，因为默认情况下，它使用与节点服务器使用的端口相同的端口来运行apache服务器，在我的情况下，端口是端口80。我要做的就是用 </font></font><code>sudo apachectl stop</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望这对某人有帮助。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的Mac上也出现了此错误。</font><font style="vertical-align: inherit;">我使用</font></font><code>npm run dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行在Windows中我的应用程序的NodeJS和它工作正常。</font><font style="vertical-align: inherit;">但是我的mac-上出现了此错误</font></font><code>error given was: Error: bind EACCES null:80</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">解决此问题的一种方法是使用root用户访问权限运行它。</font><font style="vertical-align: inherit;">您可能会使用</font></font><code>sudo npm run dev</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且需要输入密码。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通常最好在非特权端口（例如3000）上为您的应用程序提供服务，该端口无需root权限即可工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参考：</font></font><a href="https://stackoverflow.com/questions/23281895/node-js-eacces-error-when-listening-on-http-80-port-permission-denied"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在HTTP 80端口上侦听时，Node.js EACCES错误（权限被拒绝）</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您尝试本地托管的端口被转发，则会发生这种情况</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小胖</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请记住，如果您使用sudo绑定到端口80，并且正在使用env变量PORT＆NODE_ENV，则必须重新导出这些var，因为您现在位于根配置文件而非用户配置文件下。</font><font style="vertical-align: inherit;">因此，要使其在我的Mac上运行，我做了以下工作：</font></font></p>

<pre><code>sudo su<font></font>
export NODE_ENV=production<font></font>
export PORT=80<font></font>
docpad run<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的天啊！！</font><font style="vertical-align: inherit;">在我的情况下，我</font></font><code>....listen(ip, port)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不是</font><font style="vertical-align: inherit;">这样做，</font><font style="vertical-align: inherit;">而是</font></font><code>...listen(port, ip)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">抛出错误味精：</font></font><code>Error: listen EACCES localhost</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我使用的端口号&gt; = 3000，甚至尝试使用管理员访问权限。</font><font style="vertical-align: inherit;">什么都没解决。</font><font style="vertical-align: inherit;">然后仔细观察，我注意到了这个问题。</font><font style="vertical-align: inherit;">更改为</font></font><code>...listen(port, ip)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，一切开始正常！</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只是大声说出来，以防它对其他人有用...</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长猴子</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这意味着节点无法在定义的端口上侦听。</font><font style="vertical-align: inherit;">将其更改为1234或2000或3000，然后重新启动服务器。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p>Check this <a href="https://www.digitalocean.com/community/tutorials/how-to-use-pm2-to-setup-a-node-js-production-environment-on-an-ubuntu-vps#give-safe-user-permission-to-use-port-80" rel="noreferrer">reference link</a>:</p>

<blockquote>
  <p>Give Safe User Permission To Use Port 80</p>
  
  <p>Remember, we do NOT want to run your applications as the root user,
  but there is a hitch: your safe user does not have permission to use
  the default HTTP port (80). You goal is to be able to publish a
  website that visitors can use by navigating to an easy to use URL like
  <code>http://ip:port/</code></p>
  
  <p>Unfortunately, unless you sign on as root, you’ll normally have to use
  a URL like <code>http://ip:port</code> - where port number &gt; 1024.</p>
  
  <p>A lot of people get stuck here, but the solution is easy. There a few
  options but this is the one I like. Type the following commands:</p>

<pre><code>sudo apt-get install libcap2-bin<font></font>
sudo setcap cap_net_bind_service=+ep `readlink -f \`which node\``<font></font>
</code></pre>
  
  <p>Now, when you tell a Node application that you want it to run on port
  80, it will not complain.</p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙猪猪</span>
            <span class="discuss-time">2020.03.23</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">非特权用户（非root用户）无法在1024以下的端口上打开侦听套接字。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
