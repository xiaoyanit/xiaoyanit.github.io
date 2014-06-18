xiaoyanit.github.io
===================

My github blog .....

Git Base Command

Git 基本配置
com from : http://magicalboy.com/git-configuration/
1.用户信息配置

	git config --global user.name "xiaoyan"
	git config --global user.email xiaoyan@gmail.com

	git config --list

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
	查看所有配置

	$ git config --list
	查看某个配置

	$ git config user.name


6.git配置文件
	/etc/gitconfig 对所有用户有效
	~/.gitconfig 对当前用户有效
	{工作目录}/.git/config 仅对当前项目有效
	$HOME 或者 C:Documents and Settings$USER 下的.gitconfig
	git安装目录下的/etc/gitconfig
	同上
	在类 unix 系统中，配置文件为：

	在Windows中对应分别为：

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







































