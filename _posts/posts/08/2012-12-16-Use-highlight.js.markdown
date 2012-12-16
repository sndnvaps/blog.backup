---
layout: post
uri: /posts/08
permalink: /posts/08/index.html
styles: [syntax]
title: 使用highlight.js实现博客中的代码高亮
---

#要实现代码高亮，需要highlight.js

[官方下载地址](http://softwaremaniacs.org/soft/highlight/en/download/)

[我已经下载好的](/images/post/download/highlight.zip)

##添加代码

例如我把highligh.zip解压到了/javascripts/highligh
下面的操作就非常简单了，往要添加高亮的见面中加入如下的定义：
{% highlight html %}
  <link rel="stylesheet" href=/javascripts/highlight/styles/tomorrow-night-eighties.css">
  <script src="/javascripts/highlight/highlight.pack.js"></script>
  <script>hljs.initHighlighingOnLoad();</script>

{% endhighlight %}

##例子一个
*源代码*
{% highlight html %}
<pre> 
  <code class="c">
  #include <stdio.h>
  int main() {
  printf("Hello World\n");
  return 0;
 }
 </code>
</pre>
{% endhighlight %}


*效果*
<pre> 
  <code class="c">
  #include <stdio.h>
  int main() {
  printf("Hello World\n");
  return 0;
 }
 </code>
</pre>



**重点**
在
html代码中的code包围的代码中，要用到class指定语言。
例如class="c"


 


