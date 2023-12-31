---
layout: question
title:  如何使用vue.js / nuxt.js获取目录中的所有图像文件
date:   2020-03-27T12:18:59.000Z
description: 我正在一个nuxt.js项目上并出现错误： 在浏览器中，我看到此错误：__webpack_require__(...).context is no...
img: 
author: Harry凯
category: question
answer: 0
tags: JavaScript Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在一个nuxt.js项目上并出现错误： </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在浏览器中，我看到此错误：</font></font></p>

<pre><code>__webpack_require__(...).context is not a function
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而且，在终端中，我收到此错误：</font></font></p>

<pre><code>Critical dependency: require function is used in a way in which dependencies cannot be statically extracted 
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的代码</font></font></p>

<pre><code>&lt;script&gt;<font></font>
export default {<font></font>
  name: 'SectionOurClients',<font></font>
  data() {<font></font>
    return {<font></font>
      imageDir: '../assets/images/clients/',<font></font>
      images: {},<font></font>
    };<font></font>
  },<font></font>
<font></font>
  mounted() {<font></font>
    this.importAll(require.context(this.imageDir, true, /\.png$/));<font></font>
  },<font></font>
<font></font>
  methods: {<font></font>
    importAll(r) {<font></font>
      console.log(r)<font></font>
    },<font></font>
  },<font></font>
};<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已经从使用上面的脚本</font></font><a href="https://stackoverflow.com/a/48875151"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请帮忙，谢谢。</font></font></p>

<hr>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：遵循@MaxSinev的答案后，这是我的工作代码的外观：</font></font></p>

<pre><code>&lt;template lang="pug"&gt;<font></font>
  .row<font></font>
    .col(v-for="client in images")<font></font>
      img(:src="client.pathLong")<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
export default {<font></font>
  name: 'SectionOurClients',<font></font>
  data() {<font></font>
    return {<font></font>
      images: [],<font></font>
    };<font></font>
  },<font></font>
<font></font>
  mounted() {<font></font>
    this.importAll(require.context('../assets/images/clients/', true, /\.png$/));<font></font>
  },<font></font>
<font></font>
  methods: {<font></font>
    importAll(r) {<font></font>
      r.keys().forEach(key =&gt; (this.images.push({ pathLong: r(key), pathShort: key })));<font></font>
    },<font></font>
  },<font></font>
};<font></font>
&lt;/script&gt;<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3817篇《如何使用vue.js / nuxt.js获取目录中的所有图像文件》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
