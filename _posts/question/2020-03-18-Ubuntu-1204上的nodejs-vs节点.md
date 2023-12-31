---
layout: question
title:  Ubuntu 12.04上的nodejs vs节点
date:   2020-03-18T07:22:06.000Z
description: 我从这里给出的说明在Ubuntu上安装了Node.js当我node --version在终端上写时，我看到了：-bash  /usr/sbin/no...
img: 
author: 阿飞Tony
category: question
answer: 19
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我从</font><a href="https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager#ubuntu-mint"><font style="vertical-align: inherit;">这里</font></a><font style="vertical-align: inherit;">给出的说明在Ubuntu上安装了Node.js</font></font><a href="https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager#ubuntu-mint"><font style="vertical-align: inherit;"></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我</font></font><code>node --version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在终端上</font><font style="vertical-align: inherit;">写</font><font style="vertical-align: inherit;">时，我看到了：</font></font><br>
<code>-bash: /usr/sbin/node: No such file or directory</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我可以在</font></font><code>/usr/sbin/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">目录中</font><font style="vertical-align: inherit;">看到节点</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">写作</font></font><code>npm --version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">表演</font></font><code>1.3.5</code> <br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
写作</font></font><code>nodejs --version</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">表演</font></font><code>v0.10.15</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，我可以在</font></font><code>/usr/bin/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">目录中</font><font style="vertical-align: inherit;">看到节点</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么，我该如何</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">工作？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，如果我使用</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">zsh</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不是bash，则</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令有效。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2004篇《Ubuntu 12.04上的nodejs vs节点》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GO梅逆天</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><strong><em><a href="https://nodejs.org/en/download/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://nodejs.org/en/download/</font></font></a></em></strong>  </p>

<pre><code>Download .pkg file on your mac and install it. it directly works.<font></font>
<font></font>
➜  ~ which node<font></font>
/usr/local/bin/node<font></font>
➜  ~ node --version<font></font>
v10.11.0<font></font>
➜  ~ which npm<font></font>
/usr/local/bin/npm<font></font>
➜  ~ npm --version<font></font>
6.4.1<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阳光Tom逆天</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">删除现有的node和nodejs是可选的，但是必须另选安装最新的7.x nodejs。</font></font></p>

<pre><code>curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -<font></font>
sudo apt-get install -y nodejs<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚卡卡西</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只需使用NVM（节点版本管理器）-https: 
 </font></font><a href="https://github.com/creationix/nvm" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/creationix/nvm</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它已成为管理Node.js的标准。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当您需要新版本时：</font></font></p>

<pre><code>nvm install NEW_VER<font></font>
nvm use XXX<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果出现问题，您可以随时返回</font></font></p>

<pre><code>nvm use OLD_VER
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">逆天小哥蛋蛋</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以执行以下命令来启用nodejs：</font></font></p>

<pre><code>scl enable rh-nodejs8 bash
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：检查您的节点版本。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">资料来源：</font></font></strong>
<font style="vertical-align: inherit;"><a href="https://developers.redhat.com/products/softwarecollections/hello-world/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https </font></a><strong><font style="vertical-align: inherit;">: </font></strong></font><a href="https://developers.redhat.com/products/softwarecollections/hello-world/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//developers.redhat.com/products/softwarecollections/hello-world/</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐逆天</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对绝对的初学者会有所帮助</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管您已找到答案，但只想指出该</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令（不带任何参数）将以REPL </font></font><sub><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">read-eval-print-loop</font></font></sub><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模式</font><font style="vertical-align: inherit;">启动节点</font><font style="vertical-align: inherit;">以执行原始javascript代码。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令的</font><font style="vertical-align: inherit;">另一种方法</font><font style="vertical-align: inherit;">是通过提供</font></font><code>js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件作为参数。</font><font style="vertical-align: inherit;">这就是我们主要使用它的方式。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无前端</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我遇到了同样的问题，符号链接帮助了我：sudo ln -s / usr / bin / nodejs / usr / bin / node之后sudo npm install -g phantomjs-prebuilt</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">顺利进行</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无伽罗阳光</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最好的安装nodejs的方法是通过NVM（节点版本管理器）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">删除以前的版本： </font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ sudo apt-get清除节点</font></font></pre>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ sudo apt自动删除</font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">还删除</font></font><code>$ sudo rm -rf node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">包含该文件夹的目录中的</font><font style="vertical-align: inherit;">所有node_modules </font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node和Nodejs在技术上是同一回事。</font><font style="vertical-align: inherit;">只是名称改变了。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先安装或更新nvm </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以root身份运行 </font></font></p><pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ sudo su </font></font></pre><p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后</font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.7/install.sh | </font><font style="vertical-align: inherit;">重击</font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要么 </font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.31.7/install.sh | </font><font style="vertical-align: inherit;">重击</font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查NVM到路径 </font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ source〜/ .profile</font></font></pre>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ nvm ls-remote</font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您收到有关列表的错误，请安装git。</font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ sudo apt-get安装git</font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">重新运行： </font></font></p>

<p></p><pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ nvm ls-remote</font></font></pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">  要么 </font></font><pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ sudo nvm ls-remote</font></font></pre><p></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">$ nvm安装版本，您需要 </font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检查版本</font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">＃node --version</font></font></pre> 

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nvm使用您需要的版本</font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">信息来源： </font></font></p><pre><a href="https://www.digitalocean.com/community/tutorials/how-to-install-node-js-with-nvm-node-version-manager-on-a-vps" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://www.digitalocean.com/community/tutorials/how-to-install-node-js-with-nvm-node-version-manager-on-a-vps</font></font></a></pre><p></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Stafan逆天前端</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我创建了一个符号链接，但是仍然无法正常工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我忘记重启终端（腻子连接）。</font><font style="vertical-align: inherit;">在我没有符号链接的情况下工作:)</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋L西里</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您在运行Ubuntu实例的AWS EC2实例上（在Ubuntu 16.x上进行了测试），那么以下步骤可能对您有用：</font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">    sudo apt-get更新</font></font><font></font><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
    sudo apt-get --purge删除节点-y</font></font><font></font><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
    sudo apt-get --purge删除nodejs -y</font></font><font></font><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
    sudo apt-get --purge删除legacy-node -y</font></font><font></font><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
    须藤rm / usr / bin / node</font></font><font></font><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
    curl -sL https://deb.nodesource.com/setup_6.x | </font><font style="vertical-align: inherit;">须藤bash-</font></font><font></font><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
    须藤apt-get install nodejs -y</font></font><font></font><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
    节点-v</font></font><font></font>
</pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果一切正确，则最后一条命令的输出应为：v6.xx</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果没有，请运行以下命令：</font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">    须藤ln -s / usr / bin / nodejs / usr / bin / node
</font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望这会有所帮助。</font><font style="vertical-align: inherit;">它神奇地帮助了我（呵呵）。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长A</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这对我有用：</font></font></p>

<pre><code>alias node=nodejs
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">按照</font></font><a href="https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-an-ubuntu-14-04-server" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">链接中</font><font style="vertical-align: inherit;">的说明进行操作之后</font><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西樱</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">答案较晚，但需要最新信息...</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您使用</font></font><a href="https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">node github安装自述文件中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的荐用方法安装node.js </font><font style="vertical-align: inherit;">，则建议按照</font></font><a href="https://nodesource.com/blog/nodejs-v012-iojs-and-the-nodesource-linux-repositories"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nodesource博客文章</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上的说明进行操作</font><font style="vertical-align: inherit;">，而不是从过时的apt-get repo安装，node.js应该使用以下</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令</font><font style="vertical-align: inherit;">运行</font><font style="vertical-align: inherit;">：以及</font></font><code>nodejs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令，而无需进行新的符号链接。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本文中的方法是：</font></font></p>

<pre class="lang-bash prettyprint-override"><code># Note the new setup script name for Node.js v0.12<font></font>
curl -sL https://deb.nodesource.com/setup_0.12 | sudo bash -<font></font>
<font></font>
# Then install with:<font></font>
sudo apt-get install -y nodejs<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意，这是针对v0.12的，在不久的将来它可能会变得过时。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，如果您像我一样在公司代理后面，则需要在sudo命令中添加-E选项，以保留代理所需的env var：</font></font></p>

<p><code>curl -sL https://deb.nodesource.com/setup_0.12 | sudo -E bash -</code></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">凯Near</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用来自</font></font><a href="https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nodejs网站</font></font></a></strong><font style="vertical-align: inherit;"><strong><font style="vertical-align: inherit;">的官方说明</font></strong><font style="vertical-align: inherit;">：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于v7：</font></font></p>

<pre><code>curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -<font></font>
sudo apt-get install -y nodejs<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于v6：</font></font></p>

<pre><code>curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -<font></font>
sudo apt-get install -y nodejs<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于v4：</font></font></p>

<pre><code>curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -<font></font>
sudo apt-get install -y nodejs<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经从Windows bash（通过Linux-14.04子系统）和raspbian（基于ARM Debian）进行了测试。</font><font style="vertical-align: inherit;">在</font></font><code>sudo apt-get install -y nodejs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有先运行安装脚本的情况下运行将导致您获得节点0.10。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您打算安装需要构建的本机npm模块，请运行：</font></font></p>

<pre><code>sudo apt install -y build-essential
</code></pre>

<p><sup><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：这是所有体系结构中任何基于Debian的发行版的推荐路径。</font></font></sup></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易猴子Pro</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">添加到@randunel的正确答案（尚无法对此发表评论）：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我还必须将/ usr / local / bin / node链接到/ usr / bin / nodejs。 </font></font></p>

<pre><code>sudo ln -s /usr/bin/nodejs /usr/local/bin/node
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">显然，这是覆盖/ usr / bin / node命令。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不知道如何设置，但希望它对其他人有帮助，因为弄清楚为什么上述方法对我不起作用是很痛苦的。 </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GilPro</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><h3><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点版本管理器（nvm）</font></font></h3>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您想安装多个nodejs版本并在它们之间轻松切换，建议您使用</font></font><a href="https://github.com/creationix/nvm" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node Version Manger</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它还解决了命名问题（</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">vs </font></font><code>nodejs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很简单：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装一个nodejs版本：</font></font></p>

<pre><code>$ nvm install 4.4
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，除了已经安装的版本之外，您还拥有nodejs 4.4，您可以使用</font></font><code>node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">命令来访问新安装的版本：</font></font></p>

<pre><code>$ node -v    // The new version added by nvm.<font></font>
v4.4.5<font></font>
$ nodejs -v  // The OS version is untouched and still available.<font></font>
v0.10.25<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以安装更多的nodejs版本，并在它们之间轻松切换：</font></font></p>

<pre><code>$ nvm install 6.2<font></font>
$ nvm use 6.2<font></font>
Now using node v6.2.1 (npm v3.9.3)<font></font>
$ node -v<font></font>
v6.2.1<font></font>
$ nvm use 4.4<font></font>
Now using node v4.4.5 (npm v2.15.5)<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝凯斯丁</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这也发生在我身上。 </font></font></p>

<pre><code>node -v =&gt; 0.10.2<font></font>
nodejs -v =&gt; 5.5.0<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题是我前一段时间从源代码安装了节点。</font><font style="vertical-align: inherit;">跑步</font></font></p>

<pre><code>which node
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">始终指向此本地安装。</font><font style="vertical-align: inherit;">也，</font></font></p>

<pre><code>echo NODE_PATH
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指向本地安装。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用源安装删除目录并没有帮助。</font><font style="vertical-align: inherit;">它只是破坏了节点命令。</font><font style="vertical-align: inherit;">最后，取消设置NODE_PATH环境变量，然后清除然后重新安装nodejs可以解决问题。</font></font></p>

<pre><code>unset NODE_PATH<font></font>
sudo apt-get --purge remove nodejs<font></font>
sudo apt-get install nodejs<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这之后， </font></font></p>

<pre><code>node -v =&gt; 5.5.0
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和npm install开始对依赖于Node =&gt; 5.0的软件包起作用。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">L凯</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">显然，解决方案在Ubuntu版本之间有所不同。</font><font style="vertical-align: inherit;">以下在Ubuntu 13.10上为我工作：</font></font></p>

<pre><code>sudo apt-get install nodejs-legacy
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">高温超导</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑：</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">经验法则：</font></font></strong></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果已安装</font></font><code>nodejs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但缺少</font></font><code>/usr/bin/node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">二进制文件，则也要安装</font></font><code>nodejs-legacy</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">  这只会创建丢失的软链接。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据我的测试，</font><font style="vertical-align: inherit;">安装</font></font><code>/usr/bin/node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">后</font><font style="vertical-align: inherit;">，Ubuntu 17.10及更高版本已经具有兼容性-softlink </font></font><code>nodejs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因此</font></font><code>nodejs-legacy</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这些发行版中</font><font style="vertical-align: inherit;">均已</font><font style="vertical-align: inherit;">缺少它们，因为不再需要它。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙十三</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我觉得这就是：</font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">sudo update-alternatives --install / usr / bin / node节点/ usr / bin / nodejs 10
</font></font></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用Debian替代品。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">逆天米亚</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在Ubuntu 14.04中有相同的问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经安装了“ nodejs”，并且可以使用，但是仅当我使用命令“ nodejs”时才可以。</font><font style="vertical-align: inherit;">如果我尝试使用“节点”，则什么也不会发生。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我用以下方式解决了这个问题：</font></font></p>

<ol>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装nodejs-legacy</font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">须藤apt-get install nodejs-legacy</font></font></pre></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之后，当我在命令行中键入“ node”时，我收到一条错误消息“ / usr / sbin / node：没有这样的文件或目录”</font></font></p>

<ol start="2">
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其次，我做了什么，它是“ nodejs”上的符号链接：</font></font></p>

<pre><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">须藤ln -s / usr / bin / nodejs / usr / sbin / node</font></font></pre></li>
</ol></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Sam路易</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您需要手动创建一个符号链接</font></font><code>/usr/bin/node</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">bash兼容shell的快捷方式：</font></font></p>

<pre><code>sudo ln -s `which nodejs` /usr/bin/node
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或者，如果您使用非标准的shell，只需使用以下命令对找到的路径进行硬编码</font></font><code>which nodejs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>sudo ln -s /usr/bin/nodejs /usr/bin/node
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以后编辑</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在您发布的链接中找到了这种解释</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">节点程序包（业余数据包无线节点程序）存在命名冲突，并且nodejs二进制文件已从node重命名为nodejs。</font><font style="vertical-align: inherit;">您需要将/ usr / bin / node符号链接到/ usr / bin / nodejs，或者可以卸载Amateur Packet Radio Node Program以避免这种冲突。</font></font></p>
</blockquote>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以后再编辑</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">自从我回答这个问题已经有一段时间了。</font><font style="vertical-align: inherit;">尽管我在此处发布的解决方案对我有用几次，但用户在评论中报告了更多解决方案：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">来自@ user229115</font></font></p>

<p><code>sudo update-alternatives --install /usr/bin/node node /usr/bin/nodejs 10</code></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从AskUbuntu（用户leftium）</font></font></p>

<pre><code>sudo apt-get --purge remove node<font></font>
sudo apt-get --purge remove nodejs<font></font>
sudo apt-get install nodejs<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
