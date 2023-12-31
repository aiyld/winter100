---
layout: question
title:  Vue.js-在标头中使用多部分/表单数据时，验证无法在axios中上载
date:   2020-05-28T07:33:27.000Z
description: 我正在使用BootstrapVue，VeeValidate和axios作为HTTP客户端构建Laravel + Vue.js SPA（单页应用程序）。...
img: 
author: 宝儿
category: question
answer: 2
tags: laravel Vue.js
topic: Vue.js
---
<div class="article-root">
  <div class="article">
    {% include articleTitle.html info=page %}
    {% raw %}
    <div class="article-content"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我正在使用</font></font><a href="https://bootstrap-vue.js.org/" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">BootstrapVue</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，</font></font><a href="https://logaretm.github.io/vee-validate/guide/forms.html#validate-before-submit" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">VeeValidate</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和axios作为HTTP客户端</font><font style="vertical-align: inherit;">构建Laravel + Vue.js SPA（单页应用程序）</font><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在axios内部，当我   </font></font><code>multipart/form-data; boundary=${uploadForm._boundary}</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">用作</font></font><code>Content-Type</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">in时</font></font><code>headers</code> <strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，Laravel Controller方法中的所有验证都会失败</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但是，如果我</font></font><code>'content-type': 'multipart/form-data'</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在其中</font><font style="vertical-align: inherit;">使用</font><font style="vertical-align: inherit;">，</font></font><code>header</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">  则验证会起作用，</font></font><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">但</font></font><code>file</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">输入字段</font><font style="vertical-align: inherit;">除外</font><font style="vertical-align: inherit;">。</font></font><code>file</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在Laravel控制器方法中，</font><font style="vertical-align: inherit;">该</font><font style="vertical-align: inherit;">字段变为空。</font></font></strong> </p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">这发生在组件内</font></font><code>EditProfile.vue</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">那里的内容是：</font></font></p>

<pre class="lang-php prettyprint prettyprinted" style=""><code><span class="tag">&lt;template&gt;</span><span class="pln">
</span><span class="tag">&lt;ValidationObserver</span><span class="pln"> </span><span class="atn">ref</span><span class="pun">=</span><span class="atv">"form"</span><span class="pln"> </span><span class="atn">v-slot</span><span class="pun">=</span><span class="atv">"{ passes }"</span><span class="tag">&gt;</span><span class="pln">

        </span><span class="tag">&lt;div</span><span class="pln"> </span><span class="atn">id</span><span class="pun">=</span><span class="atv">"registration_form"</span><span class="tag">&gt;</span><span class="pln">

            </span><span class="tag">&lt;div</span><span class="pln"> </span><span class="atn">id</span><span class="pun">=</span><span class="atv">"form_title"</span><span class="pln"> </span><span class="atn">class</span><span class="pun">=</span><span class="atv">"text-center"</span><span class="tag">&gt;</span><span class="pln">Edit Your Profile</span><span class="tag">&lt;/div&gt;</span><span class="pln">
            </span><span class="tag">&lt;div</span><span class="pln"> </span><span class="atn">v-html</span><span class="pun">=</span><span class="atv">"result"</span><span class="pln"> </span><span class="atn">class</span><span class="pun">=</span><span class="atv">"result text-center"</span><span class="tag">&gt;&lt;/div&gt;</span><span class="pln">


            </span><span class="tag">&lt;b-form</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"uploadForm"</span><span class="pln"> @</span><span class="atn">submit</span><span class="pln">.</span><span class="atn">prevent</span><span class="pun">=</span><span class="atv">"passes(onSubmit)"</span><span class="pln"> @</span><span class="atn">reset</span><span class="pun">=</span><span class="atv">"resetForm"</span><span class="pln">  </span><span class="atn">enctype</span><span class="pun">=</span><span class="atv">"multipart/form-data"</span><span class="tag">&gt;</span><span class="pln">


                </span><span class="tag">&lt;ValidationProvider</span><span class="pln"> </span><span class="atn">vid</span><span class="pun">=</span><span class="atv">"name"</span><span class="pln"> </span><span class="atn">rules</span><span class="pun">=</span><span class="atv">"required|min:2"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"name"</span><span class="pln"> </span><span class="atn">v-slot</span><span class="pun">=</span><span class="atv">"{ valid, errors }"</span><span class="tag">&gt;</span><span class="pln">
                    </span><span class="tag">&lt;b-form-group</span><span class="pln">
                            </span><span class="atn">label</span><span class="pun">=</span><span class="atv">"User Name:"</span><span class="pln">
                            </span><span class="atn">label-for</span><span class="pun">=</span><span class="atv">"exampleInput1"</span><span class="pln">

                    </span><span class="tag">&gt;</span><span class="pln">
                        </span><span class="tag">&lt;b-form-input</span><span class="pln">
                                </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"text"</span><span class="pln">
                                </span><span class="atn">disable-leading-trailing-space</span><span class="pln">
                                </span><span class="atn">v-model</span><span class="pun">=</span><span class="atv">"name"</span><span class="pln">
                                </span><span class="atn">plaintext</span><span class="pln">
                                :</span><span class="atn">state</span><span class="pun">=</span><span class="atv">"errors[0] ? false : (valid ? true : null)"</span><span class="pln">
                                </span><span class="atn">placeholder</span><span class="pun">=</span><span class="atv">"Enter your name"</span><span class="pln">
                        </span><span class="tag">&gt;&lt;/b-form-input&gt;</span><span class="pln">
                        </span><span class="tag">&lt;b-form-invalid-feedback</span><span class="pln"> </span><span class="atn">id</span><span class="pun">=</span><span class="atv">"inputLiveFeedback"</span><span class="tag">&gt;</span><span class="pln">{{ errors[0] }}</span><span class="tag">&lt;/b-form-invalid-feedback&gt;</span><span class="pln">
                    </span><span class="tag">&lt;/b-form-group&gt;</span><span class="pln">
                </span><span class="tag">&lt;/ValidationProvider&gt;</span><span class="pln">



                </span><span class="tag">&lt;ValidationProvider</span><span class="pln"> </span><span class="atn">vid</span><span class="pun">=</span><span class="atv">"photo"</span><span class="pln"> </span><span class="atn">rules</span><span class="pun">=</span><span class="atv">"required"</span><span class="pln"> </span><span class="atn">name</span><span class="pun">=</span><span class="atv">"photo"</span><span class="pln"> </span><span class="atn">v-slot</span><span class="pun">=</span><span class="atv">"{ valid, errors }"</span><span class="tag">&gt;</span><span class="pln">
                    </span><span class="tag">&lt;b-form-group</span><span class="pln">
                            </span><span class="atn">label</span><span class="pun">=</span><span class="atv">"Photo:"</span><span class="pln">
                            </span><span class="atn">label-for</span><span class="pun">=</span><span class="atv">"exampleInput1"</span><span class="pln">
                    </span><span class="tag">&gt;</span><span class="pln">


                        </span><span class="tag">&lt;b-form-file</span><span class="pln">

                                </span><span class="atn">accept</span><span class="pun">=</span><span class="atv">"image/x-png,image/gif,image/jpeg"</span><span class="pln">
                                </span><span class="atn">v-model</span><span class="pun">=</span><span class="atv">"file"</span><span class="pln">
                                :</span><span class="atn">state</span><span class="pun">=</span><span class="atv">"Boolean(file)"</span><span class="pln">
                                </span><span class="atn">placeholder</span><span class="pun">=</span><span class="atv">"Choose a file or drop it here..."</span><span class="pln">
                                </span><span class="atn">drop-placeholder</span><span class="pun">=</span><span class="atv">"Drop file here..."</span><span class="pln">
                                @</span><span class="atn">change</span><span class="pun">=</span><span class="atv">"onFileChange"</span><span class="pln"> </span><span class="atn">enctype</span><span class="pun">=</span><span class="atv">"multipart/form-data"</span><span class="pln">
                        </span><span class="tag">&gt;&lt;/b-form-file&gt;</span><span class="pln">
                        </span><span class="tag">&lt;b-form-invalid-feedback</span><span class="pln"> </span><span class="atn">id</span><span class="pun">=</span><span class="atv">"inputLiveFeedback"</span><span class="tag">&gt;</span><span class="pln">{{ errors[0] }}</span><span class="tag">&lt;/b-form-invalid-feedback&gt;</span><span class="pln">
                        </span><span class="tag">&lt;div</span><span class="pln"> </span><span class="atn">class</span><span class="pun">=</span><span class="atv">"mt-3"</span><span class="tag">&gt;</span><span class="pln">Selected file: {{ file ? file.name : '' }}</span><span class="tag">&lt;/div&gt;</span><span class="pln">

                        </span><span class="com">&lt;!-- Plain mode --&gt;</span><span class="pln">
                        </span><span class="com">&lt;!--&lt;b-form-file v-model="file2" class="mt-3" plain&gt;&lt;/b-form-file&gt;
                        &lt;div class="mt-3"&gt;Selected file: {{ file2 ? file2.name : '' }}&lt;/div&gt;--&gt;</span><span class="pln">

                        </span><span class="tag">&lt;div</span><span class="pln"> </span><span class="atn">id</span><span class="pun">=</span><span class="atv">"preview"</span><span class="tag">&gt;</span><span class="pln">
                            </span><span class="tag">&lt;img</span><span class="pln"> </span><span class="atn">v-if</span><span class="pun">=</span><span class="atv">"url"</span><span class="pln"> :</span><span class="atn">src</span><span class="pun">=</span><span class="atv">"url"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln">
                        </span><span class="tag">&lt;/div&gt;</span><span class="pln">

                    </span><span class="tag">&lt;/b-form-group&gt;</span><span class="pln">
                </span><span class="tag">&lt;/ValidationProvider&gt;</span><span class="pln">





                </span><span class="tag">&lt;b-button</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"submit"</span><span class="pln"> </span><span class="atn">variant</span><span class="pun">=</span><span class="atv">"primary"</span><span class="tag">&gt;</span><span class="pln">Submit</span><span class="tag">&lt;/b-button&gt;</span><span class="pln">
                </span><span class="tag">&lt;b-button</span><span class="pln"> </span><span class="atn">type</span><span class="pun">=</span><span class="atv">"reset"</span><span class="pln"> </span><span class="atn">variant</span><span class="pun">=</span><span class="atv">"danger"</span><span class="tag">&gt;</span><span class="pln">Reset</span><span class="tag">&lt;/b-button&gt;</span><span class="pln">
            </span><span class="tag">&lt;/b-form&gt;</span><span class="pln">

        </span><span class="tag">&lt;/div&gt;</span><span class="com">&lt;!-- end of id registration_form--&gt;</span><span class="pln">
    </span><span class="tag">&lt;/ValidationObserver&gt;</span><span class="pln">
</span><span class="tag">&lt;/template&gt;</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在JS部分，我有：</font></font></p>

<pre class="lang-php prettyprint prettyprinted" style=""><code><span class="tag">&lt;script&gt;</span><span class="pln">


    </span><span class="kwd">import</span><span class="pln"> </span><span class="pun">{</span><span class="pln"> </span><span class="typ">ValidationObserver</span><span class="pun">,</span><span class="pln"> </span><span class="typ">ValidationProvider</span><span class="pln"> </span><span class="pun">}</span><span class="pln"> </span><span class="kwd">from</span><span class="pln"> </span><span class="str">"vee-validate"</span><span class="pun">;</span><span class="pln">

     </span><span class="kwd">export</span><span class="pln"> </span><span class="kwd">default</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
        name</span><span class="pun">:</span><span class="pln"> </span><span class="str">"EditProfile"</span><span class="pun">,</span><span class="pln">
        props</span><span class="pun">:</span><span class="pln"> </span><span class="pun">{</span><span class="pln">

        </span><span class="pun">},</span><span class="pln">

        components</span><span class="pun">:</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
            </span><span class="typ">ValidationObserver</span><span class="pun">,</span><span class="pln">
            </span><span class="typ">ValidationProvider</span><span class="pln">


        </span><span class="pun">},</span><span class="pln">
        data</span><span class="pun">:</span><span class="pln"> </span><span class="pun">()</span><span class="pln"> </span><span class="pun">=&gt;</span><span class="pln"> </span><span class="pun">({</span><span class="pln">

            name</span><span class="pun">:</span><span class="pln"> </span><span class="str">""</span><span class="pun">,</span><span class="pln">
            photo</span><span class="pun">:</span><span class="str">""</span><span class="pun">,</span><span class="pln">
            file</span><span class="pun">:</span><span class="str">""</span><span class="pun">,</span><span class="pln">
            url</span><span class="pun">:</span><span class="str">""</span><span class="pun">,</span><span class="pln">  
            result</span><span class="pun">:</span><span class="str">''</span><span class="pln">

        </span><span class="pun">}),</span><span class="pln">

        methods</span><span class="pun">:</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
            onFileChange</span><span class="pun">(</span><span class="pln">e</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
                </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">file </span><span class="pun">=</span><span class="pln"> e</span><span class="pun">.</span><span class="pln">target</span><span class="pun">.</span><span class="pln">files</span><span class="pun">[</span><span class="lit">0</span><span class="pun">];</span><span class="pln">
                </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">url </span><span class="pun">=</span><span class="pln"> URL</span><span class="pun">.</span><span class="pln">createObjectURL</span><span class="pun">(</span><span class="kwd">this</span><span class="pun">.</span><span class="pln">file</span><span class="pun">);</span><span class="pln">
            </span><span class="pun">},</span><span class="pln">
        onSubmit</span><span class="pun">()</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
                console</span><span class="pun">.</span><span class="pln">log</span><span class="pun">(</span><span class="str">"Form submitted yay!"</span><span class="pun">);</span><span class="pln">


                </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">result</span><span class="pun">=</span><span class="str">'&lt;span class="wait"&gt;Please wait ...&lt;/span&gt;'</span><span class="pun">;</span><span class="pln">

                axios</span><span class="pun">.</span><span class="pln">post</span><span class="pun">(</span><span class="str">'/update_profile_now'</span><span class="pun">,</span><span class="pln">
                    </span><span class="pun">{</span><span class="pln">
                       name</span><span class="pun">:</span><span class="pln"> </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">name</span><span class="pun">,</span><span class="pln">
                       photo</span><span class="pun">:</span><span class="kwd">this</span><span class="pun">.</span><span class="pln">file

                    </span><span class="pun">},</span><span class="pln"> </span><span class="com">// the data to post</span><span class="pln">
                    </span><span class="pun">{</span><span class="pln">


                        headers</span><span class="pun">:</span><span class="pln"> </span><span class="pun">{</span><span class="pln">

                            </span><span class="com">//Accept: 'application/json',</span><span class="pln">

                           </span><span class="str">'Content-Type'</span><span class="pun">:</span><span class="pln">  </span><span class="pun">`</span><span class="pln">multipart</span><span class="pun">/</span><span class="pln">form</span><span class="pun">-</span><span class="pln">data</span><span class="pun">;</span><span class="pln"> boundary</span><span class="pun">=</span><span class="pln">$</span><span class="pun">{</span><span class="pln">uploadForm</span><span class="pun">.</span><span class="pln">_boundary</span><span class="pun">}`</span><span class="pln">

                        </span><span class="pun">}</span><span class="pln">



                    </span><span class="pun">})</span><span class="pln">
                    </span><span class="pun">.</span><span class="pln">then</span><span class="pun">(</span><span class="pln">response </span><span class="pun">=&gt;</span><span class="pln"> </span><span class="pun">{</span><span class="pln">

                        </span><span class="kwd">if</span><span class="pun">(</span><span class="pln">response</span><span class="pun">.</span><span class="pln">data</span><span class="pun">.</span><span class="pln">success</span><span class="pun">){</span><span class="pln">

                            </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">result</span><span class="pun">=</span><span class="str">'&lt;span class="succes"&gt;Registration completed !!&lt;/span&gt;'</span><span class="pun">;</span><span class="pln">
                        </span><span class="pun">}</span><span class="kwd">else</span><span class="pun">{</span><span class="pln">

                            </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">$refs</span><span class="pun">.</span><span class="pln">form</span><span class="pun">.</span><span class="pln">setErrors</span><span class="pun">(</span><span class="pln">response</span><span class="pun">.</span><span class="pln">data</span><span class="pun">.</span><span class="pln">errors</span><span class="pun">);</span><span class="pln">

                            </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">result</span><span class="pun">=</span><span class="str">'&lt;span class="error"&gt;Invalid data !!&lt;/span&gt;'</span><span class="pun">;</span><span class="pln">
                        </span><span class="pun">}</span><span class="pln">




                    </span><span class="pun">})</span><span class="pln">
                    </span><span class="pun">.</span><span class="kwd">catch</span><span class="pun">(</span><span class="pln">error </span><span class="pun">=&gt;</span><span class="pln"> </span><span class="pun">{</span><span class="pln">

                        </span><span class="kwd">if</span><span class="pun">(</span><span class="kwd">typeof</span><span class="pln"> error </span><span class="pun">!==</span><span class="str">"undefined"</span><span class="pun">){</span><span class="pln">

                            console</span><span class="pun">.</span><span class="pln">log</span><span class="pun">(</span><span class="pln">error</span><span class="pun">);</span><span class="pln">
                        </span><span class="pun">}</span><span class="pln">

                    </span><span class="pun">});</span><span class="pln">

                </span><span class="com">//    .finally(() =&gt; this.loading = false)</span><span class="pln">
            </span><span class="pun">},</span><span class="pln">
            resetForm</span><span class="pun">()</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
                </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">name </span><span class="pun">=</span><span class="pln"> </span><span class="str">""</span><span class="pun">;</span><span class="pln">

                </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">result</span><span class="pun">=</span><span class="str">''</span><span class="pun">;</span><span class="pln">

                requestAnimationFrame</span><span class="pun">(()</span><span class="pln"> </span><span class="pun">=&gt;</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
                    </span><span class="kwd">this</span><span class="pun">.</span><span class="pln">$refs</span><span class="pun">.</span><span class="pln">form</span><span class="pun">.</span><span class="pln">reset</span><span class="pun">();</span><span class="pln">
                </span><span class="pun">});</span><span class="pln">
            </span><span class="pun">}</span><span class="pln">
        </span><span class="pun">}</span><span class="pln">
    </span><span class="pun">};</span><span class="pln">

</span><span class="tag">&lt;/script&gt;</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在相应的Laravel控制器方法中，我有：</font></font></p>

<pre class="lang-php prettyprint prettyprinted" style=""><code><span class="pln"> </span><span class="kwd">public</span><span class="pln"> </span><span class="kwd">function</span><span class="pln"> update_profile_now</span><span class="pun">(</span><span class="typ">Request</span><span class="pln"> $request</span><span class="pun">)</span><span class="pln">
    </span><span class="pun">{</span><span class="pln">


        $rules </span><span class="pun">=</span><span class="pln"> array</span><span class="pun">(</span><span class="pln">

            </span><span class="str">'name'</span><span class="pln"> </span><span class="pun">=&gt;</span><span class="pln"> </span><span class="str">'required | min:4'</span><span class="pun">,</span><span class="pln">
            </span><span class="str">'photo'</span><span class="pun">=&gt;</span><span class="pln"> </span><span class="str">'image|mimes:jpeg,png,jpg|max:2048'</span><span class="pln">
        </span><span class="pun">);</span><span class="pln">

        $validator </span><span class="pun">=</span><span class="pln"> </span><span class="typ">Validator</span><span class="pun">::</span><span class="pln">make</span><span class="pun">(</span><span class="typ">Input</span><span class="pun">::</span><span class="pln">all</span><span class="pun">(),</span><span class="pln"> $rules</span><span class="pun">);</span><span class="pln">

        </span><span class="com">// Validate the input and return correct response</span><span class="pln">
        </span><span class="kwd">if</span><span class="pln"> </span><span class="pun">(</span><span class="pln">$validator</span><span class="pun">-&gt;</span><span class="pln">fails</span><span class="pun">())</span><span class="pln">
        </span><span class="pun">{</span><span class="pln">
            </span><span class="kwd">return</span><span class="pln"> </span><span class="typ">Response</span><span class="pun">::</span><span class="pln">json</span><span class="pun">(</span><span class="pln">array</span><span class="pun">(</span><span class="pln">
                </span><span class="str">'success'</span><span class="pln"> </span><span class="pun">=&gt;</span><span class="pln"> </span><span class="kwd">false</span><span class="pun">,</span><span class="pln">
                </span><span class="str">'errors'</span><span class="pln"> </span><span class="pun">=&gt;</span><span class="pln"> $validator</span><span class="pun">-&gt;</span><span class="pln">getMessageBag</span><span class="pun">()-&gt;</span><span class="pln">toArray</span><span class="pun">()</span><span class="pln">

            </span><span class="pun">),</span><span class="pln"> </span><span class="lit">200</span><span class="pun">);</span><span class="pln"> 
        </span><span class="pun">}</span><span class="pln">

        </span><span class="com">//file uploading code goes here </span><span class="pln">

        </span><span class="kwd">return</span><span class="pln"> </span><span class="typ">Response</span><span class="pun">::</span><span class="pln">json</span><span class="pun">(</span><span class="pln">array</span><span class="pun">(</span><span class="str">'success'</span><span class="pln"> </span><span class="pun">=&gt;</span><span class="pln"> </span><span class="kwd">true</span><span class="pun">),</span><span class="pln"> </span><span class="lit">200</span><span class="pun">);</span><span class="pln">




   </span><span class="pun">}</span></code></pre>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想要的是</font></font><code>file</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将提交内部</font><font style="vertical-align: inherit;">带有</font><font style="vertical-align: inherit;">输入</font><font style="vertical-align: inherit;">的表单，</font><font style="vertical-align: inherit;">然后在文件上传和其他工作之后从该方法发送JSON响应。</font></font></p>

<p>So what should be the correct header or do I need to adopt any other means ?</p></div>
    {% endraw %}
  </div>
  <p class="winter_mark">第4233篇《Vue.js-在标头中使用多部分/表单数据时，验证无法在axios中上载》来自Winter(https://github.com/aiyld/aiyld.github.io)的站点</p>
  <div class="discuss-wrapper">
    {% include discussTitle.html info=page %}
    {% raw %}
    <div class="discuss-list">
    <div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">伽罗理查德</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我建议</font></font><code>VeeValidation</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您在提交表单后</font><font style="vertical-align: inherit;">使用它</font><font style="vertical-align: inherit;">来验证您的表单。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">它确实是最简单和最甜蜜的验证方法。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以从这里安装。</font></font><a href="https://www.npmjs.com/package/vee-validate" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">VeeValidation链接</font></font></a></p></div>
        </div></div><div class="discuss-item">
        <div class="discuss-parent">
          <div class="discuss-meta">
            <span class="discuss-user">Chloe</span>
            <span class="discuss-time">2020.05.28</span>
          </div>
          <div class="discuss-comment"><p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我想使用</font></font><a href="https://developer.mozilla.org/en-US/docs/Web/API/FormData" rel="nofollow noreferrer"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">FormData API</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">可以工作。</font></font></p>

<p><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">下面是一些示例：</font></font></p>

<p><a href="https://stackoverflow.com/questions/43013858/how-to-post-a-file-from-a-form-with-axios#43014086"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如何使用Axios从表单发布文件</font></font></a>
<a href="https://stackoverflow.com/questions/47630163/axios-post-request-to-send-form-data"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">axios发布请求以发送表单数据</font></font></a></p></div>
        </div></div>
    </div>
    {% endraw %}
  </div>
<div>
