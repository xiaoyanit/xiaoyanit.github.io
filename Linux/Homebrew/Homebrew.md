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


## [菜鸟级 Mac 配置（二）](http://jianshu.io/p/dee28486b465) ##

- **oh-my-zsh**

Mac 自带了很多 Shell，通过下面的命令：
	
	cat /etc/shells
可以看到如下列表：
	
	/bin/bash
	/bin/csh
	/bin/ksh
	/bin/sh
	/bin/tcsh
	/bin/zsh
系统默认的是 bash，但 zsh 才是其中最犀利的，被称为「终极 Shell」。而且一位国外特别有（wu）才（liao）的程序员为 zsh 量身定做了一套配置方案叫 oh-my-zsh，实在是对我等小白用心良苦，我不能辜负他的这片心意啊。

首先，通过

	chsh -s /bin/zsh\

把默认 Shell 换为 zsh。然后用下面的两句（任选其一）可以自动安装 oh-my-zsh：

`curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh`

`wget --no-check-certificate https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O - | sh`



剩下的配置就参考池老师的文章—— [终极 Shell](http://macshuo.com/?p=676)



- **iTerm2**

和 zsh 配合起来，特别酷炫！发现些小功能确实酷炫：



1. 分窗口操作：shift+command+d（横向）command+d（竖向）
2. 查找和粘贴：command+f，呼出查找功能，tab 键选中找到的文本，option+enter 粘贴 
3. 自动完成：command+ 根据上下文呼出自动完成窗口，上下键选择
4. 粘贴历史：shift+command+h
5. 回放功能：option+command+b
6. 全屏：command+enter
7. 光标去哪了？ command+/
8. Expose Tabs：option+command+e



下图是有多标签页和多窗口的 iTerm2：

![](http://myblogimage.qiniudn.com/illustration%5C%E8%8F%9C%E9%B8%9F%E7%BA%A7Mac%E9%85%8D%E7%BD%AE%5CScreen%20Shot%202014-02-26%20at%205.53.11%20PM.png)



##[brew安装的软件Smple](http://community.itbbs.cn/thread/21327/)##

今天更新brew安装的软件，结果悲剧产生了，sourceforge.net被墙了！！

我们以libpng为例进行解决，其他软件方法一样。

	sh-3.2# brew upgrade
	==> Upgrading 6 outdated packages, with result:
	libpng 1.5.12, imagemagick 6.7.7-6, libtiff 4.0.2, pcre 8.31, lighttpd 1.4.31, wget 1.14
	==> Upgrading libpng
	==> Downloading http://downloads.sf.net/project/libpng/libpng15/1.5.12/libpng-1.5.12.tar.gz

	curl: (56) Recv failure: Connection reset by peer
	Error: Download failed: http://downloads.sf.net/project/libpng/libpng15/1.5.12/libpng-1.5.12.tar.gz

很明显，下载软件失败，我们找另一个软件包地址把sf.net上的替换掉。

执行命令：

	$ brew edit libpng

会提示编辑ruby源代码，编辑器是vim，内容如下。

	require 'formula'

	class Libpng < Formula
	  homepage 'http://www.libpng.org/pub/png/libpng.html'
	  #url 'http://downloads.sf.net/project/libpng/libpng15/1.5.12/libpng-1.5.12.tar.gz'
	  url 'ftp://ftp.simplesystems.org/pub/libpng/png/src/libpng-1.5.12.tar.gz'
	  sha1 'c329f3a9b720d7ae14e8205fa6e332236573704b'

	  keg_only :provided_by_osx if MacOS::X11.installed?
	
	  def install
    system "./configure", "--disable-dependency-tracking", "--prefix=#{prefix}"
    system "make install"
	  end	
	end	

很明显我用`ftp.simplesystems.org`替换了`downloads.sf.net`的文件地址。
接下来保存好内容，继续brew，成功！


#[zsh 使用 安装](http://blog.csdn.net/housansan/article/details/19302371)#


