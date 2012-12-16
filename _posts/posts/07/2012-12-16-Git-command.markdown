---
layout: post
uri : /posts/07
permalink: /posts/07/index.html
title: Git常用命令
---



<pre>
 <code>
 git init                    #初始化本地仓库
 git add .                   #把本地的内容加到仓库中
 git commit -m "description " #进行一次commit 
 git branch -a #显示所有的分支，包括本地和远程的分支
 git branch -m ori-branch dist-branch  #修改本地分支的名字  ，ori-branch为原来的分支名，dist-branch要修改后的分支名
 git branch -d branch-name  #删除分支名
 git branch -d -r origin/test #删除远程的test分支
 git branch branch-name  #创建一个分支，名字为branch-name
 git push origin :test     #删除远程的test分支
 git push origin test:master #提交本地的test分支做为远程的master分支
 git fetch  origin master #从远程的master分支下载最新的版本到本地，但是不会自动merge(合并）
 git log -p master ../origin/master #比较本地的master分支和origin/master分支的差别
 git merge origin/master #合并分支
 git  fetch origin master:tmp #从远程下载最新的版本到tmp分支
 git diff tmp #比较tmp分支和origin/master分支的差别
 git diff tmp > 0001.patch #比较tmp分支和origin/master分支的差别，并生成patch文件
 git merge tmp #合并分支到/origin/master
 git pull origin master #相当于从远程获取最新的版本并merge(合并）到本地的master分支，相当于git fetch和git merge 
 git checkout branch-name #可以切换分支和检出分支
 git checkout --orphan gh-pages #基于master分支创建一个没有父节点的分支，名字为gh-pages 

 </code>
</pre>


##今天就更新到这里，明天再更新一些命令

