---
layout: question
title:  Vue.js v-html contenteditable防止dom刷新以防止光标/插入符跳转
date:   2020-03-16T02:07:38.000Z
description: For reference I'm using Vue 2.0, Vuex, and Firebase.I am building a content...
img: 
author: 樱古一
category: question
answer: 2
tags: Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p>For reference I'm using Vue 2.0, Vuex, and Firebase.</p>

<p>I am building a contenteditable component using the v-html binding to render the innerHTML. The data is updated onKeyUp. Whenever the data is updated the DOM element refreshes with the "new" data, causing the caret / cursor to jump back to the beginning of the contenteditable div.</p>

<p>I have looked into Rangy and a few other stackoverflow solutions, but I feel the easiest solution would be to unbind the DOM element from the data refresh. I would like for the data to still update in firebase but not result in an element refresh. </p>

<p>Is there a way for me to still use v-html but prevent the DOM element from refreshing with the data? Or is there another way to render the HTML without auto binding?</p>

<p><strong>Edit: 11/18/16</strong></p>

<p>So I’ve continued to work on a fix for this. Here are my current ideas.</p>

<ol>
<li>Use a <a href="https://vuejs.org/v2/guide/instance.html#Lifecycle-Diagram" rel="noreferrer">lifecycle hook</a> and stop component re-render. I’ve looked through the Vue docs but can’t seem to find something to stop the cycle.</li>
<li>Use something like <a href="https://facebook.github.io/react/docs/react-component.html#shouldcomponentupdate" rel="noreferrer">React’s “componentShouldRender”</a>. Again, it doesn’t look like Vue.js has a comparable method in the lifecycle.</li>
</ol>

<p>If anybody knows of any methods to end the lifecycle, stop re-render, or a way to get React's "componentShouldRender" functionality out of vue, that should be enough fix this issue.</p>

<p>-</p>

<p><strong>Update: 11/29/16</strong></p>

<p>This update is a little late coming. I've logged a <a href="https://github.com/vuejs/vue/issues/4255" rel="noreferrer">feature request</a> with Vue on Github. </p>

<p>There are a few JSFiddles in the issue discussion which could provide a <a href="https://jsfiddle.net/9upfskLy/" rel="noreferrer">potential solution</a>. However none of them I believe qualifies as a complete solution. The only promising one has recently yielded <a href="https://stackoverflow.com/questions/40877280/vue-js-force-re-render-of-component-which-contains-v-once-directive">more issues</a>. </p>

<p>All of these problems would be non-issues with the addition of a <code>componentShouldRender</code> lifecycle hook. I will continue to look for a complete solution</p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1665篇《Vue.js v-html contenteditable防止dom刷新以防止光标/插入符跳转》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞飞云</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有没有办法让我仍然使用v-html但阻止DOM元素刷新数据？</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是。</font><font style="vertical-align: inherit;">该</font></font><code>v-once</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指令正是这样做的。</font></font></p>

<p><a href="https://vuejs.org/v2/api/#v-once" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://vuejs.org/v2/api/#v-once</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Davaid番长</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">据我了解，问题在于事件传播或冒泡，从而使vue重新渲染div，从而导致十字体跳到其开头。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在您的小提琴示例中</font></font><code>event.preventDeafault();</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font><code>setContent()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法</font><font style="vertical-align: inherit;">内</font><font style="vertical-align: inherit;">添加</font><font style="vertical-align: inherit;">行即可</font><font style="vertical-align: inherit;">完成工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关更多详细信息</font></font><a href="https://vuejs.org/v2/guide/events.html#Methods-in-Inline-Handlers" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">-vue文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中“内联处理程序”中的方法部分</font><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
