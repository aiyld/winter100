---
layout: question
title:  如何使用node.js漂亮地打印JSON？
date:   2020-03-17T09:05:03.000Z
description: 这似乎是一个已解决的问题，但我无法找到解决方案。基本上，我读取了一个JSON文件，更改了密钥，然后将新的JSON写回到同一文件。都可以，但是我松了JS...
img: 
author: Davaid番长十三
category: question
answer: 3
tags: json Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这似乎是一个已解决的问题，但我无法找到解决方案。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本上，我读取了一个JSON文件，更改了密钥，然后将新的JSON写回到同一文件。</font><font style="vertical-align: inherit;">都可以，但是我松了JSON格式，所以，而不是：</font></font></p>

<pre><code>{<font></font>
  name:'test',<font></font>
  version:'1.0'<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我懂了</font></font></p>

<pre><code>{name:'test',version:'1.1'}
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js中是否可以将格式良好的JSON写入文件？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1919篇《如何使用node.js漂亮地打印JSON？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门老丝Pro</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您不想将其存储在任何地方，只需查看对象以进行调试即可。</font></font></p>

<pre><code>console.log(JSON.stringify(object, null, "  "));
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以更改第三个参数以调整缩进量。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">伽罗Mandy</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您只想漂亮地打印对象而不将其导出为有效JSON，则可以使用</font></font><code>console.dir()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它使用语法突出显示，智能缩进，从键中删除引号，并使输出尽可能漂亮。</font></font></p>

<pre><code>const jsonString = `{"name":"John","color":"green",<font></font>
                     "smoker":false,"id":7,"city":"Berlin"}`<font></font>
const object = JSON.parse(jsonString)<font></font>
<font></font>
console.dir(object, {depth: null, colors: true})<font></font>
</code></pre>

<p><a href="https://i.stack.imgur.com/ALZfc.png" rel="noreferrer"><img src="https://i.stack.imgur.com/ALZfc.png" alt="记录对象的屏幕截图"></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在引擎盖下，它是的快捷方式</font></font><code>console.log(util.inspect(…))</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">唯一的区别是它绕过了</font></font><code>inspect()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在对象上定义的</font><font style="vertical-align: inherit;">任何自定义</font><font style="vertical-align: inherit;">函数。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小阿飞</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那这个呢？</font></font></p>

<pre><code>console.table(object)
</code></pre>

<p><a href="https://i.stack.imgur.com/8PJK6.png" rel="noreferrer"><img src="https://i.stack.imgur.com/8PJK6.png" alt="样品"></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
