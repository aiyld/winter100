---
layout: post
title:  基于vite2.x+electron13快速搭建仿MacOS桌面应用EXE程序
date:   2021-06-28T08:29:03.000Z
description: 前段时间有分享一个vite2+electron桌面端管理后台项目。这次分享的是基于vue3+electron13+element-plus仿mac桌面管理程序|...
img: 
author: xiaoyan2021
category: blog
answer: 0
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p>前段时间有分享一个<a href="https://juejin.cn/post/6963310387945013261">vite2+electron桌面端管理后台</a>项目。这次分享的是基于vue3+electron13+element-plus仿mac桌面管理程序|electron跨端桌面UI框架。</p><p><a href="https://juejin.cn/post/6977298346905960456/">electron-macos</a> 基于vite.js搭建的一款跨端仿mac桌面。使用了最新前端技术栈vite2+vue3+electron13+element-plus+echarts等技术开发。支持经典dock菜单、多开窗体等功能。</p><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868245762.png"></figure><p>&nbsp;</p><h2>使用技术</h2><ul><li>编辑器：Vscode</li><li>框架技术：Vite2.3.4+Vue3.0.11+Vuex4+VueRouter@4</li><li>跨端框架：Electron13.0.1</li><li>打包工具：vue-cli-plugin-electron-builder</li><li>UI组件库：Element-Plus^1.0.2 (饿了么vue3组件库)</li><li>弹窗组件：MacLayer (vue3弹窗v3layer改进版)</li><li>图表组件：Echarts^5.1.1</li><li>模拟请求：Mockjs1.1.0</li></ul><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868334480.png"></figure><p>&nbsp;</p><h2>功能特点</h2><p>✅经典的图标+dock菜单模式</p><p>✅流畅的操作体验</p><p>✅可拖拽桌面+dock菜单</p><p>✅符合macOS big sur操作窗口管理</p><p>✅丰富的视觉效果，自定义桌面壁纸</p><p>✅可视化创建多窗口，支持拖拽/缩放/最大化，可传入自定义组件页面。</p><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868369529..gif"></figure><p>&nbsp;</p><h2>项目目录</h2><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868385496.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868430885.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868443499.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868451840.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868462829.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868469036.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868477757.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868488982.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868502296.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868514690.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868523753.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868535249.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868544690.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868554730.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868561211.png"></figure><p>&nbsp;</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868567627.png"></figure><p>&nbsp;</p><h2>桌面模板</h2><p>菜单栏位于屏幕顶部。程序坞Dock菜单位于屏幕底部。位于二者之间的称为桌面。</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868635382.png"></figure><pre><code class="language-typescript">&lt;template&gt;
    &lt;div class="macui__wrapper" :style="{'--themeSkin': store.state.skin}"&gt;
        &lt;div v-if="!route.meta.isNewin" class="macui__layouts-main flexbox flex-col"&gt;
            &lt;!-- //顶部导航 --&gt;
            &lt;div class="layout__topbar"&gt;
                &lt;TopNav /&gt;
            &lt;/div&gt;
            
            &lt;div class="layout__workpanel flex1 flexbox" @contextmenu="handleCtxMenu"&gt;
                &lt;div class="panel__mainlayer flex1 flexbox" style="margin-bottom: 70px;"&gt;
                    &lt;DeskMenu /&gt;
                &lt;/div&gt;
            &lt;/div&gt;

            &lt;!-- //底部Dock菜单 --&gt;
            &lt;Dock /&gt;
        &lt;/div&gt;
        &lt;router-view v-else class="macui__layouts-main flexbox flex-col macui__filter"&gt;&lt;/router-view&gt;
    &lt;/div&gt;
&lt;/template&gt;</code></pre><p>&nbsp;</p><h2>vue3实现dock效果</h2><p>底部的dock菜单使用了css3实现动画效果。</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868754670..gif"></figure><pre><code class="language-typescript">&lt;template&gt;
    &lt;div class="macui__dock"&gt;
        &lt;div class="macui__dock-wrap macui__filter" ref="dockRef"&gt;
            &lt;a class="macui__dock-item"&gt;&lt;span class="tooltips"&gt;appstore&lt;/span&gt;&lt;img src="/static/mac/appstore.png" /&gt;&lt;/a&gt;
            &lt;a class="macui__dock-item active"&gt;&lt;span class="tooltips"&gt;launchpad&lt;/span&gt;&lt;img src="/static/mac/launchpad.png" /&gt;&lt;/a&gt;
            ...
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/template&gt;</code></pre><p>&nbsp;</p><pre><code class="language-typescript">.macui__deskmenu {display: flex; flex-direction: column; flex-wrap: wrap;}
.macui__deskmenu-box {height: 90px;}
.macui__deskmenu-item {border: 1px solid transparent; border-radius: 15px; color: #fff; cursor: pointer; display: flex; align-items: center; flex-direction: column; margin: 10px 0 0 10px; padding: 4px 0; width: 70px; transition: background-color .3s, border-color .3s;}
.macui__deskmenu-item:hover {background: rgba(255,255,255,.15); border-color: rgba(255, 255, 255, .2);}
.macui__deskmenu-item img {height: 40px; width: 40px; object-fit: cover;}
.macui__deskmenu-item .title {display: block; margin-top: 4px; padding: 0 8px; word-break: break-all; text-align: center;}</code></pre><p>&nbsp;</p><h2>vue3实现仿mac弹窗效果</h2><p>如下图：项目中的弹窗是基于vue3自定义组件实现。支持超过30+参数自定义配置。</p><figure class="image"><img src="https://www.samyoc.com/uploads/users/26987/images/1624868854717.png"></figure><pre><code class="language-typescript">// 引入组件页面
import Home from '@/views/home.vue'

v3layer({
    type: 'component',
    content: Home,
    ...
})</code></pre><p>&nbsp;</p><pre><code class="language-typescript">// 引入frame页面
v3layer({
    type: 'iframe',
    content: 'https://cn.vitejs.dev/',
    ...
})</code></pre><p>&nbsp;</p><p>好了。基于Electron+Vue3开发桌面应用就分享到这里。希望对大家有些帮助！</p><p>&nbsp;</p><p>&nbsp;</p><p>&nbsp;</p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4285篇《基于vite2.x+electron13快速搭建仿MacOS桌面应用EXE程序》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    
    </div>
    {% endraw %}
  </div>
<div>
