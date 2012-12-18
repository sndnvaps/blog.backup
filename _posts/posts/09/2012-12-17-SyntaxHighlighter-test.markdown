---
layout: post
uri: /posts/09
permalink: /posts/09/index.html
sytles: [syntax]
title: 用syntaxhighlighter_3.0.83.js实现语法高亮
---


下载我提供的
[syntaxhighlighter_3.0.83.zip](/images/post/download/syntaxhighlighter_3.0.83.zip "syntaxhighlighter_3.0.83.zip"),把得到的zip解压到你的网站的根目录下面。

go语言专用笔刷：
[shBrushGo.js](/images/post/download/shBrushGo.zip "点击我下载") 下载地址：<a href="https://github.com/xeonx/shBrushGo">https://github.com/xeonx/shBrushGo</a>

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
###源代码_ bash
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

###源代码_ golang

{% highlight html %}
 <pre class="brush: go;">
  package main 
  import "fmt"
  import "os"
  
  type Integer int

  var Version = func() {
   fmt.Println("this is the test")
   fmt.Println("Version 0.0.1")
  }
 func (a Integer) Bigger(b Integer) bool {
    if a < b {
   return false
  }
  return true 
 }

func main() {
  if len(os.Args) == 1 {
   Version()
 } else {
 var c Integer = 4
 ok := c.Bigger(6)
 if ok {
  fmt.Println(c ,"is bigger than 6")
   } else {
  fmt.Println(c ,"is smaller the 6")
 }
}

{% endhighlight %}


<pre class="brush: go;">
 package main 
  import "fmt"
  import "os"
  
  type Integer int

  var Version = func() {
   fmt.Println("this is the test")
   fmt.Println("Version 0.0.1")
  }
 func (a Integer) Bigger(b Integer) bool {
    if a < b {
   return false
  }
  return true 
 }

func main() {
  if len(os.Args) == 1 {
   Version()
 } else {
 var c Integer = 4
 ok := c.Bigger(6)
 if ok {
  fmt.Println(c ,"is bigger than 6")
   } else {
  fmt.Println(c ,"is smaller the 6")
 }
}

</pre>



