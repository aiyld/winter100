---
layout: question
title:  如何解决“未经检查的runtime.lastError：在收到响应之前关闭消息端口”的Chrome问题？
date:   2020-03-10T02:18:50.000Z
description: 我正在为我的项目使用VueJS和Laravel。这个问题最近开始显示，甚至在旧的git分支中也显示。此错误仅在Chrome浏览器中显示。 ...
img: 
author: 
category: question
answer: 12
tags: laravel Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在为我的项目使用VueJS和Laravel。</font><font style="vertical-align: inherit;">这个问题最近开始显示，甚至在旧的git分支中也显示。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此错误仅在Chrome浏览器中显示。 </font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第419篇《如何解决“未经检查的runtime.lastError：在收到响应之前关闭消息端口”的Chrome问题？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小宇宙猪猪</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我将控制台日志数据从一个选项卡发送到另一个选项卡，而实际上并不需要第一个控制台。</font><font style="vertical-align: inherit;">但是，错误消息确实使我烦恼，所以我右键单击并选择“不显示来自x网站的消息”。</font><font style="vertical-align: inherit;">也许这是最简单的解决方法：）</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva理查德</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果浏览器上安装了任何防病毒扩展，请禁用。</font><font style="vertical-align: inherit;">就我而言，反病毒扩展才是罪魁祸首。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Near西里泡芙</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就我而言，这是在我自己的页面源中设置的断点。</font><font style="vertical-align: inherit;">如果我删除或禁用了断点，则错误将清除。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">断点位于渲染代码的中等复杂度中。</font><font style="vertical-align: inherit;">页面不同部分中的其他断点没有这种效果。</font><font style="vertical-align: inherit;">我无法制定出一个总是会触发此错误的简单测试用例。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">JinJin西门</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对我来说是</font></font><code>Auto Tab Discard</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它会在固定的标签上抛出该错误。</font><font style="vertical-align: inherit;">我创建了一个错误报告，</font></font><a href="https://github.com/rNeomy/auto-tab-discard/issues/101" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/rNeomy/auto-tab-discard/issues/101</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞宝儿猴子</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就我而言，这是OneTab chrome扩展程序。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德理查德</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于那些来这里调试Chrome 73中的错误的人来说，一种可能是因为Chrome 73及更高版本禁止内容脚本中的跨域请求。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更多阅读：</font></font></p>

<ol>
<li><a href="https://www.chromestatus.com/feature/5629709824032768" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://www.chromestatus.com/feature/5629709824032768</font></font></a></li>
<li><a href="https://www.chromium.org/Home/chromium-security/extension-content-script-fetches" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://www.chromium.org/Home/chromium-security/extension-content-script-fetches</font></font></a></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这影响到许多Chrome扩展作者，他们现在需要争夺修复扩展的原因，因为Chrome认为“我们的数据表明大多数扩展都不会受到此更改的影响。”</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（与您的应用程序代码无关）</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更新</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：我修复了CORs问题，但仍然看到此错误。</font><font style="vertical-align: inherit;">我怀疑这是Chrome的错。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞神无</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果错误的原因是扩展用隐身   </font></font><kbd>Ctrl</kbd><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">+ </font></font><kbd>Shift</kbd><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">+ </font></font><kbd>N</kbd><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">在隐身模式下，Chrome没有扩展程序。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">UPD。</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您需要在隐身模式下进行某些扩展，例如ReduxDevTools或其他任何扩展，请在扩展设置中启用“允许隐身”</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神无Davaid</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经回答了</font></font><a href="https://github.com/gatsbyjs/gatsby/issues/9899#issuecomment-469545096" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">就我而言，问题是由于</font></font><code>Video Downloader professional</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>AdBlock</code></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简而言之，由于某些Google chrome插件而出现此问题 </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tony小小</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Post很旧，与Chrome扩展程序的开发并没有密切的关系，但请在此处发布。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在回调中响应消息时，我遇到了同样的问题。</font><font style="vertical-align: inherit;">解决方案是</font><font style="vertical-align: inherit;">在后台消息侦听器中</font><font style="vertical-align: inherit;">返回</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">true</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">background.js的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简单示例</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">它响应来自popup.js的任何消息。</font></font></p>

<pre><code>chrome.runtime.onMessage.addListener(function(rq, sender, sendResponse) {<font></font>
    // setTimeout to simulate any callback (even from storage.sync)<font></font>
    setTimeout(function() {<font></font>
        sendResponse({status: true});<font></font>
    }, 1);<font></font>
    // return true;  // uncomment this line to fix error<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">popup.js</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它在弹出窗口上发送消息。</font><font style="vertical-align: inherit;">在取消注释</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">background.js</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件中的</font><font style="vertical-align: inherit;">“ return true”行之前，您将获得例外</font><font style="vertical-align: inherit;">。</font></font></p>

<pre><code>document.addEventListener("DOMContentLoaded", () =&gt; {<font></font>
    chrome.extension.sendMessage({action: "ping"}, function(resp) {<font></font>
        console.log(JSON.stringify(resp));<font></font>
    });<font></font>
});<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">manifest.json</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，以防万一:)注意警报权限部分！</font></font></p>

<pre><code>{<font></font>
  "name": "TestMessages",<font></font>
  "version": "0.1.0",<font></font>
  "manifest_version": 2,<font></font>
  "browser_action": {<font></font>
    "default_popup": "src/popup.html"<font></font>
  },<font></font>
  "background": {<font></font>
    "scripts": ["src/background.js"],<font></font>
    "persistent": false<font></font>
  },<font></font>
  "permissions": [<font></font>
    "alarms"<font></font>
  ]<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">StafanGO</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您是扩展程序开发人员，并且已在此处搜索了自己的方法以尝试停止导致此错误：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题不是CORB，因为被阻止的COR </font></font><a href="https://www.chromium.org/Home/chromium-security/corb-for-developers" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">表现为警告，</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如-</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">跨域读取阻止（CORB）阻止</font><font style="vertical-align: inherit;">了MIME类型为text / html的</font><font style="vertical-align: inherit;">跨域响应
   </font></font><a href="https://www.example.com/example.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://www.example.com/example.html</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">有关</font><font style="vertical-align: inherit;">更多详细信息，</font><font style="vertical-align: inherit;">请参见
   </font></font><a href="https://www.chromestatus.com/feature/5629709824032768" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://www.chromestatus.com/feature/5629709824032768</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题很可能是对runtime.sendMessage的异步响应处理不当。</font><font style="vertical-align: inherit;">正如</font></font><a href="https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/runtime/onMessage" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MDN所说</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要发送异步响应，有两个选项：</font></font></p>
  
  <ul>
  <li>return true from the event listener. This keeps the sendResponse
  function valid after the listener returns, so you can call it later.</li>
  <li>return a Promise from the event listener, and resolve
  when you have the response (or reject it in case of an error). </li>
  </ul>
</blockquote>

<p>When you send an async response but fail to use either of these mechanisms, the supplied <code>sendResponse</code> argument to <code>sendMessage</code> goes out of scope and the result is exactly as the error message says: your message port (the message-passing apparatus) is closed before the response was received.</p>

<p>Webextension-polyfill authors have <a href="https://github.com/mozilla/webextension-polyfill/issues/130" rel="noreferrer">already written about it in June 2018</a>.</p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，最重要的是，如果您看到扩展引起这些错误，请仔细检查所有onMessage侦听器。</font><font style="vertical-align: inherit;">其中一些可能需要开始返回promise（将它们标记为异步就足够了）。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">null</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我禁用了Chrome中所有已安装的扩展程序-适用于我。</font><font style="vertical-align: inherit;">我现在已经清除控制台，没有错误。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Green樱</span>
            <span class="discuss-time">2020.03.10</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您访问</font></font><a href="http://chrome://extensions/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">chrome：// extensions /</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，则可以一次切换每个扩展名，然后查看实际上是哪个触发了该问题。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关闭扩展名后，刷新看到错误的页面，然后左右摆动鼠标或单击。</font><font style="vertical-align: inherit;">鼠标动作是引发错误的事情。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，我能够查明实际上是哪个扩展引起了该问题，并将其禁用。 </font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
