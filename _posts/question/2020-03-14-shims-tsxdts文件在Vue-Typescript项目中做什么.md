---
layout: question
title:  shims-tsx.d.ts文件在Vue-Typescript项目中做什么？
date:   2020-03-14T10:26:19.000Z
description: 使用TypeScript创建Vue项目时，包含两个声明文件：shims-vue.d.ts和shims.tsx.d.ts。//shims-vue.d.tsdecl...
img: 
author: GreenNear
category: question
answer: 1
tags: TypeScript Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用TypeScript创建Vue项目时，包含两个声明文件：</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">shims-vue.d.ts</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">shims.tsx.d.ts</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<pre><code>//shims-vue.d.ts<font></font>
<font></font>
declare module "*.vue" {<font></font>
  import Vue from 'vue';<font></font>
  export default Vue;<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和：</font></font></p>

<pre><code>//shims-tsx.d.ts<font></font>
<font></font>
import Vue, { VNode } from 'vue';<font></font>
<font></font>
declare global {<font></font>
  namespace JSX {<font></font>
    // tslint:disable no-empty-interface<font></font>
    interface Element extends VNode {}<font></font>
    // tslint:disable no-empty-interface<font></font>
    interface ElementClass extends Vue {}<font></font>
    interface IntrinsicElements {<font></font>
      [elem: string]: any;<font></font>
    }<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在创建一个小项目（没有Vue CLI）时，我忘记包含第二个项目（shims.tsx.d.ts），并且我的项目可以编译并按预期运行（没有错误）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我发现了与此相关的帖子：</font></font><a href="https://github.com/vuejs/vue-cli/issues/1198" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> :
 </font><a href="https://github.com/vuejs/vue-cli/issues/1198" rel="noreferrer"><font style="vertical-align: inherit;">//github.com/vuejs/vue-cli/issues/1198</font></a><font style="vertical-align: inherit;">，但希望对此进行更多说明。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我很好奇这个文件的作用以及为什么包含它？</font><font style="vertical-align: inherit;">换句话说，如果我不包括此声明文件，我将不得不“破坏”我的应用程序。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">谢谢！</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1619篇《shims-tsx.d.ts文件在Vue-Typescript项目中做什么？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Davaid神奇Eva</span>
            <span class="discuss-time">2020.03.14</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第一个文件可帮助您的IDE理解以什么结尾的文件</font></font><code>.vue</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">第二个文件允许您使用</font></font><code>.tsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件，同时</font></font><code>jsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在IDE中</font><font style="vertical-align: inherit;">启用</font><font style="vertical-align: inherit;">语法</font><font style="vertical-align: inherit;">支持</font><font style="vertical-align: inherit;">以编写JSX样式的 TypeScript代码。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
