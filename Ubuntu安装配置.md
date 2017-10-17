1. 安装VMware-tools
		=>提示：
        	what is the location of the "ifconfig"program on your machine?
        =>解决：
        	输入‘yes’即可       
            
2. 安装rvm
		1> gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
        2> \curl -sSL https://get.rvm.io | bash
        3> echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"' >>~/.bashrc
        4> source ~/.bashrc

3. 利用rvm安装ruby
		rvm requirements
        rvm install 1.9.3