---
layout: question
title:  vue.js $ watch对象数组
date:   2020-03-12T02:25:25.000Z
description: mounted  function() {  this.$watch('things', function(){console.log('a thing...
img: 
author: 猿路易
category: question
answer: 1
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><pre><code>mounted: function() {<font></font>
  this.$watch('things', function(){console.log('a thing changed')}, true);<font></font>
}<font></font>
</code></pre>

<p><code>things</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> 是一组对象 </font></font><code>[{foo:1}, {foo:2}]</code></p>

<p><code>$watch</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">检测何时添加或删除对象，而不检测何时更改对象上的值。</font><font style="vertical-align: inherit;">我怎样才能做到这一点？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第880篇《vue.js $ watch对象数组》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易卡卡西</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果有人需要获取在数组内更改的项目，请检查它：</font></font></p>

<p><a href="https://jsfiddle.net/jonatan2m/h7sm7wbr/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSFiddle示例</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">帖子示例代码：</font></font></p>

<pre><code>new Vue({<font></font>
  ...<font></font>
  watch: {<font></font>
    things: {<font></font>
      handler: function (val, oldVal) {<font></font>
        var vm = this;<font></font>
        val.filter( function( p, idx ) {<font></font>
            return Object.keys(p).some( function( prop ) {<font></font>
                var diff = p[prop] !== vm.clonethings[idx][prop];<font></font>
                if(diff) {<font></font>
                    p.changed = true;                        <font></font>
                }<font></font>
            })<font></font>
        });<font></font>
      },<font></font>
      deep: true<font></font>
    }<font></font>
  },<font></font>
  ...<font></font>
})<font></font>
</code></pre></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
