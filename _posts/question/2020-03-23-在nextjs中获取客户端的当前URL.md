---
layout: question
title:  在next.js中获取客户端的当前URL
date:   2020-03-23T01:52:25.000Z
description: 因此，我正在开发一个nodejs应用程序，该应用程序将打开我的新网站，我想为我的用户在客户端提供一种显示不同内容的方法，并根据用户所按下的内容进行重新渲染...
img: 
author: 西门Davaid
category: question
answer: 0
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，我正在开发一个nodejs应用程序，该应用程序将打开我的新网站，我想为我的用户在客户端提供一种显示不同内容的方法，并根据用户所按下的内容进行重新渲染。</font><font style="vertical-align: inherit;">我的想法是，例如，首先用户将看到“请先选择一个工具”，然后用户将在导航栏中选择一个工具，然后该页面将被重新渲染并显示在超大型飞行器内选定的工具，其网址为例如更改为/ admin / [ToolSelected]。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">唯一的事情就是我不知道如何实现这一目标。</font><font style="vertical-align: inherit;">我以为客户端代码可以检测到url是什么，并将其作为页面变量放置，然后根据页面变量是什么，该工具将显示IF语句。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的理论会行得通吗，或者如何以有效的方式实现这一目标？</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的主页代码：</font></font></p>

<pre><code>// Including Navbar and css<font></font>
import AdminLayout from '../comps/admin/adminLayout'<font></font>
<font></font>
// the so called "tools" more will exist in the future<font></font>
import Passform from '../comps/admin/tools/passform'<font></font>
<font></font>
<font></font>
// Fetching the current url the user is on<font></font>
var page = CURRENT_URL;<font></font>
<font></font>
<font></font>
const jumbotron = {<font></font>
  background: 'white'<font></font>
}<font></font>
<font></font>
const Admin = (page) =&gt; (<font></font>
<font></font>
  &lt;AdminLayout&gt;<font></font>
<font></font>
  &lt;style global jsx&gt;<font></font>
  {<font></font>
    `body {<font></font>
      background: #eff0f3;<font></font>
    }`<font></font>
  }<font></font>
  &lt;/style&gt;<font></font>
    &lt;div className="jumbotron" style={jumbotron}&gt;<font></font>
<font></font>
    {(page == "passform") ? (<font></font>
      &lt;Passform/&gt;<font></font>
    ) : (<font></font>
      &lt;h3&gt;Something is wrong :/ . {page}&lt;/h3&gt;<font></font>
    )}<font></font>
<font></font>
    &lt;/div&gt;<font></font>
  &lt;/AdminLayout&gt;<font></font>
)<font></font>
<font></font>
export default Admin<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2623篇《在next.js中获取客户端的当前URL》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
