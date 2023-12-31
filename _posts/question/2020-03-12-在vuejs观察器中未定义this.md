---
layout: question
title:  在vue.js观察器中未定义\`this\`
date:   2020-03-12T07:57:43.000Z
description: 我有观察者组件props  {    propShow  { required  true, type  Boolean }},data() ...
img: 
author: 梅小宇宙
category: question
answer: 1
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有观察者组件</font></font></p>

<pre><code>props: {<font></font>
    propShow: { required: true, type: Boolean }<font></font>
},<font></font>
<font></font>
data() {<font></font>
    return {<font></font>
        show: this.propShow<font></font>
    }<font></font>
},<font></font>
<font></font>
watch: {<font></font>
    propShow: {<font></font>
        handler: (val, oldVal) =&gt; {<font></font>
            this.show = val;<font></font>
        }<font></font>
    }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">每当</font></font><code>parent</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件更改时，</font></font><code>propShow</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此组件必须更新其</font></font><code>show</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">属性。</font></font><code>This</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件还修改了</font></font><code>show</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">属性，这就是为什么我需要同时使用</font></font><code>show</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font><font style="vertical-align: inherit;">的原因</font></font><code>propShow</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因为Vue.js不允许直接更改属性。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这条线</font></font></p>

<pre><code>this.show = val;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">导致错误</font></font></p>

<pre><code>TypeError: Cannot set property 'show' of undefined
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因为</font></font><code>this</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">内部处理程序是</font></font><code>undefined</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为什么？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1103篇《在vue.js观察器中未定义\`this\`》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德Itachi</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你将不得不使用</font></font><code>function</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里的语法，在文档告诫</font></font><a href="https://vuejs.org/v2/api/#watch"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意，您不应使用箭头功能来定义观察者（例如searchQuery：newValue =&gt; this.updateAutocomplete（newValue））。</font><font style="vertical-align: inherit;">原因是箭头函数绑定了父上下文，因此这将不是您期望的Vue实例，并且this.updateAutocomplete将是未定义的。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，您的代码应为：</font></font></p>

<pre><code>watch: {<font></font>
    propShow: {<font></font>
        handler: function(val, oldVal) {<font></font>
            this.show = val;<font></font>
        }<font></font>
    }<font></font>
}<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
