---
layout: post
uri: /golang-learning/01
permalink: /golang-learning/01/index.html
title: golang-learnging
---


[源代码连接](https://github.com/sndnvaps/Golang-learning)


##这是根据**许式伟**的书的实例进行修改的源代码
程序名为calc

<h3 id="catalog">目录</h3>

*    [目录结构](#construct)
*    [构建工程](#proj)
     *    [把当前的目录加入到GOPATH中](#proj1)
	 *    [编译](#proj2)
	     *          [测试](#proj3)
	 *    [运行一下](#proj4)
* * *


<h3 id="construct">目录结构</h3>

被标识为
<pre><code>*calc*</code></pre>


<pre>
  <code>
   *calcproj*
      |--*src*
	     |--*calc*
             |--calc.go
         |--*simplemath*
             |--add.go
             |--add_test.go
             |--sqrt.go
             |--sqrt_test.go
     |--*bin*
     |--*pkg*


   </code>
</pre>

<h3 id="proj">构建工程</h3>

<h4 id="proj1">把当前的目录加入到GOPATH中</h4>

例如当前目录的位置为

在windows系统下面

<code>
  E:\work\calcproj
</code>

在linux系统下面：

<code>
 /home/sn/calcproj
</code>

根据不同的系统环境作相应的修改的，

<pre>
 <code class="bash">
  set GOPATH=E:\work\calcproj   #这是在windows系统下面的设置

  export GOPATH=/home/sn/calcproj   #这是在linux系统下面的设置
 </code>
</pre>


<h4 id="proj2">编译</h4>

因为我喜欢用**linux**系统，所以下面的讲解以linux系统为主：
 因为GOPATH和PATH环境变量一样，也可以接受多个路径，并且路径和路径之间用冒号分割在。设置完成GOPATH后，现在就开始构建工程了。
我们把生成的执行文件放置在/home/sn/calcproj/bin目录中，需要执行如下的命令：

<pre>
  <code>
   $ cd /home/sn/calcproj
   $ mkdir bin
   $ cd bin
   $ go build calc
 </code>
</pre>

<h4 id="proj3">测试</h4>

<pre>
 <code>
 $ go test simplemath
 ok simplemath  0.625s

 </code>
</pre>

<h4 id="proj4">运行一下</h4>

<pre>
 <code>

 $ ./calc add 4 5
 Result: 9
 
 $ ./calc sqrt 9
 Result: 3

 $ ./calc 
USAGE: calc command [argument] ...

The commands are 
     add  Addition of two values.
     sqrt Square root of a non-negative value.

 </code>
</pre>



