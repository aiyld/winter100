---
layout: question
title:  Vue.js Vuetify，用Jest运行我的第一个单元测试的问题
date:   2020-04-03T03:48:20.000Z
description: 这是我的第一个测试：Heading.spec.js    import Vuetify from "vuetify";    import { ...
img: 
author: 西门GO村村
category: question
answer: 1
tags: 单元测试 Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是我的第一个测试：</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Heading.spec.js</font></font></strong></p>

<pre><code>    import Vuetify from "vuetify";<font></font>
    import { shallowMount, createLocalVue } from "@vue/test-utils";<font></font>
    import router from "@/router";<font></font>
    import i18n from "@/locales";<font></font>
    import Heading from "@/components/Home/Heading.vue";<font></font>
<font></font>
    describe("Heading.vue", () =&gt; {<font></font>
      let wrapper;<font></font>
<font></font>
      beforeEach(() =&gt; {<font></font>
        const localVue = createLocalVue()<font></font>
        localVue.use(router)<font></font>
        localVue.use(Vuetify)<font></font>
        localVue.filter("translate", function(value) {<font></font>
          if (!value) return "";<font></font>
          value = "lang.views.global." + value.toString();<font></font>
          return i18n.t(value);<font></font>
        });<font></font>
<font></font>
        wrapper = shallowMount(Heading, { localVue: localVue, router, i18n });<font></font>
      });<font></font>
<font></font>
      it("should contains default heading", () =&gt; {<font></font>
        console.log ('WRAPPER: ', wrapper)<font></font>
        // const heading = wrapper.find("h1");<font></font>
        // expect(heading.text()).toContain("In the heart of Charentes...");<font></font>
      });<font></font>
    });<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当我运行它时，出现Vuetify错误...</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">console.log</font></font></p>

<pre><code>    vue-cli-service test:unit<font></font>
<font></font>
     PASS  tests/unit/Heading.spec.js (11.247s)<font></font>
      Heading.vue<font></font>
        ✓ should contains default heading (462ms)<font></font>
<font></font>
      console.log tests/unit/Heading.spec.js:23<font></font>
        WRAPPER:  undefined<font></font>
<font></font>
      console.error node_modules/vuetify/dist/vuetify.js:19429<font></font>
        [Vuetify] Multiple instances of Vue detected<font></font>
        See https://github.com/vuetifyjs/vuetify/issues/4068<font></font>
<font></font>
        If you're seeing "$attrs is readonly", it's caused by this<font></font>
<font></font>
      console.error node_modules/vuetify/dist/vuetify.js:19429<font></font>
        [Vuetify] Multiple instances of Vue detected<font></font>
        See https://github.com/vuetifyjs/vuetify/issues/4068<font></font>
<font></font>
        If you're seeing "$attrs is readonly", it's caused by this<font></font>
<font></font>
      console.error node_modules/vue/dist/vue.runtime.common.js:589<font></font>
        [Vue warn]: Invalid prop: type check failed for prop "src". Expected String, got Object.<font></font>
<font></font>
        found in<font></font>
<font></font>
        ---&gt; &lt;VParallax&gt;<font></font>
               &lt;Heading&gt;<font></font>
                 &lt;Root&gt;<font></font>
<font></font>
    Test Suites: 1 passed, 1 total<font></font>
    Tests:       1 passed, 1 total<font></font>
    Snapshots:   0 total<font></font>
    Time:        17.641s<font></font>
    Ran all test suites.<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为什么我会检测到多个Vue实例？</font><font style="vertical-align: inherit;">在我的测试中定义了一次……就这些了？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">测试通过了，但是我不理解Vuetify的错误..感谢您的反馈</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第3987篇《Vue.js Vuetify，用Jest运行我的第一个单元测试的问题》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">缺啥补啥</span>
            <span class="discuss-time">2020.04.28</span>
          </div>
          <div class="discuss-comment"><p>修改 webpack.render.config.js:</p><blockquote><pre><code class="language-plaintext">let whiteListedModules = ['vue'];</code></pre></blockquote><p>&nbsp;</p><p>为：</p><blockquote><p><i>let</i> whiteListedModules = ['vue', 'vuetify'];</p></blockquote><p>然后从新npm run dev即可</p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
