---
layout: question
title:  ReactJS-.JS与.JSX
date:   2020-03-11T03:38:52.000Z
description: 在工作时，我感到有些困惑React。互联网上有很多示例，它们使用.js具有React的文件，但还有许多其他示例使用.jsx文件。我已阅读过有关.j...
img: 
author: 
category: question
answer: 6
tags: reactjs React.js
topic: React.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在工作时，我感到有些困惑</font></font><code>React</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">互联网上有很多示例，它们使用</font></font><code>.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">具有React的文件，但还有许多其他</font><font style="vertical-align: inherit;">示例</font><font style="vertical-align: inherit;">使用</font></font><code>.jsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我已阅读过有关</font></font><code>.jsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件的信息，据我了解，它们只是让您在文件中编写html标签</font></font><code>javascript</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">但是同样的事情也可以写在</font></font><code>.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件中。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">那么究竟是什么这两个分机之间的实际差异</font></font><code>.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>.jsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第606篇《ReactJS-.JS与.JSX》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">老丝乐</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSX不是标准的JavaScript，根据Airbnb样式指南“ eslint”可以考虑采用这种模式 </font></font></p>

<pre><code>// filename: MyComponent.js<font></font>
function MyComponent() {<font></font>
  return &lt;div /&gt;;<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为警告，如果您将文件命名为MyComponent.jsx，它将通过，除非您编辑eslint规则，您可以在</font><a href="https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-filename-extension.md" rel="nofollow noreferrer"><font style="vertical-align: inherit;">此处</font></a><font style="vertical-align: inherit;">查看样式指南</font></font><a href="https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-filename-extension.md" rel="nofollow noreferrer"><font style="vertical-align: inherit;"></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">YOC43564555</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在大多数情况下，只需要Transpiler / bundler，可能未配置为与JSX文件一起使用，而与JS一起使用！</font><font style="vertical-align: inherit;">因此，您不得不使用JS文件而不是JSX。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而且由于react只是javascript的库，因此您可以在JSX或JS之间进行选择。</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它们是完全可以互换的！</font></font></strong></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在某些情况下，由于代码突出显示，用户/开发人员也可能选择JSX而不是JSX，但是大多数较新的编辑器也在JS文件中正确查看react语法。 </font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱小胖Mandy</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">除了提到的JSX标签不是标准javascript的事实之外，我使用.jsx扩展名的原因是因为Emmet仍然可以在编辑器中使用-您知道，有用的插件可将html代码扩展，例如ul&gt; li到</font></font></p>

<pre><code>&lt;ul&gt;<font></font>
  &lt;li&gt;&lt;/li&gt;<font></font>
&lt;/ul&gt;<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙Stafan</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSX标签（</font></font><code>&lt;Component/&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">）显然不是标准的javascript，</font></font><code>&lt;script&gt;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">例如，</font><font style="vertical-align: inherit;">如果将它们放在裸</font><font style="vertical-align: inherit;">标签</font><font style="vertical-align: inherit;">内，则没有特殊含义</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">因此，包含它们的所有React文件都是JSX而不是JS。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">按照惯例，React应用程序的入口点通常是.js而不是.jsx，即使它包含React组件。</font><font style="vertical-align: inherit;">也可以是.jsx。</font><font style="vertical-align: inherit;">其他任何JSX文件通常都具有.jsx扩展名。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无论如何，存在歧义的原因是因为最终扩展名并不重要，因为编译器只要实际上是JSX，便会愉快地压缩任何类型的文件。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我的建议是：不要担心。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易Green</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">正如其他提到的那样，</font></font><code>JSX</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它不是标准的Javascript扩展。</font><font style="vertical-align: inherit;">最好基于来命名Application的入口点，</font></font><code>.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于其余组件，可以使用</font></font><code>.jsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我有一个重要原因，为什么要使用</font></font><code>.JSX</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有组件的文件名。</font><font style="vertical-align: inherit;">实际上，在具有大量代码的大规模项目中，如果我们将所有React的组件都设置为具有</font></font><code>.jsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">扩展名，那么在项目中导航至不同的javascript文件（例如助手，中间件等）时会更容易。一个React Component，而不是其他类型的javascript文件。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁Jim</span>
            <span class="discuss-time">2020.03.11</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件扩展名没有。</font><font style="vertical-align: inherit;">打包器/编译器/无论做什么，都将负责解决存在的文件内容类型。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，在确定要放入</font><font style="vertical-align: inherit;">文件</font></font><code>.js</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>.jsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件类型中的内容</font><font style="vertical-align: inherit;">时还需要考虑其他一些因素</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">由于JSX不是标准的JavaScript，因此可以说，任何非“普通” JavaScript的内容都应加入自己的扩展名</font><font style="vertical-align: inherit;">，例如</font></font><code>.jsx</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JSX和</font></font><code>.ts</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">TypeScript。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这里有一个</font></font><a href="https://github.com/airbnb/javascript/pull/985" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">很好的讨论可供阅读</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
