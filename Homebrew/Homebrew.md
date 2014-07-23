# Homebrew #
*OS X 不可或缺的套件管理器*

-------------------------------------------------------------------

又提示缺少套件啦？别担心，Homebrew 随时守候。

	$ brew install wget

```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````

Homebrew 会将套件安装到独立目录，并将文件软链接至 /usr/local 。



	$ cd /usr/local
	$ find Cellar
	Cellar/wget/1.15
	Cellar/wget/1.15/bin/wget
	Cellar/wget/1.15/share/man/man1/wget.1

	$ ls -l bin
	bin/wget -> ../Cellar/wget/1.15/bin/wget


```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````


Homebrew 的所有文件均会被安装到预定义目录下，所以您无需担心 Homebrew 的安装位置。

```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````


轻松创建您的 Homebrew 程式。
	
`$ brew create http://foo.com/bar-1.0.tgzCreated /usr/local/Library/Formula/bar.rb`

```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````


以 git、 ruby 为其筋骨，所以借助您的相关知识，自由修改，并且可以简单撤回您的调改或者合并上游更新。

	$ brew edit wget # opens in $EDITOR!

```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````

Homebrew 的程式都是简单的 Ruby 脚本：

	require "formula"
	
	class Wget < Formula
	  homepage "http://www.gnu.org/software/wget/"
	  url "http://ftp.gnu.org/gnu/wget/wget-1.15.tar.gz"
	  sha1 "f3c925f19dfe5ed386daae4f339175c108c50574"
	
	  def install
	    system "./configure", "--prefix=#{prefix}"
	    system "make", "install"
	  end
	end

```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````



Homebrew 使 OS X 更完美。使用 gem 来安装 gems、用 brew 来搞定那些依赖包。
```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````


获取 Homebrew
	
`ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"`

打开终端窗口, 粘贴以上脚本。

脚本会解释它的作用，然后在您的确认下执行安装。高级安装选项请看 这里（需要10.5）。
```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````


更多文档
[Homebrew 维基（翻译中)](https://github.com/Homebrew/homebrew/wiki)

Original code by Max Howell. Website by Rémi Prévost.




# [通过Homebrew安装软件:](http://www.cr173.com/html/20276_1.html) #

查找你需要的软件使用brew search * 命令,安装使用brew install *命令(用具体的软件名称替换*),下面演示:

	brew search git
	brew install git

如果你想安装vim,wget或者unrar等其它各类软件,都这么做去吧.

另外,你已经安装了git了,那么建立了本地的git仓库,执行如下:

	cd /usr/local
	git init
	git remote add origin git://github.com/mxcl/homebrew.git
	git pull origin master
如果GitHub上有项目,也可直接拿下:

`git clone http://github.com/YOURGITHUBUSERNAME/homebrew.git /tmp/homebrew`

## 其它Homebrew指令: ##

	brew list —列出已安装的软件
	brew update —更新Homebrew
	brew home *—用浏览器打开
	brew info *—显示软件内容信息
	brew deps * — 显示包依赖
	brew server * —启动web服务器，可以通过浏览器访问http://localhost:4567/ 来同网页来管理包
	brew -h brew —帮助

## 删除Homebrew: ##

万一你用的不爽了,告诉你卸载指令:

	cd `brew –prefix`
	rm -rf Cellar
	brew prune
	rm -rf Library .git .gitignore bin/brew README.md share/man/man1/brew
	rm -rf ~/Library/Caches/Homebrew


##[ 安裝及使用方式 ](http://ihower.tw/blog/archives/4308)##

1. 要先安裝有 Xcode，你才能編譯東西。
2. 下載執行 http://gist.github.com/323731

安裝好之後，就有以下指令可以使用

	brew search   搜尋套件
	brew info     查詢套件資訊
	brew list     已經裝了哪些套件
	brew update   更新 homebrew 自己
	brew install  安裝套件

例如，我馬上就安裝了 wget 跟 git 這兩個是我最基本要用的工具，一下就搞定了，cool!

	brew install wget
	brew install git

參考資料

[homebrew — Mac OS X 下新的软件包管理工具](http://blog.jjgod.org/2009/12/21/homebrew-package-management/)

[Homebrew: OS X’s Missing Package Manager](http://www.engineyard.com/blog/2010/homebrew-os-xs-missing-package-manager/)








@BY xiaoyan

参考资料
[Ruby系列文章之6 ---OS X 10.8.1 系统 HomeBrew的安装和简单使用](http://blog.csdn.net/maojudong/article/details/7918291)