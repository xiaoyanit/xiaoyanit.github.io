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



##Git detached from origin/macOS)
  
  ![detached from ...]()  
  [参考资料](http://hi.barretlee.com/2014/04/30/switch-branch-in-git/)  
  
  
  
`git branch -va`
  
  可以查看本地+远程分支列表  
       
    * macOS                        51e70f8 remove older web source
    master                       fa5d764 [ahead 1, behind 3] Create README.md
    origin/master                acd1dc6 add source
    windowXP                     b9389f1 Signed-off-by: xiaoyanit <xiaoyanitmail@gmail.com>
    remotes/origin/HEAD          -> origin/master
    remotes/origin/macOS         51e70f8 remove older web source
    remotes/origin/master        043d640 Create CNAME
    remotes/origin/origin/master acd1dc6 add source
    remotes/origin/windowXP      b9389f1 Signed-off-by: xiaoyanit <xiaoyanitmail@gmail.com>
  
  
  此时`git branch branch_name` 是不起作用的

`git checkout -b macOS`  
  
  -b 的意思是 base，以当前分支为 base，新建一个名叫 `macOS` 的分支，这里当然也可以使用其他的命名。此时再执行 git branch 就能看到：

    * macOS
    master
    origin/master
    windowXP  
至此，分支切换成功。

##git版本回退操作

  [参考资料](http://hi.barretlee.com/2014/04/30/switch-branch-in-git/)
  
  git 回退总结收集：
  
  	- git checkout commit-id(SHA)
  	- git reset hard commit-id(SHA)
  	
这句命令可以回退到指定版本。不过上传的时候要注意了，如果你是：
  
  `git push -u master origin`
  
  肯定会出现这样的错误提示：  
           
	error: failed to push some refs to 'https://github.com/barretlee/barretlee.github.io.git'
	hint: Updates were rejected because the tip of your current branch is behind
	hint: its remote counterpart. Integrate the remote changes (e.g.
	hint: 'git pull ...') before pushing again.
	hint: See the 'Note about fast-forwards' in 'git push --help' for details.
  
  原因是你本地版本要落后于服务器上的版本（git reset 回退了嘛），如果想覆盖服务器上版本，应该加 -f ，强制提交，
  
  `git push -u master origin -f`
  
不过这样的操作要谨慎了，先把修改的位置备份（拿出来，复制到文件夹外），完成上述操作之后再复制回来处理。 （完）  
  
  
##资料收集

[在 git 中使用 pull 的常用方法 ](http://zhaojunde1976.blog.163.com/blog/static/12199866820132275511791/)
  
  
  
