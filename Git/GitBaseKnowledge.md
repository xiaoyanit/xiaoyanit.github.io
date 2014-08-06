Git远程操作详解
===================
  
  
[come from]:(http://www.ruanyifeng.com/blog/2014/06/git_remote.html)


	*git clone
	*git remote
	*git fetch
	*git pull
	*git push

[OSChina Git 中指南](http://git.oschina.net/progit/)


[Git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

[OSChina Git wikis](http://git.oschina.net/oschina/git-osc/wikis/Home)




#Git问题操作记录#

####报错①

######如果只在本地修改，还没有commit，那么用git status, 打印信息为：
![](https://raw.githubusercontent.com/xiaoyanit/xiaoyanit.github.io/master/Git/20140804103815.png)


######commit之后，用git status，打印信息为：
	# On branch master
	# Your branch is ahead of 'origin/master' by 1 commit.
	#
	nothing to commit (working directory clean)

说明没有文件需要commit，但是本地仓库 有一个commit ahead原来的master，就是本地仓库有一个提交，比远程仓库要先进一个commit。git push origin master之后，再用git staus，打印信息为：

	# On branch master
	nothing to commit (working directory clean)


####方案一：
--------------------------------------------


今天更新了一下git，然后出现如下问题：

	$ git status -u
	# On branch master
	# Your branch is ahead of 'origin/master' by 6016 commits.
	#

解决方法：

	# git pull --rebase
	remote: Counting objects: 5304, done.
	remote: Compressing objects: 100% (1417/1417), done.
	remote: Total 4299 (delta 3122), reused 4043 (delta 2880)
	Receiving objects: 100% (4299/4299), 2.19 MiB | 449 KiB/s, done.
	Resolving deltas: 100% (3122/3122), completed with 425 local objects.
	From git://git.kernel.org/pub/scm/git/git
	   8ef2794..bce14aa  maint      -> origin/maint
	   16eed7c..bce14aa  master     -> origin/master
	 + 68bd821...59f2e5e next       -> origin/next  (forced update)
	 + d3a6f81...fa8cfe3 pu         -> origin/pu  (forced update)
	   85a4700..aa5f592  todo       -> origin/todo
	Current branch master is up to date.


![](https://raw.githubusercontent.com/xiaoyanit/xiaoyanit.github.io/master/Git/20140804103951.png)


####方案二：
--------------------------------------------




















  

--------------------------------------------

Git工作流程(Git工作流程)

http://www.open-open.com/lib/view/open1341754663635.html




##Git for mac 中文乱码

>git stataus .  
 然后中文乱码 

		modified:   Git/vi/274\232\350\256\256\346\200\273\347\273\223.pdf 
		
		
###解决方案：
在bash提示符下输入：

`git config --global core.quotepath false`

######core.quotepath设为false的话，就不会对0×80以上的字符进行quote。中文显示正常。
  - - - 
  
####[GIT乱码解决方案汇总](http://www.cnblogs.com/perseus/archive/2012/11/21/2781074.html)
  
  
  
####本文参考链接
[搞定Git中文乱码、用TortoiseMerge实现Diff/Merge](http://topic.csdn.net/u/20110113/19/b0d5d506-4307-428b-a61d-7974aa66a2da.html)	  
[MsysGit乱码与跨平台版本管理](http://topic.csdn.net/u/20110106/20/f11ef8dd-44ec-478e-b78a-73240bcdde43.html)  
[git中文文件名、目录名乱码应该怎么解决？](http://bbs.et8.net/bbs/showthread.php?t=942185)  
[git中文乱码解决](http://www.wangyinneng.com/git%E4%B8%AD%E6%96%87%E4%B9%B1%E7%A0%81%E8%A7%A3%E5%86%B3/)  
[git status中文乱码](http://bbs.chinaunix.net/thread-3558872-1-1.html)
  
  
 - - -
  ***
  *** 
 - - -
  ***
  ***
 - - -
  ***
  ***
 - - -
  ***
  *** 
 - - -
  ***
  ***
 - - -
  ***
  ***
##git 更新本地代码 
  
  - `git fetch`
  - ...
  - `git pull origin`
  
##git log 绘制日志
  `git log --pretty=oneline --graph`
![log日志](https://raw.githubusercontent.com/xiaoyanit/xiaoyanit.github.io/master/Git/20140805172212.png)  
  
 
##Git学习教程专题

- [Git学习教程（一）：git简介](http://fsjoy.blog.51cto.com/318484/244397)
- [Git学习教程（二）：配置和初始化](http://fsjoy.blog.51cto.com/318484/244803)
- [Git学习教程（三）：Git工作流程](http://fsjoy.blog.51cto.com/318484/244397)
- [Git学习教程（四）：分枝和合并](http://fsjoy.blog.51cto.com/318484/245081)
- [Git学习教程（五）：Git标签](http://fsjoy.blog.51cto.com/318484/245106)
- [Git学习教程（六）Git日志](http://fsjoy.blog.51cto.com/318484/245261)
- [Git学习教程（七） Git差异比对](http://fsjoy.blog.51cto.com/318484/245465)
- []()
- []()



####[git 合并远程分支时候的操作](http://hlee.iteye.com/blog/669831)
  
>合并到主分支

  `$git merge master` 
  
  


- - -

##[在GitHub上管理项目](http://www.cnblogs.com/mengdd/p/3447464.html)


设置开发流
######push方法1：

　　现在如果想直接Push这个develop分支上的内容到github

　　`git push -u origin`

　　如果是新建分支第一次push，会提示：

    fatal: The current branch develop has no upstream branch. 
	To push the current branch and set the remote as upstream, use
	git push --set-upstream origin develop
　　输入这行命令，然后输入用户名和密码，就push成功了。

　　以后的push就只需要输入 `git push origin`
