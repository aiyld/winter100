---
layout: question
title:  短路Array.forEach就像调用break
date:   2020-03-09T12:47:37.000Z
description: \[1,2,3\].forEach(function(el) {    if(el === 1) break;});如何使用forEachJavaS...
img: 
author: 逆天Green古一
category: question
answer: 22
tags: JavaScript
topic: JavaScript
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><pre><code>[1,2,3].forEach(function(el) {<font></font>
    if(el === 1) break;<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用</font></font><code>forEach</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JavaScript中</font><font style="vertical-align: inherit;">的新</font><font style="vertical-align: inherit;">方法</font><font style="vertical-align: inherit;">执行此操作</font><font style="vertical-align: inherit;">？</font><font style="vertical-align: inherit;">我试过</font></font><code>return;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>return false;</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><code>break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font><code>break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">崩溃，</font></font><code>return</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">除了继续迭代外什么也不做。</font></font></p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第256篇《短路Array.forEach就像调用break》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小哥番长番长</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p>Yes it is possible to continue and to exit of a forEach loop.</p>

<p>To continue, you can use return, the loop will continue but the current function will end.</p>

<p>To exit of the loop, you can set the third parameter to 0 length, set to empty array. The loop will not continue, the current function do, so you can use "return" to finish, like exit in a normal for loop...</p>

<p>This:</p>

<pre><code>[1,2,3,4,5,6,7,8,9,10].forEach((a,b,c) =&gt; {<font></font>
    console.log(a);<font></font>
    if(b == 2){return;}<font></font>
    if(b == 4){c.length = 0;return;}<font></font>
    console.log("next...",b);<font></font>
});<font></font>
</code></pre>

<p>will print this:</p>

<pre><code>1<font></font>
next... 0<font></font>
2<font></font>
next... 1<font></font>
3<font></font>
4<font></font>
next... 3<font></font>
5<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">宝儿前端</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><pre><code>var array = [1,2,3,4];<font></font>
<font></font>
for(var item of array){<font></font>
    console.log(item);<font></font>
    if(item == 2){<font></font>
       break;<font></font>
    }<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">伽罗小哥</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">尝试使用“查找”：</font></font></p>

<pre><code>var myCategories = [<font></font>
 {category: "start", name: "Start", color: "#AC193D"},<font></font>
 {category: "action", name: "Action", color: "#8C0095"},<font></font>
 {category: "exit", name: "Exit", color: "#008A00"}<font></font>
];<font></font>
<font></font>
function findCategory(category) {<font></font>
  return myCategories.find(function(element) {<font></font>
    return element.category === category;<font></font>
  });<font></font>
}<font></font>
<font></font>
console.log(findCategory("start"));<font></font>
// output: { category: "start", name: "Start", color: "#AC193D" }<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">null</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果需要根据情况中断数组中元素的值（例如，中断条件不依赖于在分配数组元素值后可能会更改的运行时变量），也可以使用组合的</font></font><a href="https://www.w3schools.com/jsref/jsref_slice_array.asp" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">切片（）</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://www.w3schools.com/jsref/jsref_indexof_array.asp" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的indexOf（）</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如下。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您需要在forEach到达“ Apple”时休息一下，可以使用</font></font></p>

<pre><code>var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];<font></font>
var fruitsToLoop = fruits.slice(0, fruits.indexOf("Apple"));<font></font>
// fruitsToLoop = Banana,Orange,Lemon<font></font>
<font></font>
fruitsToLoop.forEach(function(el) {<font></font>
    // no need to break<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如</font></font><a href="https://www.w3schools.com/jsref/jsref_slice_array.asp" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">W3Schools.com中</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所述，slice（）方法将数组中选定的元素作为新的数组对象返回。</font><font style="vertical-align: inherit;">原始阵列将不会更改。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在</font><a href="https://jsfiddle.net/ula/6djbwh1c/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">JSFiddle</font></a><font style="vertical-align: inherit;">中</font></font><a href="https://jsfiddle.net/ula/6djbwh1c/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">查看</font></font></a></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">希望它能帮助某人</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">三千曜米亚</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以创建一个变种</font></font><code>forEach</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它允许</font></font><code>break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>continue</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><code>return</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">甚至</font></font><code>async</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">/ </font></font><code>await</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：（例如写在 TypeScript）</font></font></p>

<pre><code>export type LoopControlOp = "break" | "continue" | ["return", any];<font></font>
export type LoopFunc&lt;T&gt; = (value: T, index: number, array: T[])=&gt;LoopControlOp;<font></font>
<font></font>
Array.prototype.ForEach = function ForEach&lt;T&gt;(this: T[], func: LoopFunc&lt;T&gt;) {<font></font>
    for (let i = 0; i &lt; this.length; i++) {<font></font>
        const controlOp = func(this[i], i, this);<font></font>
        if (controlOp == "break") break;<font></font>
        if (controlOp == "continue") continue;<font></font>
        if (controlOp instanceof Array) return controlOp[1];<font></font>
    }<font></font>
};<font></font>
<font></font>
// this variant lets you use async/await in the loop-func, with the loop "awaiting" for each entry<font></font>
Array.prototype.ForEachAsync = async function ForEachAsync&lt;T&gt;(this: T[], func: LoopFunc&lt;T&gt;) {<font></font>
    for (let i = 0; i &lt; this.length; i++) {<font></font>
        const controlOp = await func(this[i], i, this);<font></font>
        if (controlOp == "break") break;<font></font>
        if (controlOp == "continue") continue;<font></font>
        if (controlOp instanceof Array) return controlOp[1];<font></font>
    }<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用法：</font></font></p>

<pre><code>function GetCoffee() {<font></font>
    const cancelReason = peopleOnStreet.ForEach((person, index)=&gt; {<font></font>
        if (index == 0) return "continue";<font></font>
        if (person.type == "friend") return "break";<font></font>
        if (person.type == "boss") return ["return", "nevermind"];<font></font>
    });<font></font>
    if (cancelReason) console.log("Coffee canceled because: " + cancelReason);<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阳光阿飞</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以按照以下适用于我的代码进行操作：</font></font></p>

<pre><code> var     loopStop = false;<font></font>
YOUR_ARRAY.forEach(function loop(){<font></font>
    if(loopStop){ return; }<font></font>
    if(condition){ loopStop = true; }<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">米亚小哥斯丁</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这不是最有效的，因为您仍然循环所有元素，但是我认为可能值得考虑非常简单的一点：</font></font></p>

<pre><code>let keepGoing = true;<font></font>
things.forEach( (thing) =&gt; {<font></font>
  if (noMore) keepGoing = false;<font></font>
  if (keepGoing) {<font></font>
     // do things with thing<font></font>
  }<font></font>
});<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">JimAGil</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">使用该</font></font><code>array.prototype.every</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">函数，该函数为您提供了打破循环的实用程序。</font><font style="vertical-align: inherit;">请参阅此处的示例</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Mozilla开发人员网络上的Javascript文档</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">小小Stafan宝儿</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我知道这是不正确的方法。</font><font style="vertical-align: inherit;">这不是打破循环。</font><font style="vertical-align: inherit;">这是一个神态
</font></font></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>let result = true;<font></font>
[1, 2, 3].forEach(function(el) {<font></font>
    if(result){<font></font>
      console.log(el);<font></font>
      if (el === 2){<font></font>
        result = false;<font></font>
      }<font></font>
    }<font></font>
});</code></pre>
</div>
</div>
<p></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">泡芙古一神无</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我</font><font style="vertical-align: inherit;">为此</font><font style="vertical-align: inherit;">使用</font></font><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">nullhack</font></font></em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它尝试访问的属性</font></font><code>null</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这是一个错误：</font></font></p>

<pre><code>try {<font></font>
  [1,2,3,4,5]<font></font>
  .forEach(<font></font>
    function ( val, idx, arr ) {<font></font>
      if ( val == 3 ) null.NULLBREAK;<font></font>
    }<font></font>
  );<font></font>
} catch (e) {<font></font>
  // e &lt;=&gt; TypeError: null has no properties<font></font>
}<font></font>
//<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">TomDavaid</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另一种方法</font></font></p>

<pre><code>        var wageType = types.filter(function(element){<font></font>
            if(e.params.data.text == element.name){ <font></font>
                return element;<font></font>
            }<font></font>
        });<font></font>
        console.dir(wageType);<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">猿阿飞Tom</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果不需要在迭代后访问数组，则可以通过将数组的长度设置为0来纾困。如果在迭代后仍然需要它，则可以使用slice克隆它。</font></font></p>

<pre><code>[1,3,4,5,6,7,8,244,3,5,2].forEach(function (item, index, arr) {<font></font>
  if (index === 3) arr.length = 0;<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或使用克隆：</font></font></p>

<pre><code>var x = [1,3,4,5,6,7,8,244,3,5,2];<font></font>
<font></font>
x.slice().forEach(function (item, index, arr) {<font></font>
  if (index === 3) arr.length = 0;<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与在代码中引发随机错误相比，这是一个更好的解决方案。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">十三Tony伽罗</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这是一个for循环，但是像forEach（）一样在循环中维护对象引用，但是您可以将其拆分。</font></font></p>

<pre><code>var arr = [1,2,3];<font></font>
for (var i = 0, el; el = arr[i]; i++) {<font></font>
    if(el === 1) break;<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Near神乐路易</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这只是我想出的解决问题的方法...我很确定它可以解决原始申请者所遇到的问题：</font></font></p>

<pre><code>Array.prototype.each = function(callback){<font></font>
    if(!callback) return false;<font></font>
    for(var i=0; i&lt;this.length; i++){<font></font>
        if(callback(this[i], i) == false) break;<font></font>
    }<font></font>
};<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">然后，您可以通过以下方式调用它：</font></font></p>

<pre><code>var myarray = [1,2,3];<font></font>
myarray.each(function(item, index){<font></font>
    // do something with the item<font></font>
    // if(item != somecondition) return false; <font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在回调函数中返回false将导致中断。</font><font style="vertical-align: inherit;">让我知道那是否实际上不起作用。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">蛋蛋神乐</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在另一个站点上找到了此解决方案。</font><font style="vertical-align: inherit;">您可以在try / catch场景中包装forEach。</font></font></p>

<pre><code>if(typeof StopIteration == "undefined") {<font></font>
 StopIteration = new Error("StopIteration");<font></font>
}<font></font>
<font></font>
try {<font></font>
  [1,2,3].forEach(function(el){<font></font>
    alert(el);<font></font>
    if(el === 1) throw StopIteration;<font></font>
  });<font></font>
} catch(error) { if(error != StopIteration) throw error; }<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">此处有更多详细信息：</font><a href="http://dean.edwards.name/weblog/2006/07/enum/" rel="nofollow noreferrer"><font style="vertical-align: inherit;">http</font></a><font style="vertical-align: inherit;"> : </font></font><a href="http://dean.edwards.name/weblog/2006/07/enum/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">//dean.edwards.name/weblog/2006/07/enum/</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">达蒙Davaid斯丁</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">简短答案：</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可用于此目的或更改代码以免破坏</font></font><code>forEach</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">不要使用</font></font><code>.some()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>.every()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">模仿</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">重写代码以避免</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">循环，或使用</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">每次您使用这些方法作为</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">替代</font><font style="vertical-align: inherit;">方法时，</font><font style="vertical-align: inherit;">上帝都会杀死小猫。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">长答案：</font></font></p>

<p><code>.some()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">并且</font></font><code>.every()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">都返回</font></font><code>boolean</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">值，</font></font><code>.some()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">返回</font></font><code>true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是否有针对任何元素传递函数返回时</font></font><code>true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，每一个回报</font></font><code>false</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，如果有针对任何元素传递函数返回</font></font><code>false</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">这就是功能的含义。</font><font style="vertical-align: inherit;">使用函数的含义并不比使用表而不是CSS差得多，因为使用函数会使每个阅读您代码的人感到沮丧。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">另外，使用这些方法作为</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">替代</font><font style="vertical-align: inherit;">方法的唯一可能方法</font><font style="vertical-align: inherit;">是产生副作用（在</font></font><code>.some()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">回调函数</font><font style="vertical-align: inherit;">外部更改一些var </font><font style="vertical-align: inherit;">），这与并无太大区别</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">因此，使用</font></font><code>.some()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">or </font></font><code>.every()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">循环替代品并不是没有副作用的，那么</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，这并</font><font style="vertical-align: inherit;">没有那么干净</font><font style="vertical-align: inherit;">，这令人沮丧，因此还不是更好。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您始终可以重写代码，这样就不需要了</font></font><code>for...break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">您可以使用筛选数组</font></font><code>.filter()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，可以使用</font></font><code>.slice()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">等</font><font style="vertical-align: inherit;">拆分数组</font><font style="vertical-align: inherit;">，然后</font><font style="vertical-align: inherit;">对数组的该部分</font><font style="vertical-align: inherit;">使用</font></font><code>.forEach()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><code>.map()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">A达蒙</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从您的代码示例中，</font></font><code>Array.prototype.find</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您正在寻找的是：</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Array.prototype.find（）</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">Array.prototype.findIndex（）</font></font></a> </p>

<pre><code>[1, 2, 3].find(function(el) {<font></font>
    return el === 2;<font></font>
}); // returns 2<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">斯丁宝儿</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">不幸的是在这种情况下，如果不使用它将更好</font></font><code>forEach</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">而是使用常规</font></font><code>for</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">循环，它现在将完全按照您的期望工作。</font></font></p>

<pre><code>var array = [1, 2, 3];<font></font>
for (var i = 0; i &lt; array.length; i++) {<font></font>
  if (array[i] === 1){<font></font>
    break;<font></font>
  }<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">梅老丝</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">引用以下</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">MDN文档中的内容</font></font><code>Array.prototype.forEach()</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有</font></font><strong><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">没有办法阻止或打破</font></font></em></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">一个</font></font><code>forEach()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">比抛出异常等循环。</font><font style="vertical-align: inherit;">如果您需要这种行为，则该</font></font><code>.forEach()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法是</font></font><strong><em><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">错误的工具</font></font></em></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，请改用普通循环。</font><font style="vertical-align: inherit;">如果要为谓词测试数组元素并且需要布尔返回值，则可以使用</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every" rel="noreferrer"><code>every()</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">或</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some" rel="noreferrer"><code>some()</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代替。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于@bobince建议的代码（在问题中），请</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some" rel="noreferrer"><code>Array.prototype.some()</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">改用。</font><font style="vertical-align: inherit;">它非常适合您的用例。</font></font></p>

<blockquote>
  <p><code>Array.prototype.some()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对数组中存在的每个元素执行一次回调函数，直到找到一个回调返回真值（转换为a的值）的值为止</font></font><code>Boolean</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">如果找到这样的元素，则</font></font><code>some()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">立即返回true。</font><font style="vertical-align: inherit;">否则，</font></font><code>some()</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">返回false。</font><font style="vertical-align: inherit;">仅对具有指定值的数组索引调用回调；</font><font style="vertical-align: inherit;">对于已删除或从未分配值的索引，不会调用它。</font></font></p>
</blockquote></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">GreenGil</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以使用</font></font><a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array/every" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">每种</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">方法：</font></font></p>

<pre><code>[1,2,3].every(function(el) {<font></font>
    return !(el === 1);<font></font>
});<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ES6</font></font></p>

<pre><code>[1,2,3].every( el =&gt; el !== 1 )
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于旧的浏览器支持，请使用：</font></font></p>

<pre><code>if (!Array.prototype.every)<font></font>
{<font></font>
  Array.prototype.every = function(fun /*, thisp*/)<font></font>
  {<font></font>
    var len = this.length;<font></font>
    if (typeof fun != "function")<font></font>
      throw new TypeError();<font></font>
<font></font>
    var thisp = arguments[1];<font></font>
    for (var i = 0; i &lt; len; i++)<font></font>
    {<font></font>
      if (i in this &amp;&amp;<font></font>
          !fun.call(thisp, this[i], i, this))<font></font>
        return false;<font></font>
    }<font></font>
<font></font>
    return true;<font></font>
  };<font></font>
}<font></font>
</code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更多细节</font></font><a href="http://www.tutorialspoint.com/javascript/array_every.htm" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在这里</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">阳光凯</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">现在，在ECMAScript2015（又名ES6）中，有一种使用新的</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of" rel="noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">for循环的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">更好方法</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">例如，此代码不会在数字5之后打印数组元素：</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>let arr = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];<font></font>
for (let el of arr) {<font></font>
  console.log(el);<font></font>
  if (el === 5) {<font></font>
    break;<font></font>
  }<font></font>
}</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">从文档： </font></font></p>

<blockquote>
  <p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">无论</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于...在</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对...的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语句迭代的东西。</font><font style="vertical-align: inherit;">它们之间的主要区别在于它们迭代的内容。</font><font style="vertical-align: inherit;">在</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">为...在</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">声明中遍历对象的枚举的属性，在原来的插入顺序。</font><font style="vertical-align: inherit;">在</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对...的</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">语句迭代数据迭代的对象定义要遍历。</font></font></p>
</blockquote>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">迭代中需要索引吗？</font><font style="vertical-align: inherit;">您可以使用</font></font><a href="http://devdocs.io/javascript/global_objects/array/entries" rel="noreferrer"><code>Array.entries()</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<pre><code>for (const [index, el] of arr.entries()) {<font></font>
  if ( index === 5 ) break;<font></font>
}<font></font>
</code></pre></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">樱Itachi</span>
            <span class="discuss-time">2020.03.09</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">有没有内置的能力</font></font><code>break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的</font></font><code>forEach</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">要中断执行，您将必须抛出某种异常。</font><font style="vertical-align: inherit;">例如。</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>var BreakException = {};<font></font>
<font></font>
try {<font></font>
  [1, 2, 3].forEach(function(el) {<font></font>
    console.log(el);<font></font>
    if (el === 2) throw BreakException;<font></font>
  });<font></font>
} catch (e) {<font></font>
  if (e !== BreakException) throw e;<font></font>
}</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">JavaScript异常不是很漂亮。</font></font><code>for</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您确实需要</font><font style="vertical-align: inherit;">传统</font><font style="vertical-align: inherit;">循环，则</font><font style="vertical-align: inherit;">传统</font><font style="vertical-align: inherit;">循环可能更合适</font></font><code>break</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<h2><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">采用 </font></font><a href="https://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Global_Objects/Array/some" rel="noreferrer"><code>Array#some</code></a></h2>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">而是使用</font></font><a href="https://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Global_Objects/Array/some" rel="noreferrer"><code>Array#some</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：</font></font></p>

<p></p><div class="snippet" data-lang="js" data-hide="false" data-console="true" data-babel="false">
<div class="snippet-code">
<pre class="snippet-code-js lang-js prettyprint-override"><code>[1, 2, 3].some(function(el) {<font></font>
  console.log(el);<font></font>
  return el === 2;<font></font>
});</code></pre>
</div>
</div>
<p></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">之所以</font></font><code>some</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可行，</font></font><code>true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">是</font><font style="vertical-align: inherit;">因为</font><font style="vertical-align: inherit;">只要按数组顺序执行任何回调，就返回return </font></font><code>true</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，从而使其余部分的执行短路。</font></font></p>

<p><code>some</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，它的反函数</font></font><a href="https://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Global_Objects/Array/every" rel="noreferrer"><code>every</code></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（将在上停止</font></font><code>return false</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">），以及</font></font><code>forEach</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">所有ECMAScript Fifth Edition方法，都需要将它们添加到</font></font><code>Array.prototype</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">缺少它们的浏览器中。</font></font></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
