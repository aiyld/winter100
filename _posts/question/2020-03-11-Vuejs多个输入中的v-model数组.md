---
layout: question
title:  Vue.js：多个输入中的v-model数组
date:   2020-03-11T07:02:29.000Z
description: 我有一个附加了v模型的输入文本字段，每当有人单击“添加”按钮时，就会有另一个具有相同v模型的输入文本添加到DOM中。我以为我会得到一个v模型值的数组，但它...
img: 
author: 樱Davaid
category: question
answer: 0
tags: 数组 Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个附加了v模型的输入文本字段，每当有人单击“添加”按钮时，就会有另一个具有相同v模型的输入文本添加到DOM中。</font><font style="vertical-align: inherit;">我以为我会得到一个v模型值的数组，但它只会得到第一个v模型输入的值：</font></font></p>

<pre><code>&lt;div id="app"&gt;<font></font>
  &lt;div id="references"&gt;<font></font>
    &lt;input v-model="references" type="text"&gt;<font></font>
  &lt;/div&gt;<font></font>
  &lt;button @click="addReference"&gt;Add&lt;/button&gt;<font></font>
&lt;/div&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我附加到dom的html由addReference方法触发：</font></font></p>

<pre><code>addReference: function(e) {<font></font>
  e.preventDefault();<font></font>
  console.log(this.references);<font></font>
  var inputEl = '&lt;input v-model="references" type="text"&gt;';<font></font>
  $('#references').append(inputEl);<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是Vuejs无法做到的吗？</font><font style="vertical-align: inherit;">使用Vuejs从动态dom元素中收集值是否有其他方法？</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="true" data-console="true" data-babel="false">
<div class="snippet-code snippet-currently-hidden">
<pre class="snippet-code-js lang-js prettyprint-override"><code>new Vue({<font></font>
  el: "#app",<font></font>
  data: {<font></font>
    references: "text"<font></font>
  },<font></font>
  methods: {<font></font>
    addReference: function(e) {<font></font>
      e.preventDefault();<font></font>
      console.log(this.references);<font></font>
      var inputEl = '&lt;input v-model="references" type="text"&gt;';<font></font>
      $('#references').append(inputEl);<font></font>
    }<font></font>
  }<font></font>
})</code></pre>
<pre class="snippet-code-css lang-css prettyprint-override"><code>input {<font></font>
  display: block;<font></font>
  margin: 1px;<font></font>
}</code></pre>
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.5.16/vue.min.js"&gt;&lt;/script&gt;<font></font>
&lt;script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"&gt;&lt;/script&gt;<font></font>
&lt;div id="app"&gt;<font></font>
  &lt;div id="references"&gt;<font></font>
    &lt;input v-model="references" type="text"&gt;<font></font>
  &lt;/div&gt;<font></font>
  &lt;button @click="addReference"&gt;Add&lt;/button&gt;<font></font>
&lt;/div&gt;</code></pre>
</div>
</div>
<p></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第708篇《Vue.js：多个输入中的v-model数组》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
