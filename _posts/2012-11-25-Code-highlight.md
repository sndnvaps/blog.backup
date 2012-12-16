---
layout: post
styles: [syntax]
title: 语法高亮
---

<pre>
  <code>$ git init
  $ git add .
  $ git commit -a -m 'init commit.'
  $ git remote add origin
  $ git push origin master</code>
</pre>

##Go语言代码
 {% highlight go linenos %}
 package main
 import "fmt"
 func main() {
 fmt.Printf("Hello World form Golang\n")
 fmt.Printf("Chinese simple,你好\n")
 }
 
 {% endhighlight %}
 
<h2>C语言代码</h2>
'''c
 #include <stdio.h>
 int main() {
  printf("Hello World form y.ipy.cc \n");
  return 0;
  }
 
 
###在markdown文件中加入图片元素
 {% highlight html %}
 <img src="/images/post/pic-name.jpg" width="xxx" height="xxx" border="0" alt=""/>
 
 {% endhighlight %}
 其中 
 <pre>
  <code>src="文件相位置/文件名" 
  width="图片的宽度“ 单位为像素
  height="图片高度"  单位为像素
  border="0"         解释为边框
  alt=""             解释为属性
  
</pre>

  
 