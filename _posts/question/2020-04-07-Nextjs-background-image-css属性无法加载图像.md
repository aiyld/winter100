---
layout: question
title:  Next.js background-image css属性无法加载图像
date:   2020-04-07T03:48:36.000Z
description: 问题只是我正在尝试访问静态图像以在React的内联backgroundImage属性中使用。我正在使用reactjs和next.js，然后在next....
img: 
author: DavaidTony宝儿
category: question
answer: 1
tags: HTML React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">问题只是我正在尝试访问静态图像以在React的内联backgroundImage属性中使用。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用reactjs和next.js，然后在next.js添加图像时遇到了一个问题，但是通过使用名为Next.js + Images的图像加载器解决了此问题</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在我可以使用普通的html img标签正常添加图像</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">示例：</font></font><code>&lt;img src={ img } /&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这可行。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是当我尝试添加css背景图像时，如下所示： </font></font></p>

<pre><code>const team = (props) =&gt; {<font></font>
const img = require("../../assets/images/security-team.jpg");<font></font>
const styling = {<font></font>
    backgroundImage: `url('${img}')`,<font></font>
    width:"100%",<font></font>
    height:"100%"<font></font>
}<font></font>
console.log(img);<font></font>
return (<font></font>
    &lt;dev className="team" style={styling}&gt;<font></font>
<font></font>
    &lt;/dev&gt;<font></font>
);<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">}</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是console.log结果： </font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">/_next/static/images/security-team-449919af8999ae47eaf307dca4dda8e1.jpg</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该图像没有出现，并且没有错误发生，然后，我尝试在浏览器中输入website-url + console.log结果该图像出现了！ </font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4117篇《Next.js background-image css属性无法加载图像》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Lynn</span>
            <span class="discuss-time">2022.03.04</span>
          </div>
          <div class="discuss-comment"><p>有解决吗</p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
