---
layout: question
title:  Vue.js将函数作为prop传递，并使子对象使用数据进行调用
date:   2020-03-12T06:06:32.000Z
description: 我有一个帖子列表组件和一个帖子组件。我传递了一种从帖子列表调用帖子组件的方法，因此当单击按钮时，它将被调用。 但是我想在单击此功能时传递帖子ID...
img: 
author: 古一梅
category: question
answer: 0
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个帖子列表组件和一个帖子组件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我传递了一种从帖子列表调用帖子组件的方法，因此当单击按钮时，它将被调用。 </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是我想在单击此功能时传递帖子ID</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">码：</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>let PostsFeed = Vue.extend({<font></font>
    data: function () {<font></font>
        return {<font></font>
          posts: [....]<font></font>
        }<font></font>
    },<font></font>
    template: `<font></font>
      &lt;div&gt;<font></font>
        &lt;post v-for="post in posts" :clicked="clicked" /&gt;<font></font>
      &lt;/div&gt;<font></font>
    `,<font></font>
    methods: {<font></font>
      clicked: function(id) {<font></font>
        alert(id);<font></font>
      }<font></font>
    }<font></font>
  }<font></font>
                           <font></font>
  let Post = Vue.extend({<font></font>
    props: ['clicked'],<font></font>
    data: function () {<font></font>
        return {}<font></font>
    },<font></font>
    template: `<font></font>
      &lt;div&gt;<font></font>
        &lt;button @click="clicked" /&gt;<font></font>
      &lt;/div&gt;<font></font>
    `<font></font>
}</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正如您在“发布”组件中看到的那样，您单击了运行从道具获得的方法的单击，我想向该方法添加一个变量。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你是怎样做的？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第973篇《Vue.js将函数作为prop传递，并使子对象使用数据进行调用》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
