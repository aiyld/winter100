---
layout: question
title:  Vue.jsTypeScriptthis。$ refs。<refField> .value不存在
date:   2020-03-16T07:29:28.000Z
description: 用TypeScript重写VueJs项目时，遇到了TypeScript错误。这是具有自定义v模型的组件的一部分。html中的输入字段有一个称为“ plate”的...
img: 
author: 神奇飞云
category: question
answer: 4
tags: JavaScript Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用TypeScript重写VueJs项目时，遇到了TypeScript错误。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是具有自定义v模型的组件的一部分。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">html中的输入字段有一个称为“ plate”的引用，我想访问该值。</font><font style="vertical-align: inherit;">该字段上的@input调用下面编写的update方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TypeScript抱怨板上没有价值。 </font></font></p>

<pre><code>@Prop() value: any;<font></font>
<font></font>
update() {<font></font>
    this.$emit('input',<font></font>
        plate: this.$refs.plate.value<font></font>
    });<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模板：</font></font></p>

<pre><code>&lt;template&gt;  <font></font>
&lt;div&gt;<font></font>
    &lt;div class="form-group"&gt;<font></font>
        &lt;label for="inputPlate" class="col-sm-2 control-label"&gt;Plate&lt;/label&gt;<font></font>
<font></font>
        &lt;div class="col-sm-10"&gt;<font></font>
            &lt;input type="text" class="form-control" id="inputPlate" ref="plate" :value="value.plate" @input="update"&gt;<font></font>
        &lt;/div&gt;<font></font>
    &lt;/div&gt;<font></font>
<font></font>
&lt;/div&gt;<font></font>
&lt;/template&gt;<font></font>
</code></pre></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第1805篇《Vue.jsTypeScriptthis。$ refs。<refField> .value不存在》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚猴子</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果是自定义组件方法调用，</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们可以键入该组件的名称，因此很容易引用该方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如</font></font></p>

<pre><code>(this.$refs.annotator as AnnotatorComponent).saveObjects();
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">其中AnnotatorComponent是基于类的vue组件，如下所示。</font></font></p>

<pre><code>@Component<font></font>
export default class AnnotatorComponent extends Vue {<font></font>
    public saveObjects() {<font></font>
        // Custom code<font></font>
    }<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">JinJin猴子</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也许对某人有用。</font><font style="vertical-align: inherit;">它看起来更漂亮，并保持类型支持。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">HTML：</font></font></p>

<pre><code>&lt;input ref="inputComment" v-model="inputComment"&gt;
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TS：</font></font></p>

<pre><code>const inputValue = ((this.$refs.inputComment as Vue).$el as HTMLInputElement).value;
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Mandy宝儿</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以上答案均不适用于我想做的事情。</font><font style="vertical-align: inherit;">添加以下$ refs属性可以修复该问题，并且似乎可以恢复预期的属性。</font><font style="vertical-align: inherit;">我在</font><a href="https://github.com/vuejs/vue-class-component/issues/94#issuecomment-298813210" rel="nofollow noreferrer"><font style="vertical-align: inherit;">此github帖子</font></a><font style="vertical-align: inherit;">上找到了链接的解决方案</font></font><a href="https://github.com/vuejs/vue-class-component/issues/94#issuecomment-298813210" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></a></p>

<pre><code>class YourComponent extends Vue {<font></font>
  $refs!: {<font></font>
    vue: Vue,<font></font>
    element: HTMLInputElement,<font></font>
    vues: Vue[],<font></font>
    elements: HTMLInputElement[]<font></font>
  }<font></font>
<font></font>
  someMethod () {<font></font>
    this.$refs.&lt;element&gt;.&lt;attribute&gt;<font></font>
  }<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva西里蛋蛋</span>
            <span class="discuss-time">2020.03.16</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">你可以这样做：</font></font></p>

<pre><code>class YourComponent extends Vue {<font></font>
  $refs: {<font></font>
    checkboxElement: HTMLFormElement<font></font>
  }<font></font>
<font></font>
  someMethod () {<font></font>
    this.$refs.checkboxElement.checked<font></font>
  }<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从此问题开始：</font><a href="https://github.com/vuejs/vue-class-component/issues/94" rel="noreferrer"><font style="vertical-align: inherit;">https</font></a><font style="vertical-align: inherit;"> : </font></font><a href="https://github.com/vuejs/vue-class-component/issues/94" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/vuejs/vue-class-component/issues/94</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
