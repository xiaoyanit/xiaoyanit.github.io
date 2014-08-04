##autojump

[转载](http://uecss.com/zsh-brew-autojump-plugins-shell-for-mac.html)

####autojump 初次配置完之后会报错：

	xiaoyan >>> j /home 
	python: can't open file '/usr/lib/command-not-found': [Errno 2] No such file or directory
	

>解决办法如下：在.zshrc 配置文件中找到 plugins=() 这行
作出如下修改

	plugins=(git autojump)
	
	
	
####autojump 候选项过多问题：
	
>添加如下脚本即可
[脚本cd-quickly.sh](https://github.com/nuoerlz/cd-quicKly/blob/master/cd-quickly.sh)
	
	
	// add these lines to ~/.bashrc

	cdqf=$HOME/.cd_quickly_history
	function cd()
	{
    	cdtf=/tmp/tmp3234_23933333_cd_tmp
	    dst="$@"

    	if [[ $# != 0 ]]; then
        	ret=`sed -ne "${1}p" $cdqf 2>/dev/null`
	        [[ ! -z $ret ]] && {
    	        dst=$ret
        	}
	    else
    	    dst=$HOME
	    fi

    	builtin cd "$dst" && pwd

	    echo -e "`pwd`" >> $cdqf
    	cat $cdqf | sort -u >> $cdtf
    	mv -f $cdtf $cdqf
	}

	function c()
	{
    	cat $cdqf | nl
	}

	function cg()
	{
    	c | grep -i "$1"
	}

	function cr()
	{
    	cdtf=/tmp/tmp3234_23937793_cd_tmp
    	[[ $# != 0 ]] && {
        	`sed -e "${1}d" $cdqf 1>$cdtf 2>/dev/null`
        	mv -f $cdtf $cdqf
    	}
	}