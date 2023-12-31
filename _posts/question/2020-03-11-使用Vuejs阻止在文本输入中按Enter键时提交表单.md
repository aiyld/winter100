---
layout: question
title:  使用Vue.js阻止在文本输入中按Enter键时提交表单
date:   2020-03-11T07:04:41.000Z
description: 我在应用程序中使用Vue.js，并且在表单中输入了文本<div id="myVueForm"><form>   <input type="text...
img: 
author: 小胖凯前端
category: question
answer: 8
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在应用程序中使用Vue.js，并且在表单中输入了文本</font></font></p>

<pre><code>&lt;div id="myVueForm"&gt;<font></font>
&lt;form&gt;<font></font>
   &lt;input type="text"  v-on="keyup:addCategory | key 'enter'"&gt;<font></font>
<font></font>
   &lt;!-- more form fields --&gt;<font></font>
   &lt;button type="submit"&gt;Submit Form&lt;/button&gt;<font></font>
&lt;/form&gt;<font></font>
&lt;/div&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在我的Vue实例中，我有以下内容</font></font></p>

<pre><code>new Vue({<font></font>
    el: '#myVueForm',<font></font>
<font></font>
    methods: {<font></font>
        addCategory: function(e)<font></font>
        {<font></font>
           if(e) e.preventDefault();<font></font>
           console.log("Added a new category, thanks!");<font></font>
        }<font></font>
    }<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尽管有</font></font><code>preventDefault();</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">呼叫，但是当用户在文本输入时按下Enter键时，表单仍会提交（尽管该</font></font><code>addCategory()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法确实触发了）。</font><font style="vertical-align: inherit;">这种行为可以在</font></font><a href="http://jsfiddle.net/Lr3yk13e/4/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这个小提琴中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">得到证明</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我知道我可以使用jQuery捕获事件并阻止提交，但是我想看看在Vue中是否有可能这样做，因为这似乎很常见。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第713篇《使用Vue.js阻止在文本输入中按Enter键时提交表单》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Harry猴子A</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于那些只是想阻止表单在Enter上提交但不想在输入上触发任何方法的用户，只需执行以下操作：</font></font></p>

<pre><code>&lt;input type="text" @keypress.enter.prevent /&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或在自定义组件上包括</font></font><code>native</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">修饰符：</font></font></p>

<pre><code>&lt;custom-input type="text" @keypress.enter.native.prevent /&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">精美可读，简洁明了。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">ProGO</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个边缘情况，其中输入在弹出窗口内，而弹出窗口仅用于表单的一部分。</font><font style="vertical-align: inherit;">我想防止Enter在弹出窗口打开时提交表单，但不是完全提交。</font><font style="vertical-align: inherit;">这工作：</font></font></p>

<pre><code>&lt;input type="text" @keydown.enter.prevent = "" /&gt; 
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚西门</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以从HTML获取事件并将其发送到Vue只是为了防止default，如下所示：</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的HTML</font></font></p>

<pre><code>&lt;input type="text" v-on:keydown.13="my_method($event)"&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JS</font></font></p>

<pre><code>methods: {<font></font>
    my_method(event){<font></font>
        // do something<font></font>
        if (event) event.preventDefault();<font></font>
        if (event) event.stopPropagation();<font></font>
    },<font></font>
},<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GO逆天L</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我为此写了一个助手。</font></font></p>

<pre class="lang-js prettyprint-override"><code>export const preventFormSubmitOnEnter = {<font></font>
  mounted() {<font></font>
    let cb = event =&gt; {<font></font>
      if (event) event.preventDefault();<font></font>
    };<font></font>
    if (this.$el.nodeName.toLowerCase() === "form") {<font></font>
      this.$el.onsubmit = cb;<font></font>
    } else {<font></font>
      const forms = this.$el.getElementsByTagName("form");<font></font>
      for (let i = 0; i &lt; forms.length; i++) {<font></font>
        const form = forms[i];<font></font>
        if (form) form.onsubmit = cb;<font></font>
      }<font></font>
    }<font></font>
  }<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在您的vue组件中包含此mixin，它将自动运行。 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个示例（我使用ElementUI）： </font></font></p>

<pre><code>&lt;template&gt;<font></font>
  &lt;el-form :model="form" :rules="rules" ref="form"&gt;<font></font>
    &lt;el-form-item prop="reference"&gt;<font></font>
      &lt;el-input v-model="form.reference" placeholder="Your Reference"/&gt;<font></font>
    &lt;/el-form-item&gt;<font></font>
  &lt;/el-form&gt;<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
import { preventFormSubmitOnEnter } from "./util";<font></font>
<font></font>
export default {<font></font>
  mixins: [preventFormSubmitOnEnter],<font></font>
  data() {<font></font>
    return {<font></font>
      form: {<font></font>
        reference: ""<font></font>
      },<font></font>
      rules: {<font></font>
        reference: [{ required: true, message: "Reference is required!" }]<font></font>
      }<font></font>
    };<font></font>
  },<font></font>
  methods: {<font></font>
    validate() {<font></font>
      return new Promise((resolve, reject) =&gt; {<font></font>
        this.$refs.form.validate(valid =&gt; {<font></font>
          this.$emit("on-validate", valid, this.form);<font></font>
          resolve(valid);<font></font>
        });<font></font>
      });<font></font>
    },<font></font>
    validateField(prop) {<font></font>
      this.$refs.form.validateField(prop);<font></font>
    }<font></font>
  }<font></font>
};<font></font>
&lt;/script&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门达蒙</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用禁用提交事件：</font></font></strong></p>

<pre><code>&lt;form @submit.prevent=""&gt;
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，当您需要提交表单时，请使用以下内容：</font></font></strong></p>

<pre><code>&lt;button type="submit" @click="mySubmitMethod"&gt; Send &lt;/button&gt;
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝猿路易</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用此： </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的HTML</font></font></p>

<pre><code>&lt;form name="..." @submit.prevent="onSubmitMethod"&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JS</font></font></p>

<pre><code>methods: {<font></font>
  onSubmitMethod() {<font></font>
<font></font>
  }<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">番长西里神无</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以执行Vue.js 1.0：</font></font></p>

<pre><code>&lt;input type="text" @keyup.enter.prevent="addCategory"&gt;
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">ItachiJinJin</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为什么不只是禁用表单提交？</font></font></p>

<pre><code>&lt;form v-on:submit.prevent&gt;&lt;input .../&gt;&lt;/form&gt;
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
