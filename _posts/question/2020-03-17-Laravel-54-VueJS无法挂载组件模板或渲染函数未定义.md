---
layout: question
title:  Laravel 5.4 Vue.JS无法挂载组件：模板或渲染函数未定义
date:   2020-03-17T07:05:59.000Z
description: 从Vue.js开始，想尝试一下laravel附带的示例。没有显示任何组件，并且在控制台中我得到了\[Vue warn\]  Failed to mou...
img: 
author: 小哥Green小哥
category: question
answer: 1
tags: laravel Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从Vue.js开始，想尝试一下laravel附带的示例。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有显示任何组件，并且在控制台中我得到了</font></font></p>

<pre><code>[Vue warn]: Failed to mount component: template or render function not defined.<font></font>
<font></font>
found in<font></font>
<font></font>
---&gt; &lt;Example&gt;<font></font>
   &lt;Root&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不是全新安装，从5.2-&gt; 5.3-&gt; 5.4升级</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">资源/资产/js/app.js</font></font></p>

<pre><code>/**<font></font>
 * First we will load all of this project's JavaScript dependencies which<font></font>
 * includes Vue and other libraries. It is a great starting point when<font></font>
 * building robust, powerful web applications using Vue and Laravel.<font></font>
 */<font></font>
<font></font>
require('./bootstrap');<font></font>
<font></font>
window.Vue = require('vue');<font></font>
<font></font>
/**<font></font>
 * Next, we will create a fresh Vue application instance and attach it to<font></font>
 * the page. Then, you may begin adding components to this application<font></font>
 * or customize the JavaScript scaffolding to fit your unique needs.<font></font>
 */<font></font>
Vue.component('example', require('./components/Example.vue'));<font></font>
<font></font>
const app = new Vue({<font></font>
    el: '#app'<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">资源/资产/js/components/Example.vue</font></font></p>

<pre><code>&lt;template&gt;<font></font>
&lt;div class="container"&gt;<font></font>
    &lt;div class="row"&gt;<font></font>
        &lt;div class="col-md-8 col-md-offset-2"&gt;<font></font>
            &lt;div class="panel panel-default"&gt;<font></font>
                &lt;div class="panel-heading"&gt;Example Component&lt;/div&gt;<font></font>
<font></font>
                &lt;div class="panel-body"&gt;<font></font>
                    I'm an example component!<font></font>
                &lt;/div&gt;<font></font>
            &lt;/div&gt;<font></font>
        &lt;/div&gt;<font></font>
    &lt;/div&gt;<font></font>
&lt;/div&gt;<font></font>
&lt;/template&gt;<font></font>
<font></font>
&lt;script&gt;<font></font>
    export default {<font></font>
        mounted() {<font></font>
            console.log('Component mounted.')<font></font>
        }<font></font>
    }<font></font>
&lt;/script&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我拥有js的刀片</font></font></p>

<pre><code>&lt;!DOCTYPE html&gt;<font></font>
&lt;html lang="en"&gt;<font></font>
&lt;head&gt;<font></font>
    &lt;meta charset="UTF-8"&gt;<font></font>
    &lt;title&gt;Testing&lt;/title&gt;<font></font>
    &lt;link rel="stylesheet" href="css/app.css"&gt;<font></font>
    &lt;meta name="csrf-token" content="{{ csrf_token() }}"&gt;<font></font>
&lt;/head&gt;<font></font>
    &lt;body&gt;<font></font>
    &lt;div id="app"&gt;<font></font>
        &lt;example&gt;&lt;/example&gt;<font></font>
    &lt;/div&gt;<font></font>
        &lt;script src="js/app.js" charset="utf-8"&gt;&lt;/script&gt;<font></font>
    &lt;/body&gt;<font></font>
&lt;/html&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">webpack.mix.js</font></font></p>

<pre><code>let mix = require('laravel-mix');<font></font>
<font></font>
mix.js('resources/assets/js/app.js', 'public/js')<font></font>
    .sass('resources/assets/sass/app.scss', 'public/css');<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1884篇《Laravel 5.4 Vue.JS无法挂载组件：模板或渲染函数未定义》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Green阿飞泡芙</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">删除文件夹node_modules</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行npm install </font></font></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将以下行添加到package.json</font></font></p>

<pre><code>"webpack": "cross-env NODE_ENV=development webpack --progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js"
</code></pre></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm运行webpack</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">npm run watch</font></font></p></li>
<li><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不要改变其他任何东西 </font></font></p></li>
</ul></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
