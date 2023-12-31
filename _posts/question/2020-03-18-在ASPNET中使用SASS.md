---
layout: question
title:  在ASP.NET中使用SASS
date:   2020-03-18T07:38:17.000Z
description:                                                                          ...
img: 
author: 老丝小卤蛋
category: question
answer: 5
tags: ass.net CSS
topic: CSS
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
                                <div class="grid--cell mb0 mt8"><font style="vertical-align: inherit;"></font><span title="2012-11-26 16：22：23Z" class="relativetime"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">7年前</font></font></span><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">关闭</font><font style="vertical-align: inherit;">。</font></font></div>
            </div>
                    </aside>
<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在研究</font><font style="vertical-align: inherit;">在ASP.NET环境中使用Ruby HAML包中的</font></font><a href="http://haml.hamptoncatlin.com/docs/rdoc/classes/Sass.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SASS</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（语法上很棒的StyleSheets）的方法。</font><font style="vertical-align: inherit;">理想情况下，我希望将SASS文件编译为CSS是构建过程中的一个无缝部分。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">进行集成的最佳方法是什么？</font><font style="vertical-align: inherit;">另外，还有其他CSS生成工具更适合.NET环境吗？</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2017篇《在ASP.NET中使用SASS》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">逆天小小</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它不是SASS，但您可以看看我们</font></font><a href="http://www.dotlesscss.org/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的.NET</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">端口的</font><a href="http://www.dotlesscss.org/" rel="noreferrer"><font style="vertical-align: inherit;">Less Css</font></a><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">指南针看起来真的很有趣，我认为Less这类的东西会是一个很好的补充。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">村村GO</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我昨天才发现这一点，它看起来非常有前景，除了sass / scss之外，它还可以处理JS（尚未CSS）和文件组合的自动最小化。</font><font style="vertical-align: inherit;">我希望的一件事是为外面的人创建一个VS插件，用于编辑sass / scss文件。</font><font style="vertical-align: inherit;">我确实发现了一个问题，那就是当您的sass / scss代码出错时，您只会发现它在测试或检查生成的CSS文件。</font><font style="vertical-align: inherit;">我没有尽全力，但是到目前为止还不错。  </font></font></p>

<p><a href="https://github.com/xpaulbettsx/SassAndCoffee" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">https://github.com/xpaulbettsx/SassAndCoffee</font></font></a> </p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Sam凯小卤蛋</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为了在Visual Studio中获得更好的工作体验，可以安装</font><font style="vertical-align: inherit;">开始支持Sass（SCSS语法）</font><font style="vertical-align: inherit;">的最新版本的</font></font><a href="http://vswebessentials.com/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Web Essential</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><br><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或者，您可以安装</font></font><a href="http://visualstudiogallery.msdn.microsoft.com/85fa99a6-e4c6-4a1c-9f00-e6a8129b6f4d" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Sassy Studio</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><a href="http://www.mindscapehq.com/products/web-workbench" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Web Workbench</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，要在ASP.NET项目中编译.sass / .scss文件，有一些不同的工具：通过</font></font><a href="http://vswebessentials.com/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Web Essential</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><a href="http://www.mindscapehq.com/products/web-workbench" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Web Workbench</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><a href="https://github.com/hcatlin/sassc" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SassC</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><a href="http://libsassnet.codeplex.com/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Sass.Net</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><a href="http://compass-style.org/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Compass</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><a href="https://github.com/xpaulbettsx/SassAndCoffee" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SassAndCoffee</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> ...</font></font></p>

<hr>

<p><a href="http://vswebessentials.com/" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Web Essential</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是Visual Studio的功能齐全的插件，它确实为所有前端内容提供了更好的体验。</font><font style="vertical-align: inherit;">最新版本开始支持Sass（SCSS语法）。</font><font style="vertical-align: inherit;">在内部，它使用Libsass将SCSS编译为CSS。</font></font></p>

<hr>

<p><a href="http://www.mindscapehq.com/products/web-workbench" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Web Workbench</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是Visual Studio的另一个插件，它添加了语法突出显示，智能和其他一些用于编辑SCSS文件的有用内容。</font><font style="vertical-align: inherit;">它还可以将您的代码编译为普通或精简的CSS。</font><font style="vertical-align: inherit;">在内部，它使用了Ruby Sass编译器的包装版本。</font></font></p>

<hr>

<p><a href="http://visualstudiogallery.msdn.microsoft.com/85fa99a6-e4c6-4a1c-9f00-e6a8129b6f4d" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Sassy Studio</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：Visual Studio的另一个插件。</font><font style="vertical-align: inherit;">功能较少，但重量较轻。</font></font></p>

<hr>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><a href="https://github.com/hcatlin/libsass" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Libsass库</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是萨斯CSS预编译器（开发中仍然）的C ++接口。</font><font style="vertical-align: inherit;">原始版本是用Ruby编写的，但是此版本旨在提高效率和可移植性。</font><font style="vertical-align: inherit;">该库力求轻便，简单，易于构建，并与各种平台和语言集成。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Libsass库周围有几个包装器：</font></font></p>

<ul>
<li><a href="https://github.com/hcatlin/sassc" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SassC</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：命令行编译器（在Windows上，您需要使用MsysGit编译SassC的源代码以获取sassc.exe）。</font></font></li>
<li><a href="https://github.com/TBAPI-0KA/NSass" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">NSass</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：.Net包装器。</font></font></li>
<li><a href="https://github.com/andrew/node-sass" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node-Sass</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：在Node.js上使用Libsass。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">等等</font></font></li>
</ul>

<hr>

<p><a href="http://compass-style.org/" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Compass</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是Sass的框架，它添加了许多有用的帮助程序（例如图像拼接），并且还可以编译SCSS / Sass。</font><font style="vertical-align: inherit;">但是，您需要在需要编译样式的每个开发环境上安装Ruby。</font></font></p>

<hr>

<p><a href="https://github.com/xpaulbettsx/SassAndCoffee" rel="noreferrer"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">SassAndCoffee</font></font></strong></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是一个通过一些DLL和配置添加SCSS / Sass编译和最小化支持的软件包。</font><font style="vertical-align: inherit;">与Web Workbench编译器相比，它的优势在于它是独立包含在Visual Studio解决方案中的：您无需在每个开发环境上都安装插件。</font><font style="vertical-align: inherit;">备注：SassAndCoffee并不经常更新，并且由于它使用IronRuby来包装正式的Ruby编译器，因此可能会遇到一些性能问题。</font><font style="vertical-align: inherit;">您可以通过</font></font><a href="http://nuget.org/packages/SassAndCoffee" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"> Nuget软件包</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">安装最新版本</font><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Eva梅</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我刚刚编写了一个Visual Studio加载项，其中包含详细说明，包括有关如何使Sass进入Visual Studio的屏幕截图。</font><font style="vertical-align: inherit;">在这里查看-http: </font></font><a href="http://giri.sh/2011/01/21/sass-for-visual-studio-2010/"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//giri.sh/2011/01/21/sass-for-visual-studio-2010/</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">前端LEYLEY</span>
            <span class="discuss-time">2020.03.18</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该罗盘项目具有一个编译器，它将您的Sass编译为CSS。</font><font style="vertical-align: inherit;">它可以在Windows上运行，但是在该平台上没有经过很好的测试。</font><font style="vertical-align: inherit;">如果您发现任何与平台相关的错误，我们将很乐意帮助您修复它们。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">指南针可以在这里找到：</font><a href="http://github.com/chriseppstein/compass" rel="noreferrer"><font style="vertical-align: inherit;">http</font></a><font style="vertical-align: inherit;"> : </font></font><a href="http://github.com/chriseppstein/compass" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//github.com/chriseppsein/compass</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
