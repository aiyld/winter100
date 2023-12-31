---
layout: question
title:  firebase.auth不是函数
date:   2020-03-24T09:21:57.000Z
description: 我将Webpack与firebase和firebase-admin一起使用。要安装firebase，我跑了npm install --save f...
img: 
author: 神乐
category: question
answer: 5
tags: JavaScript Webpack
topic: Webpack
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我将Webpack与firebase和firebase-admin一起使用。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要安装firebase，我跑了</font></font></p>

<pre><code>npm install --save firebase
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用导入Firebase，</font></font></p>

<pre><code>import * as firebase from 'firebase/app'<font></font>
import 'firebase/auth'<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我也试过</font></font></p>

<pre><code>import * as firebase from 'firebase'
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我试过了</font></font></p>

<pre><code>const firebase = require('firebase')
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据</font><a href="https://firebase.google.com/docs/web/setup" rel="noreferrer"><font style="vertical-align: inherit;">网络入门指南中的</font></a><font style="vertical-align: inherit;">建议</font></font><a href="https://firebase.google.com/docs/web/setup" rel="noreferrer"><font style="vertical-align: inherit;"></font></a> </p>

<p><font style="vertical-align: inherit;"></font><code>firebase.auth()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，</font><font style="vertical-align: inherit;">当我尝试使用</font><font style="vertical-align: inherit;">时，出现错误</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">console.js：32 TypeError：firebase.auth不是函数</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我使用调试器进行检查时，</font></font><code>firebase</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我发现它实际上没有</font></font><code>auth</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">功能：</font></font></p>

<pre><code>&gt; firebase<font></font>
 {__esModule: true, initializeApp: ƒ, app: ƒ, Promise: ƒ,&nbsp;…}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用webpack将auth（）包含在函数中？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谢谢。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑：这</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不是</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注释中问题的重复。</font><font style="vertical-align: inherit;">该问题涉及的是属于auth服务而不是auth服务本身的成员的方法。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3549篇《firebase.auth不是函数》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">十三</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我遇到了同样的问题，并通过以下方式解决了这个问题：</font></font></p>

<pre><code>&lt;script src = "https://www.gstatic.com/firebasejs/6.5.0/firebase-app.js"&gt; &lt;/script&gt;<font></font>
&lt;script src = "https://www.gstatic.com/firebasejs/6.5.0/firebase-auth.js"&gt; &lt;/script&gt;<font></font>
&lt;script&gt;<font></font>
// Firebase settings of your web application<font></font>
var firebaseConfig = {<font></font>
apiKey: "your apikey",<font></font>
authDomain: "hackatonteleton.firebaseapp.com",<font></font>
databaseURL: "https://name-database.firebaseio.com",<font></font>
projectId: "name-projectid",<font></font>
storageBucket: "name.appspot.com",<font></font>
messagingSenderId: "730018138942",<font></font>
Application ID: "1: 730018138942: web: eb12fac2f91fb17f"<font></font>
};<font></font>
// Initialize Firebase<font></font>
firebase.initializeApp (firebaseConfig);<font></font>
const auth = firebase.auth ();<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您注意到的区别是他们需要：</font></font></p>

<pre><code>&lt;script src = "https://www.gstatic.com/firebasejs/6.5.0/firebase-auth.js"&gt; &lt;/script&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并初始化功能</font></font></p>

<pre><code>const auth = firebase.auth ();`enter code here`
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">卡卡西</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">曾经有过同样的问题，我认为是因为版本问题。</font><font style="vertical-align: inherit;">我通过删除</font></font><code>node_modules</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有</font></font><code>webpack</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">生成的东西并从</font></font><a href="https://github.com/firebase/quickstart-nodejs/blob/master/auth-sessions/package.json" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此处</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">获取版本来</font><font style="vertical-align: inherit;">解决它</font><font style="vertical-align: inherit;">。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
顺便说一句，我认为这是非常奇怪的行为，因为它应该像官方文档中那样工作。  </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿理查德</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是因为未添加firebase-auth脚本。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，您必须通过以下方式在节点模块中安装npm文件：</font></font></p>

<pre><code>npm install firebase --save<font></font>
npm install firebase-admin --save<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您必须在firebase-app脚本之后添加firebase.auth脚本，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并确保版本相同。</font></font></strong></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">修复之前：</font></font></strong></p>

<pre><code>&lt;script src="https://www.gstatic.com/firebasejs/7.8.1/firebase-app.js"&gt;&lt;/script&gt;
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">修复后，您需要同时添加脚本和此FIREBASE帐户脚本，如下所示</font></font></strong></p>

<pre><code>&lt;script src="https://www.gstatic.com/firebasejs/7.8.1/firebase-app.js"&gt;&lt;/script&gt;<font></font>
&lt;script src="https://www.gstatic.com/firebasejs/7.8.1/firebase-auth.js"&gt;&lt;/script&gt;<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后就应该很好地工作</font></font></strong></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不断收到错误消息，说</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">“ TypeError：firebase.auth不是函数”</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我出现了auth对象，而我做了不同的事情是以不同的顺序安装模块。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一次安装模块（这是auth对象未出现的时候）：</font></font></p>

<pre><code>// this seems to confuse things with the auth object when installed in this order<font></font>
$ npm install firebase-admin --save<font></font>
$ npm install firebase --save<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我删除了npm文件夹并从头开始，尽管这次我颠倒了安装顺序：</font></font></p>

<pre><code>// for some reason this worked and now I can access the auth object<font></font>
$ npm install firebase --save<font></font>
$ npm install firebase-admin --save<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我什么也没做。</font><font style="vertical-align: inherit;">我只是通过首先安装firebase然后第二安装firebase-admin来颠倒了安装顺序。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我希望这对其他人有用。</font></font></p>

<p><a href="https://github.com/firebase/firebase-js-sdk/issues/752#issuecomment-389508849" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你可以在这里读更多关于它的内容</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">乐古一</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管此问题背后有许多根本原因，但也可能是这种情况。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我忘了包括auth和db的js文件，尽管我在JS代码中使用了它们。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">修复之前；</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="false" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;!-- Firebase App (the core Firebase SDK) is always required and must be listed first --&gt;<font></font>
&lt;script src="https://www.gstatic.com/firebasejs/6.1.1/firebase-app.js"&gt;&lt;/script&gt;</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">修复后；</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="false" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;!-- Firebase App (the core Firebase SDK) is always required and must be listed first --&gt;<font></font>
&lt;script src="https://www.gstatic.com/firebasejs/6.1.1/firebase-app.js"&gt;&lt;/script&gt;<font></font>
<font></font>
&lt;!-- Add Firebase products that you want to use --&gt;<font></font>
&lt;script src="https://www.gstatic.com/firebasejs/6.1.1/firebase-auth.js"&gt;&lt;/script&gt;<font></font>
<font></font>
&lt;script src="https://www.gstatic.com/firebasejs/6.1.1/firebase-database.js"&gt;&lt;/script&gt;</code></pre>
</div>
</div>
<p></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
