---
layout: question
title:  我应该为Node.js和MySQL使用哪个ORM？\[关闭\]
date:   2020-03-18T08:55:25.000Z
description:                                                                          ...
img: 
author: Stafan小宇宙
category: question
answer: 3
tags: mysql Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><aside class="s-notice s-notice__info js-post-notice mb16" aria-hidden="false" role="status">
            <div class="grid fd-column fw-nowrap"> 
                <div class="grid fw-nowrap">
                        <div class="grid--cell mr8">
                            <svg aria-hidden="true" class="svg-icon iconLightbulb" width="18" height="18" viewBox="0 0 18 18"><path d="M9.5.5a.5.5 0 0 0-1 0v.25a.5.5 0 0 0 1 0V.5zm5.6 2.1a.5.5 0 0 0-.7-.7l-.25.25a.5.5 0 0 0 .7.7l.25-.25zM1 7.5c0-.28.22-.5.5-.5H2a.5.5 0 0 1 0 1h-.5a.5.5 0 0 1-.5-.5zm14.5 0c0-.28.22-.5.5-.5h.5a.5.5 0 0 1 0 1H16a.5.5 0 0 1-.5-.5zM2.9 1.9c.2-.2.5-.2.7 0l.25.25a.5.5 0 1 1-.7.7L2.9 2.6a.5.5 0 0 1 0-.7z" fill-opacity=".4"></path><path opacity=".4" d="M7 16h4v1a1 1 0 0 1-1 1H8a1 1 0 0 1-1-1v-1z" fill="#3F3F3F"></path><path d="M15 8a6 6 0 0 1-3.5 5.46V14a1 1 0 0 1-1 1h-3a1 1 0 0 1-1-1v-.54A6 6 0 1 1 15 8zm-4.15-3.85a.5.5 0 0 0-.7.7l2 2a.5.5 0 0 0 .7-.7l-2-2z" fill="#FFC166"></path></svg>
                        </div>
                    <div class="grid--cell fl1 lh-lg">
                        <div class="grid--cell fl1 lh-lg"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">
                            按照目前的情况，这个问题并不适合我们的问答形式。</font><font style="vertical-align: inherit;">我们希望答案得到事实，参考或专业知识的支持，但是这个问题可能会引起辩论，争论，民意调查或扩展讨论。</font><font style="vertical-align: inherit;">如果您认为此问题可以解决并且可以重新提出，</font></font><a href="/help/reopen-questions"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请访问帮助中心</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">以获取指导。
                            
                        </font></font></div>
                    </div>
                </div>
                                <div class="grid--cell mb0 mt8"><font style="vertical-align: inherit;"></font><span title="2012-05-06 12：43：37Z" class="relativetime"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">7年前</font></font></span><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关闭</font><font style="vertical-align: inherit;">。</font></font></div>
            </div>
                    </aside>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在重写一个项目以使用Node.js。</font><font style="vertical-align: inherit;">我想继续使用MySQL作为数据库（即使我不介意重写架构）。</font><font style="vertical-align: inherit;">我正在寻找一种易于使用，性能合理的ORM，它支持缓存，多对一和多对多关系。</font><font style="vertical-align: inherit;">从MySQL ORM中我可以发现，</font></font><a href="https://github.com/coresmart/persistencejs"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">persistencejs</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="http://sequelizejs.com"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">sequelize</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">似乎是最成熟的。</font><font style="vertical-align: inherit;">您是否有经验？</font><font style="vertical-align: inherit;">我在决策中应注意哪些利弊？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2075篇《我应该为Node.js和MySQL使用哪个ORM？\[关闭\]》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Sequelize和Persistence.js之间的主要区别是前者支持一种</font></font><code>STRING</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据类型，即</font></font><code>VARCHAR(255)</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">做一切我真感到不自在</font></font><code>TEXT</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">ADavaid</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">首先，请注意，我没有使用过任何一个（但是使用过Node.js）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这两个库都有很好的文档记录，并具有稳定的API。</font><font style="vertical-align: inherit;">但是，persistence.js似乎</font></font><a href="http://persistencejs.org/users" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在更多项目中使用</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">我不知道他们是否仍然使用它。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">sequelize的开发者有时会在</font></font><a href="http://blog.depold.com" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">blog.depold.com上发布</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有关此问题的博客</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果您想将主键用作外键，则需要</font></font><a href="http://www.hiddentao.com/archives/2011/11/18/primary-key-foreign-key-improvements-to-sequelize-date-js-alternatives/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此博客文章中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">描述的补丁</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果您需要persistence.js的帮助，可以使用专门的Google小组。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从我收集的示例中，续集比persistance.js有点像JavaScript（更多糖），但是支持较少的数据存储（仅MySQL，而persistance.js甚至可以使用浏览器内存储）。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我认为续集可能是您的最佳选择，因为您只需要MySQL支持。</font><font style="vertical-align: inherit;">但是，如果您需要一些方便的功能（例如搜索），或者以后想要使用其他数据库，则需要使用persistence.js。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村小小十三</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我会选择</font></font><a href="http://sequelizejs.com/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Sequelize，</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因为它的文档很好。</font><font style="vertical-align: inherit;">这只是一个诚实的看法（我从没真正将MySQL与Node一起使用那么多）。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
