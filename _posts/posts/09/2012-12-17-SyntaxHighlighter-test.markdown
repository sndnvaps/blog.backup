---
layout: post
uri: /posts/09
permalink: /posts/09/index.html
sytles: [syntax]
title: 用syntaxhighlighter_3.0.83.js实现语法高亮
---


下载我提供的
[syntaxhighlighter_3.0.83.zip](/images/post/download/syntaxhighlighter_3.0.83.zip "syntaxhighlighter_3.0.83.zip"),把得到的zip解压到你的网站的根目录下面。

再在要实现高亮的网页中加入如下的代码，

{% highlight html %}

<!—-必须添加--> 
<script type="text/javascript" src="scripts/shCore.js"></script> 
<!—-下面是根据语言进行添加--> 
<script type="text/javascript" src="scripts/shBrushJScript.js"></script>
 <script type="text/javascript" src="scripts/shBrushCSharp.js"></script> 
 <script type="text/javascript" src="scripts/shBrushBash.js"></script>
 <!--添加了JScript,Bash,CSharp三个语言的支持-->
  <link type="text/css" rel="stylesheet" href="styles/shCoreDefault.css"/>
 <script type="text/javascript">SyntaxHighlighter.all();</script>  

{% endhighlight %}

##测试：
###源代码：
 {% highlight html %}
<pre class="brush: bash;">
 $ mkdir highlight.js
 $ cd highlight.js
 $ git clone git://github.com/sndnvaps/highlight.js.git -b master ./
 $ 

</pre>
{% endhighlight %}

###效果如下：

<pre class="brush: bash;">

 $ mkdir highlight.js
 $ cd highlight.js
 $ git clone git://github.com/sndnvaps/highlight.js.git -b master ./
 $ 
</pre>




