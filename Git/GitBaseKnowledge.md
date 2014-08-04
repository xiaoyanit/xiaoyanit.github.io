Git远程操作详解
===================
  
  
[come from]:(http://www.ruanyifeng.com/blog/2014/06/git_remote.html)


	*git clone
	*git remote
	*git fetch
	*git pull
	*git push

OSChina Git 中指南
http://git.oschina.net/progit/

Git教程

http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000

OSChina Git wikis

http://git.oschina.net/oschina/git-osc/wikis/Home


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
















