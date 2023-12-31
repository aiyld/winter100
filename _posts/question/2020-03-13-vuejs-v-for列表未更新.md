---
layout: question
title:  vue.js v-for列表未更新
date:   2020-03-13T09:10:45.000Z
description: 我有这个清单：<ul id="tab">    <li v-for="list in names">        {{ list.personN...
img: 
author: GreenGil
category: question
answer: 1
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有这个清单：</font></font></p>

<pre><code>&lt;ul id="tab"&gt;<font></font>
    &lt;li v-for="list in names"&gt;<font></font>
        {{ list.personName }}<font></font>
    &lt;/li&gt;<font></font>
&lt;/ul&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后我有了这个vue对象：</font></font></p>

<pre><code>var vm = new Vue ({<font></font>
    el: '#tab',<font></font>
        data: {<font></font>
            names: //an object array coming from the server<font></font>
        }<font></font>
    });<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，“名称”数据将被更新并从服务器获得信息。</font><font style="vertical-align: inherit;">但是，当名称被更新/更改时，它不会反映在客户端列表上。</font><font style="vertical-align: inherit;">列表中显示的项目仅反映最初加载页面时存在的项目。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Google Chrome浏览器的vue.js开发人员工具中，我始终可以看到更新的“名称”数据，但它并没有反映在DOM本身上。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">EDIT1</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：“名称”中有什么：</font></font></p>

<pre><code>names: Array[2]<font></font>
    0: Object<font></font>
    _id: "580aeafd017fbfb81a3a794d"<font></font>
    personName: "hi"<font></font>
<font></font>
    1: Object<font></font>
   _id: "580c4455ccc9e39c21f02434"<font></font>
   personName: "test"<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑2</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所以我正在使用node.js，并通过socket.io将数据实时从节点传输到客户端，如下所示：</font></font></p>

<pre><code>socket.on('userDocument', function(userDocument) {<font></font>
    var vm= new Vue ({<font></font>
        el: '#tab',<font></font>
        data: {<font></font>
            names: //an object array coming from the server<font></font>
        }<font></font>
    });<font></font>
});<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1468篇《vue.js v-for列表未更新》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙神无伽罗</span>
            <span class="discuss-time">2020.03.13</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果它是作为对象从服务器传递过来的，则在与data（）反应性绑定时，请确保使用Vue.set（obj，key，value）。</font></font></p>

<p><a href="http://vuejs.org/api/#Vue-set" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">http://vuejs.org/api/#Vue-set</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
