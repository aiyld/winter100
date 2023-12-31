---
layout: question
title:  package.json中的本地依赖项
date:   2020-03-17T09:04:33.000Z
description: 我想要做这样的事情，所以npm install也安装package.json的../somelocallib或更重要的是它的依赖。"dependenc...
img: 
author: 乐米亚
category: question
answer: 10
tags: node.js Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想要做这样的事情，所以</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也安装</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font><code>../somelocallib</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或更重要的是它的依赖。</font></font></p>

<pre><code>"dependencies": {<font></font>
    "express": "*",<font></font>
    "../somelocallib": "*"<font></font>
}<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1917篇《package.json中的本地依赖项》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无A</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实际上，从npm 2.0开始，现在支持本地路径（请参阅</font></font><a href="https://www.npmjs.org/doc/files/package.json.html#local-paths" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此处</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小JinJin蛋蛋</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很好.....至少在Windows上（我的npm是3.something），我需要这样做：</font></font></p>

<pre><code>"dependencies": {<font></font>
 "body-parser": "^1.17.1",<font></font>
 "module1": "../module1",<font></font>
 "module2": "../module2",<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我这样做时，</font></font><code>npm install ../module1 --save</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它导致绝对路径，而不是文档中的相对路径。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我弄乱了一点，确定</font></font><code>../xxx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">足够了。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">具体来说，我已签出本地节点模块以说d：\ build \ module1，d：\ build \ module2和d：\ build \ nodeApp中的节点项目（应用程序）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要“安装”，我：</font></font></p>

<pre><code>d:\build\module1&gt; rmdir "./node_modules" /q /s &amp;&amp; npm install<font></font>
d:\build\module2&gt; rmdir "./node_modules" /q /s &amp;&amp; npm install<font></font>
d:\build\nodeApp&gt; rmdir "./node_modules" /q /s &amp;&amp; npm install<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">module1的package.json的依赖项为“ module2”：“ ../module2”; </font><font style="vertical-align: inherit;">module2没有本地依赖关系；</font><font style="vertical-align: inherit;">nodeApp具有依赖项“ module1”：“ ../ module1”和“ module2”：“ ../ module2”。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不确定这是否仅对我有用，因为所有3个文件夹（module1，module2和nodeApp）都位于同一级别上。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神奇Tony古一</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这对我有用：首先，确保npm目录具有正确的用户</font></font></p>

<pre><code>sudo chown -R myuser ~/.npm<font></font>
sudo chown -R myuser /usr/local/lib/node_modules<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后您在package.json中链接目录</font></font></p>

<pre><code>"scripts": {<font></font>
 "preinstall": "npm ln mylib ../../path/to/mylib"<font></font>
}, <font></font>
"dependencies": {<font></font>
  "mylib" : "*"<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞达蒙樱</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">完成本地开发的两个步骤：</font></font></strong></p>

<ol>
<li><a href="https://docs.npmjs.com/files/package.json#local-paths" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供包含程序包的本地目录的路径。</font></font></a></li>
<li><a href="https://docs.npmjs.com/cli/link" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">符号链接包文件夹</font></font></a></li>
</ol></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长LA</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我知道那</font></font><code>npm install ../somelocallib</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可行。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，我不知道您在问题中显示的语法是否适用于</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">...</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不幸的是，</font></font><a href="https://npmjs.org/doc/json.html#URLs-as-Dependencies" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">似乎只提到URL作为依赖项。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试</font></font><code>file:///.../...tar.gz</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，指向一个压缩的本地库...，然后告诉我们它是否有效。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Harry小小</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">硕士项目</font></font></h1>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是您将用于主项目的package.json：</font></font></p>

<pre><code>"dependencies": {<font></font>
    "express": "*",<font></font>
    "somelocallib": "file:./somelocallib"<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那里</font></font><code>./somelocallib</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相对于主项目package.json</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的库文件夹的引用</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参考：</font><a href="https://docs.npmjs.com/files/package.json#local-paths" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://docs.npmjs.com/files/package.json#local-paths" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//docs.npmjs.com/files/package.json#local-paths</font></font></a></p>

<hr>

<h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">子项目</font></font></h1>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">处理您的库依赖项。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">除了运行外</font></font><code>npm install</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，您还需要运行</font></font><code>(cd node_modules/somelocallib &amp;&amp; npm install)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是NPM的已知错误。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参考：</font></font><a href="https://github.com/npm/npm/issues/1341" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font><a href="https://github.com/npm/npm/issues/1341" rel="noreferrer"><font style="vertical-align: inherit;">//github.com/npm/npm/issues/1341</font></a><font style="vertical-align: inherit;">（寻求更新的参考）</font></font></p>

<hr>

<h1><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Docker注释</font></font></h1>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">签入您的母版，</font></font><code>package.lock</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后签</font></font><code>somelocallib/package.lock</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">入源代码管理器。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后在您的Dockerfile中使用：</font></font></p>

<pre><code>FROM node:10<font></font>
WORKDIR /app<font></font>
# ...<font></font>
COPY ./package.json ./package-lock.json ./<font></font>
COPY somelocallib somelocallib<font></font>
RUN npm ci<font></font>
RUN (cd node_modules/zkp-utils/ &amp;&amp; npm ci)<font></font>
# ...<font></font>
</code></pre>

<p><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在</font></font><code>(cd A &amp;&amp; B)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">结构中</font><font style="vertical-align: inherit;">使用括号</font><font style="vertical-align: inherit;">使运算幂等。</font></font></em></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞米亚</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这对我有用。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将以下内容放入您的package.json文件中</font></font></p>

<pre><code>"scripts": {<font></font>
    "preinstall": "npm install ../my-own-module/"<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙阳光</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在可以</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">直接</font><font style="vertical-align: inherit;">在您的本地指定本地Node模块的安装路径</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">从文档：</font></font></p>

<blockquote>
  <h2><a href="https://docs.npmjs.com/files/package.json#local-paths" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">本地路径</font></font></a></h2>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从2.0.0版开始，您可以提供包含软件包的本地目录的路径。</font><font style="vertical-align: inherit;">可以使用</font></font><code>npm install -S</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>npm install --save</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用以下任意形式</font><font style="vertical-align: inherit;">保存本地路径</font><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>../foo/bar<font></font>
~/foo/bar<font></font>
./foo/bar<font></font>
/foo/bar<font></font>
</code></pre>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这种情况下，它们将被标准化为相对路径并添加到您的中</font></font><code>package.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">例如：</font></font></p>

<pre><code>{<font></font>
  "name": "baz",<font></font>
  "dependencies": {<font></font>
    "bar": "file:../foo/bar"<font></font>
  }<font></font>
}<font></font>
</code></pre>
  
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此功能对于本地脱机开发和创建需要npm安装的测试很有用，您不想在不打外部服务器的地方安装npm，但是在将程序包发布到公共注册表时不应使用。 </font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚猪猪</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您想进一步实现自动化，因为您正在将模块检入版本控制中，并且不想依赖记住npm链接的开发人员，则可以将其添加到package.json的“脚本”部分：</font></font></p>

<pre><code>"scripts": {<font></font>
    "postinstall": "npm link ../somelocallib",<font></font>
    "postupdate": "npm link ../somelocallib"<font></font>
  }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这感觉不算是骇人听闻的，但似乎“可行”。</font><font style="vertical-align: inherit;">从此npm问题获得了提示：</font><a href="https://github.com/npm/npm/issues/1558#issuecomment-12444454" rel="nofollow noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> :
 </font></font><a href="https://github.com/npm/npm/issues/1558#issuecomment-12444454" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/npm/npm/issues/1558#issuecomment-12444454</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙神无</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是添加本地依赖项的方法：</font></font></p>

<p><code>npm install file:src/assets/js/FILE_NAME</code></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从NPM将其添加到package.json：</font></font></strong></p>

<p><code>npm install --save file:src/assets/js/FILE_NAME</code></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">像这样直接添加到package.json中：</font></font></strong></p>

<pre><code>....<font></font>
  "angular2-autosize": "1.0.1",<font></font>
  "angular2-text-mask": "8.0.2", <font></font>
  "animate.css": "3.5.2",<font></font>
  "LIBRARY_NAME": "file:src/assets/js/FILE_NAME"<font></font>
....<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
