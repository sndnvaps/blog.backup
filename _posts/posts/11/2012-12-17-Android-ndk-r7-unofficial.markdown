---
layout: post
uri: /posts/11
permalink: /posts/11/index.html
title: CrystaX，一个第三方Android NDK，扩充了google官方NDK没有的实用
---


地址：<a href="http://www.crystax.net/?locale=en">http://www.crystax.net/?locale=en</a>

这个**CrystaX NDK**的作者是俄罗斯人，牛逼！俄罗斯，一个**黑客**云集的地方。


<h3 id="catalog">目录:</h3>
*    [Description](#Des)
*    [Features supported by Crystax NDK](#Features)
     *     [1.Wide chrarcters](#F1)
     *     [2.New 4.6.3 toolchain](#F2)
     *     [3.C++11 support](#F3)
     *     [4.Objective-C support](#F4)
     *     [5.Static code analysis](#F5)
     *     [6.To be continued...](#F6)
* * *


这个是NDK r7的新特性介绍：
<h2 id="Des">Description</h2>

Here is customized distribution of Android NDK r7 which I have rebuilt from official sources. Starting from NDK r5, Google added support of C++ exceptions, RTTI and STL to the official NDK. That's good but not enough for many peoples including me. Starting from r5-crystax-1, main goal of this project will be improvements of official NDK (after all, this is the best way to integrate such improvements into mainline - that's how it was with full C++ support in Google's NDK).

<h2 id="Features">Features supported by CrystaX NDK:</h2>

<h3 id="F1">1. Wide characters</h3>
Google's NDK doesn't support wide chars properly - neither in C or C++. Using CrystaX NDK you get full standard compliant wide characters support. You can easily port existing code which use wide characters/strings/streams or write new one.

<h3 id="F2">2.  New 4.6.3 toolchain</h3>
  Starting from r7-crystax-1, CrystaX NDK contains two versions of compiler toolchain: 4.4.3 (old one, the same as Google use) and 4.6.3 (new one). 
  New toolchain contains GCC 4.6.3 with enabled Graphite framework allowing gcc do high-level memory optimizations. 
  By default 4.6.3 toolchain is not enabled. That's done to be compatible with Google's NDK. To enable it for your application, just add following to the app's Application.mk:APP_TOOLCHAIN_VERSION := 4.6.3


<h3 id="F3">3. C++11 support (formerly known as C++0x)</h3>
Google's NDK offer GCC 4.4.3 which is good compiler but doesn't support some modern features. One of such features is support of new International Standard known as C++11 (formerly known as C++0x). There is very limited support of C++0x features in GCC 4.4.3. 
Using CrystaX NDK you can start use many of new C++0x features right now. Of course, there is no yet full C++11 support in GCC 4.6.3 but GCC team works very intensively on that and it already contains many very usable features (lambdas, decltype, auto and many others). To see full list of C++0x features supported, look to GCC C++ Support page. 
To use C++0x features in your project, just add following to the app's Application.mk:APP_USE_CPP0X := trueNote that in this case new 4.6.3 toolchain implicitly selected.

<h3 id="F4">4. Objective-C support</h3>
The only languages Google NDK supports are C and C++. Starting from r7-crystax-4, CrystaX NDK support additionally Objective-C. This is experimental feature, but at least core language works fine. Of course, just core language is not enough; peoples who use Objective-C, rely on libraries like Cocoa (formerly known as NeXTSTEP/OpenStep). I understand that and don't stop on this stage. I've planned port GNUStep on Android, but this is not so easy task and it can't be done quickly. In the meantime I suppose many peoples could start using Objective-C as is.
To start using Objective-C in your project, just add source files with extension .m (Objective-C) or .mm (Objective-C++) and specify them in LOCAL_SRC_FILES in Android.mk.

<h3 id="F5">5. Static code analysis</h3>
Android NDK uses GCC which analyze code pretty good and warn about potential errors (especially with -Wall -Wextra) but, as every developer knows, there could not be reviews enough. Really, sometime we do absolutely dumb mistakes and pass them to the production. To decrease number of such mistakes, experienced developers uses static code analyzers. There are many such tools (open source and proprietary) so choice is not easy.
Clang project offer code analyzer which is pretty good in many situations. This is the same analyzer known to Apple developers through "Build and analyze" XCode's menu item. With CrystaX NDK, you can start use it with Android too. To do that, you need install clang and ensure you have 'scan-build' script from Clang distribution accessible from command-line. Then, start build your project:ndk-build ANALYZE=1I plan support more static code analyzers but have not specific plans yet.

<h3 id="F6">6. To be continued...</h3>
Seriously, if you don't see some feature here, request me to do that! Use my issue/bug tracker to report bugs or feature requests. I would be glad to implement such features if many of peoples need them. And, of course, contributes are welcome!

