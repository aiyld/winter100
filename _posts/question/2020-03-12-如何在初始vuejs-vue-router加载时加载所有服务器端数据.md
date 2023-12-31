---
layout: question
title:  如何在初始vue.js / vue-router加载时加载所有服务器端数据？
date:   2020-03-12T03:02:36.000Z
description: 我目前正在使用WordPress REST API和vue-router在小型单页站点上的页面之间进行转换。但是，当我使用REST API对服务器进行AJ...
img: 
author: 樱
category: question
answer: 1
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我目前正在使用WordPress REST API和vue-router在小型单页站点上的页面之间进行转换。</font><font style="vertical-align: inherit;">但是，当我使用REST API对服务器进行AJAX调用时，数据将加载，但仅在页面已呈现之后才加载。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><a href="https://router.vuejs.org/en/advanced/data-fetching.html" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">VUE路由器文档</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">提供了深入了解在关于如何前和导航到各航线后加载数据，但我想知道如何加载在初始页面加载的所有路线和页面数据，绕过需要每个负载数据激活路线的时间。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意，我正在将数据加载到</font></font><code>acf</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">属性中，然后使用来在</font></font><code>.vue</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">文件组件中</font><font style="vertical-align: inherit;">访问它</font></font><code>this.$parent.acfs</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">main.js路由器代码：</font></font></strong></p>

<pre><code>const router = new VueRouter({<font></font>
    routes: [<font></font>
        { path: '/', component: Home },<font></font>
        { path: '/about', component: About },<font></font>
        { path: '/tickets', component: Tickets },<font></font>
        { path: '/sponsors', component: Sponsors },<font></font>
    ],<font></font>
    hashbang: false<font></font>
});<font></font>
<font></font>
exports.router = router;<font></font>
<font></font>
const app = new Vue({<font></font>
    router,<font></font>
    data: {<font></font>
        acfs: ''<font></font>
    },<font></font>
    created() {<font></font>
        $.ajax({<font></font>
            url: 'http://localhost/placeholder/wp-json/acf/v2/page/2',<font></font>
            type: 'GET',<font></font>
            success: function(response) {<font></font>
                console.log(response);<font></font>
                this.acfs = response.acf;<font></font>
                // this.backgroundImage = response.acf.background_image.url<font></font>
            }.bind(this)<font></font>
        })<font></font>
    }<font></font>
}).$mount('#app')<font></font>
</code></pre>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Home.vue组件代码：</font></font></strong></p>

<pre><code>export default {<font></font>
    name: 'about',<font></font>
    data () {<font></font>
        return {<font></font>
            acf: this.$parent.acfs,<font></font>
        } <font></font>
    },<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有任何想法吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第918篇《如何在初始vue.js / vue-router加载时加载所有服务器端数据？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Sam神乐番长</span>
            <span class="discuss-time">2020.03.12</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用</font></font><a href="https://router.vuejs.org/en/advanced/navigation-guards.html" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">导航卫士</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在特定组件上，它看起来像这样：</font></font></p>

<pre><code>export default {<font></font>
    beforeRouteEnter (to, from, next) {<font></font>
        // my ajax call<font></font>
    }<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您还可以向所有组件添加导航保护：</font></font></p>

<pre><code>router.beforeEach((to, from, next) =&gt; {<font></font>
    // my ajax call<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要记住的一件事是导航保护是异步的，因此您需要</font></font><code>next()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在数据加载完成后</font><font style="vertical-align: inherit;">调用</font><font style="vertical-align: inherit;">回调。</font><font style="vertical-align: inherit;">我的应用程序中的一个真实示例（保护功能位于单独的文件中）：</font></font></p>

<pre><code>export default function(to, from, next) {<font></font>
    Promise.all([<font></font>
        IngredientTypes.init(),<font></font>
        Units.init(),<font></font>
        MashTypes.init()<font></font>
    ]).then(() =&gt; {<font></font>
        next();<font></font>
    });<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在你的情况，你需要调用</font></font><code>next()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font><code>success</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">回调，当然。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
