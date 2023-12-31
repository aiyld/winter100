---
layout: question
title:  当Node.js内部仍依赖于Threads时，其固有速度如何？
date:   2020-03-19T03:20:22.000Z
description: 我刚刚观看了以下视频：Node.js简介，但仍然不了解如何获得速度优势。主要是在某一点上，Ryan Dahl（Node.js的创建者）说Node.js...
img: 
author: 小胖蛋蛋
category: question
answer: 4
tags: JavaScript Node.js
topic: Node.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我刚刚观看了以下视频：</font></font><a href="http://www.yuiblog.com/blog/2010/05/20/video-dahl/" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js简介</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，但仍然不了解如何获得速度优势。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">主要是在某一点上，Ryan Dahl（Node.js的创建者）说Node.js是基于事件循环的，而不是基于线程的。</font><font style="vertical-align: inherit;">线程很昂贵，只应留给并行编程专家使用。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">稍后，他然后展示了Node.js的体系结构堆栈，该体系结构堆栈具有基础的C实现，该实现在内部具有自己的线程池。</font><font style="vertical-align: inherit;">因此，显然，Node.js开发人员永远不会启动自己的线程或直接使用线程池...他们使用异步回调。</font><font style="vertical-align: inherit;">我很明白。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不明白的是，Node.js仍在使用线程...只是在隐藏实现，因此，如果50个人很好地请求50个文件（当前不在内存中），那么不需要50个线程，这样做会更快吗？ ？</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">唯一的区别是，由于它是在内部进行管理的，因此Node.js开发人员不必对线程详细信息进行编码，而是在其下方仍在使用线程来处理IO（阻止）文件请求。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，您难道不是真的只遇到一个问题（线程）并在该问题仍然存在时将其隐藏：主要是多个线程，上下文切换，死锁等吗？  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">必须有一些我仍然不明白的细节。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第2292篇《当Node.js内部仍依赖于Threads时，其固有速度如何？》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">路易斯丁神奇</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">线程仅用于处理没有异步功能的函数，例如</font></font><code>stat()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该</font></font><code>stat()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">函数始终处于阻塞状态，因此node.js需要使用一个线程来执行实际的调用而不会阻塞主线程（事件循环）。</font><font style="vertical-align: inherit;">潜在地，如果您不需要调用那些函数，则永远不会使用线程池中的任何线程。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GreenSamA</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我不明白的是，Node.js仍在使用线程。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Ryan将线程用于阻塞的部分（大部分node.js使用非阻塞IO），因为某些部分难以编写非阻塞的疯狂。</font><font style="vertical-align: inherit;">但是我相信Ryan希望一切都畅通无阻。</font><font style="vertical-align: inherit;">在</font></font><a href="http://s3.amazonaws.com/four.livejournal/20091117/jsconf.pdf" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">幻灯片63（内部设计）上，</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您看到Ryan将</font></font><a href="http://software.schmorp.de/pkg/libev.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">libev</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（抽象化异步事件通知的库）用于非阻塞</font></font><a href="http://en.wikipedia.org/wiki/Event_loop" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">eventloop</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">由于事件循环，node.js需要较少的线程，从而减少了上下文切换，内存消耗等。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阿飞阳光</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意！</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个老答案。</font><font style="vertical-align: inherit;">尽管在粗略轮廓中仍然是正确的，但是由于Node在过去几年中的快速发展，某些细节可能已更改。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用线程是因为：</font></font></p>

<ol>
<li><font style="vertical-align: inherit;"></font><a href="http://fixunix.com/linux/401454-aio_read-write-versus-o_nonblock-linux-context.html" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">open（）</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font><a href="http://fixunix.com/linux/401454-aio_read-write-versus-o_nonblock-linux-context.html" rel="noreferrer"><font style="vertical-align: inherit;">O_NONBLOCK选项不适用于files</font></a><font style="vertical-align: inherit;">。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有些第三方库不提供非阻塞IO。</font></font></li>
</ol>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">要伪造非阻塞IO，必须使用线程：在单独的线程中阻塞IO。</font><font style="vertical-align: inherit;">这是一个丑陋的解决方案，并导致大量开销。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在硬件级别甚至更糟：</font></font></p>

<ul>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过</font></font><a href="http://en.wikipedia.org/wiki/Direct_memory_access" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">DMA</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，CPU异步卸载IO。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">数据直接在IO设备和存储器之间传输。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">内核将其包装在一个同步的阻塞系统调用中。</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Node.js将阻塞的系统调用包装在一个线程中。</font></font></li>
</ul>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这只是愚蠢而低效的。</font><font style="vertical-align: inherit;">但这至少有效！</font><font style="vertical-align: inherit;">我们可以享受Node.js，因为它隐藏了事件驱动的异步体系结构背后的丑陋而繁琐的细节。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">也许将来有人会为文件实现O_NONBLOCK？</font></font></p>

<p><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编辑：</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我与一个朋友讨论了这个问题，他告诉我，线程的替代方法是使用</font></font><a href="http://linux.die.net/man/2/select" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">select进行</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">轮询</font><font style="vertical-align: inherit;">：将超时指定为0并在返回的文件描述符上执行IO（现在保证它们不会阻塞）。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿理查德</span>
            <span class="discuss-time">2020.03.19</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">实际上，这里合并了一些不同的东西。</font><font style="vertical-align: inherit;">但这始于模因，即线程真的很难。</font><font style="vertical-align: inherit;">因此，如果它们很困难，则使用线程的可能性更大：1）由于错误而中断，2）不能尽可能高效地使用它们。</font><font style="vertical-align: inherit;">（2）是您要问的那个。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">考虑一下他提供的示例之一，其中有一个请求进入，您运行了一些查询，然后对结果进行一些处理。</font><font style="vertical-align: inherit;">如果您以标准的程序方式编写代码，则代码可能如下所示：</font></font></p>

<pre><code>result = query( "select smurfs from some_mushroom" );<font></font>
// twiddle fingers<font></font>
go_do_something_with_result( result );<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果传入的请求导致您创建了一个运行上述代码的新线程，则您将有一个线程坐在那里，而在</font></font><code>query()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行</font><font style="vertical-align: inherit;">时则什么也不做</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">（根据Ryan所说，Apache正在使用一个线程来满足原始请求，而在他所说的情况下，nginx的性能要好于后者，因为它不是。）</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，如果您真的很聪明，则可以在运行查询时以一种可能导致环境崩溃并执行其他操作的方式来表示上面的代码：</font></font></p>

<pre><code>query( statement: "select smurfs from some_mushroom", callback: go_do_something_with_result() );
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">基本上，这就是node.js的工作。</font><font style="vertical-align: inherit;">您基本上是在进行装饰（由于语言和环境的原因，因此很方便，因此要考虑闭包的要点），因此您的代码可以使环境对运行的内容和时间有所了解。</font><font style="vertical-align: inherit;">这样，node.js </font><font style="vertical-align: inherit;">在发明异步I / O（并不是有人声称这样）的意义上</font><font style="vertical-align: inherit;">并不是</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">新</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的，但是它的表达方式却有所不同。  </font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">注意：当我说环境可以在何时运行时变得很聪明时，我的意思是说它用来启动一些I / O的线程现在可以用来处理其他请求或可以完成的某些计算并行，或启动其他并行I / O。</font><font style="vertical-align: inherit;">（我不确定节点是否足够成熟，可以为同一请求启动更多工作，但是您明白了。）</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
