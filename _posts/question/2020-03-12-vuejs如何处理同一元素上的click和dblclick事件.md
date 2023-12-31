---
layout: question
title:  vue.js：如何处理同一元素上的click和dblclick事件
date:   2020-03-12T09:43:04.000Z
description: 我有一个vue组件，具有click / dblclik的单独事件。单击（取消）选择行，dblclick打开编辑表单。<ul class="data_r...
img: 
author: 梅十三
category: question
answer: 1
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个vue组件，具有click / dblclik的单独事件。</font><font style="vertical-align: inherit;">单击（取消）选择行，dblclick打开编辑表单。</font></font></p>

<pre><code>&lt;ul class="data_row"<font></font>
  v-for="(row,index) in gridData"<font></font>
  @dblclick="showEditForm(row,$event)"<font></font>
  @click="rowSelect(row,$event)"<font></font>
&gt;<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这样做，双击会触发3个事件。</font><font style="vertical-align: inherit;">两个单击事件，最后一个dblclick。</font><font style="vertical-align: inherit;">由于click事件首先触发，是否有办法（将click事件推迟固定的毫秒数）以阻止double上click事件的传播？</font></font></p>

<p><font style="vertical-align: inherit;"><a href="https://jsfiddle.net/kjtkzgvp/" rel="noreferrer"><font style="vertical-align: inherit;">在这里</font></a><font style="vertical-align: inherit;">摆弄</font></font><a href="https://jsfiddle.net/kjtkzgvp/" rel="noreferrer"><font style="vertical-align: inherit;"></font></a></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1236篇《vue.js：如何处理同一元素上的click和dblclick事件》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞GO</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为我有一个更简单的解决方案（我正在使用vue类，但适用相同的原则）：</font></font></p>

<pre><code>private timeoutId = null;<font></font>
onClick() {<font></font>
        if(!this.timeoutId)<font></font>
        {<font></font>
            this.timeoutId = setTimeout(() =&gt; {<font></font>
                // simple click<font></font>
            }, 50);//tolerance in ms<font></font>
        }else{<font></font>
            clearTimeout(this.timeoutId);<font></font>
            // double click<font></font>
        }<font></font>
    }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它不需要计算点击次数。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
