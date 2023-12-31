---
layout: question
title:  Vue.js $ children按组件名称
date:   2020-03-12T07:24:43.000Z
description: 我正在尝试通过名称访问特定的孩子。此刻，由于孩子的位置，我以此称呼孩子：this.$root.$children\[0\]只要那个孩子一直都是可以的...
img: 
author: 猪猪Harry
category: question
answer: 5
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在尝试通过名称访问特定的孩子。</font><font style="vertical-align: inherit;">此刻，由于孩子的位置，我以此称呼孩子：</font></font></p>

<pre><code>this.$root.$children[0]
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只要那个孩子一直都是可以的，</font></font><code>[0]</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是如果有一种方法可以做到，那就太好了：</font></font></p>

<pre><code>this.$root.$children['detail']
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我一直认为这</font></font><code>$refs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可能是解决我的问题的方法，但永远找不到找到帮助我的方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有任何想法吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1052篇《Vue.js $ children按组件名称》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小哥Tony</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您不一定需要</font></font><code>$refs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，实际上，如果您具有深层嵌套的组件，则有时它们是不可行的。</font><font style="vertical-align: inherit;">在搜索时，我已经多次找到该问答，但是由于我经常遇到这种情况，因此最终决定实施自己的解决方案。</font><font style="vertical-align: inherit;">不要对老式循环感到厌恶，它们有两个原因是必要的，因为</font><font style="vertical-align: inherit;">在我推动的每个迭代中</font><font style="vertical-align: inherit;">，我都会测试</font></font><code>x&lt;descendants.length</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（而不是预先设置诸如</font></font><code>len=descendants.length</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">测试之类的</font><font style="vertical-align: inherit;">东西</font><font style="vertical-align: inherit;">）在第二个for循环中进入堆栈。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一，用法：</font></font></p>

<pre><code>let unPersonalizable = matchingDescendants(this, /a.checkimprintfiinformation$/, {first: true});
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实现方式：</font></font></p>

<pre><code>function matchingDescendants(vm, matcher, options) {<font></font>
    let descendants = vm.$children;<font></font>
    let descendant;<font></font>
    let returnFirst = (options || {}).first;<font></font>
    let matches = [];<font></font>
<font></font>
    for (let x=0; x&lt;descendants.length; x++) {<font></font>
        descendant = descendants[x];<font></font>
<font></font>
        if (matcher.test(descendant.$vnode.tag)) {<font></font>
            if (returnFirst) {<font></font>
                return descendant;<font></font>
            }<font></font>
            else {<font></font>
                matches.push(descendant);<font></font>
            }<font></font>
        }<font></font>
<font></font>
        for (let y=0, len = descendant.$children.length; y&lt;len; y++) {<font></font>
            descendants.push(descendant.$children[y]);<font></font>
        }    <font></font>
    }<font></font>
<font></font>
    return matches.length === 0 ? false : matches;<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">神乐小宇宙Gil</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有内容几乎相同，但是在Vue 2中，您需要使用：</font></font><code>&lt;details ref="detailsChild"&gt;&lt;/details&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而不是v-ref。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您需要做的就是使用</font></font><code>this.$refs.detailsChild;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，您可以访问它的任何属性。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易猴子Pro</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><pre><code>this.$root.$children[0].constructor.name
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Tom阳光</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用以下属性：</font></font></p>

<pre><code>this.$root.$children[0].$options.name
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如：</font></font></p>

<pre><code>this.$root.$children.find(child =&gt; { return child.$options.name === "name"; });
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">理查德Near</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您所说的这个孩子真的是您要从中访问组件的孩子吗？</font><font style="vertical-align: inherit;">在这种情况下，</font></font><code>v-ref</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">确实是答案：</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="false" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>// in the code of the parent component, access the referenced child component like this:<font></font>
<font></font>
this.$refs.detailsChild</code></pre>
<pre class="snippet-code-html lang-html prettyprint-override"><code>&lt;!-- Template of the parent component, assuming your child Component is called Details --&gt;<font></font>
&lt;details v-ref:details-child&gt;&lt;/details&gt;</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">相关API文档：</font><a href="http://vuejs.org/api/#v-ref" rel="noreferrer"><font style="vertical-align: inherit;">http</font></a><font style="vertical-align: inherit;"> : </font></font><a href="http://vuejs.org/api/#v-ref" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//vuejs.org/api/#v-ref</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
