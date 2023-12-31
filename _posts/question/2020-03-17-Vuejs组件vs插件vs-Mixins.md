---
layout: question
title:  Vue.js：组件vs.插件vs. Mixins
date:   2020-03-17T07:01:36.000Z
description: 以下两者之间到底有什么区别（何时使用）：Vue组件Vue插件Vue Mixins...
img: 
author: 乐米亚
category: question
answer: 1
tags: vue.js Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以下两者之间到底有什么区别（何时使用）：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Vue组件</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Vue插件</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Vue Mixins</font></font></li>
</ul></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1875篇《Vue.js：组件vs.插件vs. Mixins》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">西门泡芙Jim</span>
            <span class="discuss-time">2020.03.17</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">组件是元素。</font><font style="vertical-align: inherit;">它们就像您将用来构建应用程序或UI的功能和布局块。</font><font style="vertical-align: inherit;">可以扩展组件，这样做可以使用原始组件的各个方面，同时还可以添加其他功能。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与扩展现有组件类似，您可以使用mixin，它非常类似于您要扩展的组件，但是它向现有组件添加了功能。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">插件添加了可以由任何组件访问的顶级功能。</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用途取决于您要实现的目标。</font><font style="vertical-align: inherit;">路由和状态管理之类的内容非常适合插件使用，因为它允许您在不设置道具或侦听器的情况下影响/监听应用程序中的更改。</font><font style="vertical-align: inherit;">但是您不会将它们用于特定于组件的功能，因为它们会污染您的应用程序。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Mixins是一个有争议的功能，有些人不应该使用它。</font><font style="vertical-align: inherit;">这个想法是组件包装或高阶组件可以以更可靠的方式实现。</font><font style="vertical-align: inherit;">更多信息在这里：（</font></font><a href="https://reactjs.org/blog/2016/07/13/mixins-considered-harmful.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://reactjs.org/blog/2016/07/13/mixins-considered-harmful.html</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这些组件是构建vue应用程序的基础，因此您无法随意使用它们，但是有一些方法可以使您获得更多收益。</font><font style="vertical-align: inherit;">Vue允许使用插槽，该插槽有助于覆盖某些功能，而React社区更喜欢高阶组件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您是Vue的新手，我建议您不要使用mixins，请不要使用Plugins，直到使用组件来实现功能时再花时间，如果您要使用作用域插槽来创建可重用的组件，则建议您。  </font></font><a href="https://vuejs.org/v2/guide/components-slots.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://vuejs.org/v2/guide/components-slots.html</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
