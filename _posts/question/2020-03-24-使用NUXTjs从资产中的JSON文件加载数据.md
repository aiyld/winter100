---
layout: question
title:  使用NUXT.js从资产中的JSON文件加载数据
date:   2020-03-24T02:15:40.000Z
description: 假设我assets/data/geo/regions.json在NUXT.js项目文件夹结构中有文件。如何将数据从该文件读取到我的项目中？我已经尝试过...
img: 
author: 卡卡西米亚
category: question
answer: 2
tags: json Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">假设我</font></font><code>assets/data/geo/regions.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在NUXT.js项目文件夹结构中</font><font style="vertical-align: inherit;">有</font><font style="vertical-align: inherit;">文件。</font><font style="vertical-align: inherit;">如何将数据从该文件读取到我的项目中？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经尝试过</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">axios，</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是我不知道该文件将使用哪个URL，我已经尝试了所有可能的URL。</font><font style="vertical-align: inherit;">有什么更好的解决方案？</font><font style="vertical-align: inherit;">也许将JSON文件保存在</font></font><code>static</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹中</font><font style="vertical-align: inherit;">更好</font><font style="vertical-align: inherit;">？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谢谢！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3226篇《使用NUXT.js从资产中的JSON文件加载数据》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">前端JinJin</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您打算在循环中加载数据，则可能需要使用“ require”而不是“ import”。</font></font></p>

<pre><code>jsons = ["json_one","json_two"]<font></font>
jsons_readed = []<font></font>
<font></font>
// In the loop<font></font>
file = require(`./assets/data/geo/${jsons[i]}`)<font></font>
jsons_readed.push(file)<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，我认为您可以使用jsons_readed访问对象。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva猿</span>
            <span class="discuss-time">2020.03.24</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果</font></font><code>regions.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件不会更改，则可以轻松地将其放在</font></font><code>static</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件夹中。</font><font style="vertical-align: inherit;">然后该网址将是</font><a href="https://github.com/nuxt/nuxt.js/issues/123" rel="noreferrer"><font style="vertical-align: inherit;">在nuxt问题页面上</font></a></font><code>/data/geo/regions.json</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 
查看此问题</font></font><a href="https://github.com/nuxt/nuxt.js/issues/123" rel="noreferrer"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
