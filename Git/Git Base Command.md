 xiaoyanit.github.io 
-----------------

##### My github blog ..... #####

Git Base Command

Git 基本配置
com from :  [magicalboy.comgit-configuration](hhttp://magicalboy.com/git-configuration/ "magicalboy.com") 


1.用户信息配置

	$ git config --global user.name "xiaoyan"
	$ git config --global user.email xiaoyan@gmail.com
	$ git config --list

2.文本编辑器

在需要输入必要的文本信息时调用，比如提交更新时忘了加注释。一般情况会用系统默认的编辑器，比如Vi、Vim。当然也可以自定：


	$ git config --global core.editor emacs


3.差异分析工具
	在解决冲突时经常用到，一般为vimdiff

	$ git config --global merge.tool vimdiff

4.自动高亮
	很有用的颜色提示，因有些人不喜欢，所以默认是不开启的

	$ git config --global color.ui auto


5.查看配置

*	查看所有配置
		
		$ git config --list

*	查看某个配置
	
		$ git config user.name


6.git配置文件

*	/etc/gitconfig 对所有用户有效
*	~/.gitconfig 对当前用户有效
*	{工作目录}/.git/config 仅对当前项目有效
*	$HOME 或者 C:Documents and Settings$USER 下的.gitconfig git安装目录下的etc/gitconfig同上在类 unix 系统中，配置文件为：

>	在Windows中对应分别为：

	对应命令：

	$ git config --system
	$ git config --global
	$ git config --local 或 $ git config


7.帮助与参数资料
	想全面了解更完整和详细的说明，方法有三：

	$ git help
	$ git --help
	$ man git-
	比如，要学习 config 命令可以怎么用，可执行：

	$ git help config




##Git 命令收集<汇总表>
- - -
 git-branch 分支名称    
 git-checout –b 分支名 
 git-branch –d 分支名 (删除分支)  
 git-branch –D 分支名 (强制删除分支)  
 git show-branch  查看分支历史 
 git merge  合并分支    
git-clone  远程获取一个git库  
git-pull  从远程获取一个git分支   
git-push  将本地分支内容提交到远端分支  
git-reset 库的逆转与恢复    
git log --stat 显示被修改文件的修改统计信息，添加或删除了多少行。  

>###调整显示格式
 
>使用`git log --pretty=format`命令，可以将提交历史显示成你想要的格式。这里format的可选项包括：  
>oneline，short，medium，full，fuller，email，raw。  
>每种格式都有侧重的显示相关内容。
















- - -






##git remote基本使用
-------------------------------------------------------------
##### 添加远程仓库路径
	$: git remote add github git@github.com:yyfrankyy/search.git

##### 实际上，pull 就是 fetch + merge
	$: git pull github --all --tags
##### 把工作目录迁移到github上面：
	$: git remote add github git@github.com:yyfrankyy/search.git
	$: git push github --all --tags
##### 显示所有的远程仓库
	$: git remote -v
	origin	git@search.ued.taobao.net:projects/search.git (fetch)
	origin	git@search.ued.taobao.net:projects/search.git (push)
	github	git@github.com:yyfrankyy/search.git (fetch)
	github	git@github.com:yyfrankyy/search.git (push)
##### 重命名远程仓库
	$: git remote rename github gh
	$: git remote
	origin
	gh
##### 删除远程仓库
	$: git remote rm github
	$: git remote
	origin
##### 从远程仓库抓取数据，更新本地仓库：
	$: git fetch origin
	remote: Counting objects: 58, done.
	remote: Compressing objects: 100% (41/41), done.
	remote: Total 44 (delta 24), reused 1 (delta 0)
	Unpacking objects: 100% (44/44), done.
	From git://search.ued.taobao.net:projects/search.git
	 * [new branch]      product     -> origin/product
##### 查看远程仓库信息，可用于跟踪别人的push：
	$: git remote show origin
	* remote origin
	  Fetch URL: git@search.ued.taobao.net:projects/search.git
	  Push  URL: git@search.ued.taobao.net:projects/search.git
	  HEAD branch: master
	  Remote branches:
	    master  tracked
	    p4popt  tracked
	    prepub  tracked
	    product tracked
	  Local branches configured for 'git pull':
	    master  merges with remote master
	    p4popt  merges with remote p4popt
	    prepub  merges with remote prepub
	    product merges with remote product
	  Local refs configured for 'git push':
	    master  pushes to master  (up to date)
	    p4popt  pushes to p4popt  (up to date)
	    prepub  pushes to prepub  (up to date)
	    product pushes to product (up to date)


#####git remote 不带参数，列出已经存在的远程分支，例如：

	$git remote
	origin_apps

######git remote -v | --verbose 列出详细信息，在每一个名字后面列出其远程url，例如：
	git remote -v
	origin_apps     gitolite@scm:apps/Welcome.git (fetch)
	origin_apps     gitolite@scm:apps/Welcome.git (push)
需要注意的是，如果有子命令，-v | --verbose需要放在git remote与子命令中间。

######git remote add name url 在url创建名字为name的仓库
（Adds a remote named <name> for the repository at <url>）
name为远程仓库的名字

`git remote show name` 必须要带name，否则git remote show的作用就是git remote，给出remote name的信息。 




##[Git fetch和git pull的区别 (2013-07-23 14:37:18)转载▼](http://blog.sina.com.cn/s/blog_86fe5b44010197rs.html)


######Git中从远程的分支获取最新的版本到本地有这样2个命令：
#####1. git fetch：相当于是从远程获取最新版本到本地，不会自动merge

    
	git fetch origin master
	git log -p master..origin/master
	git merge origin/master

   以上命令的含义：
   首先从远程的`origin`的`master`主分支下载最新的版本到`origin/master`分支上
   然后比较本地的`master`分支和`origin/master`分支的差别
   最后进行合并
   上述过程其实可以用以下更清晰的方式来进行：

	git fetch origin master:tmp
	git diff tmp 
	git merge tmp


   从远程获取最新的版本到本地的test分支上
   之后再进行比较合并
#####2. git pull：相当于是从远程获取最新版本并merge到本地

	git pull origin master


> 上述命令其实相当于g`it fetch` 和 `git merge`
> 在实际使用中，`git fetch`更安全一些
> 因为在merge前，我们可以查看更新情况，然后再决定是否合并


##[git fetch 的简单用法:更新远程代码到本地仓库](http://www.360doc.com/content/13/0814/10/9171956_307028720.shtml)
	
######Git中从远程的分支获取最新的版本到本地方式如下

####1. 查看远程仓库
	
		$ git remote -v
		eoecn https://github.com/eoecn/android-app.git (fetch)
		eoecn https://github.com/eoecn/android-app.git (push)
		origin https://github.com/com360/android-app.git (fetch)
		origin https://github.com/com360/android-app.git (push)
		su@SUCHANGLI /e/eoe_client/android-app (master)
从上面的结果可以看出，远程仓库有两个，一个是eoecn，一个是origin

####2 ,从远程获取最新版本到本地

		$ git fetch origin master
		From https://github.com/com360/android-app
		 * branch master -> FETCH_HEAD
		su@SUCHANGLI /e/eoe_client/android-app (master)
		$ git fetch origin master 
这句的意思是：从远程的origin仓库的master分支下载代码到本地的
		origin master
####3. 比较本地的仓库和远程参考的区别
	
		$ git log -p master.. origin/master
		su@SUCHANGLI /e/eoe_client/android-app (master)
因为我的本地仓库和远程仓库代码相同所以没有其他任何信息

####4. 把远程下载下来的代码合并到本地仓库，远程的和本地的合并
	
		$ git merge origin/master
		Already up-to-date.
		su@SUCHANGLI /e/eoe_client/android-app (master)
我的本地参考代码和远程代码相同，所以是Already up-to-date
以上的方式有点不好理解，大家可以使用下面的方式，并且很安全



####1.查看远程分支，和上面的第一步相同

####2. 从远程获取最新版本到本地
	
	$ git fetch origin master:temp
	From https://github.com/com360/android-app
	 * [new branch] master -> temp
	su@SUCHANGLI /e/eoe_client/android-app (master)
`git fetch origin master:temp` 这句命令的意思是：从远程的origin仓库的master分支下载到本地并
新建一个分支temp

1. 比较本地的仓库和远程参考的区别

		$ git diff temp
		su@SUCHANGLI /e/eoe_client/android-app (master)
命令的意思是：比较master分支和temp分支的不同
由于我的没有区别就没有显示其他信息

4. 合并temp分支到master分支
	
		$ git merge temp
		Already up-to-date.
		su@SUCHANGLI /e/eoe_client/android-app (master)
由于没有区别，所以显示Already up-to-date.
合并的时候可能会出现冲突，有时间了再把如何处理冲突写一篇博客补充上。

5.如果不想要temp分支了，可以删除此分支
	
	$ git branch -d temp
	Deleted branch temp (was d6d48cc).
	su@SUCHANGLI /e/eoe_client/android-app (master)

如果该分支没有合并到主分支会报错，可以用以下命令强制删除git branch -D <分支名>
总结：方式二更好理解，更安全，对于pull也可以更新代码到本地，相当于fetch+merge，多人
写作的话不够安全。












