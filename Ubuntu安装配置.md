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
        
4. 安装MySQL
		sudo apt-get install mysql-server mysql-client
        sudo service mysql restart
        ifconfig -a        
        
		首次通过navicat连接时，
		=>报错：10038
    	=>解决：安装vim（vi的升级版）-sudo apt-get install vim
			打开my.cnf文件查看MySQL的配置文件夹 -vim /etc/mysql/my.cnf
            分别打开两个目录，修改mysqld.cnf文件权限 -sudo chmod a+w mysqld.cnf
            找到bind-address = 127.0.0.1并注释 :wq!保存并退出
            取消权限 -sudo chmod a-w mysqld.cnf
            登录MySQL -mysql -uroot -p
            1>grant all privileges on *.* to root@"%" identified by "root" with grant option;
            2>flush privileges;
            重启MySQL -service mysql restart
            
5. 安装jdk

	1>下载安装包，`tar -zxvf xx`解压
    
    2>`vi ~/.bashrc`在文末添加以下代码，注意路径更改
    	export JAVA_HOME=/home/hand/jdk1.8.0_101
        export CLASSPATH=${JAVA_HOME}/lib
        export PATH=${JAVA_HOME}/bin:$PATH

	3>执行`source ~/.bashrc`使改动生效
    4>执行`java -version`验证
   
6. 安装Git `sudo apt-get install git`
7. 安装搜狗输入法
		sudo dpkg -i XX
        若有依赖关系报错，执行 sudo apt-get install -f，执行完毕则输入法也安装完毕。
        配置 打开【系统设置/语言支持/键盘输入方式系统】 选择 fcitx
        注销
        点击右上角键盘选择配置，勾选搜狗输入法
        注销
8. 安装Chrome
		添加下载源 => sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/
        导入公钥 => wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
        更新当前系统可用更新列表 => sudo apt-get update
        安装Chrome => sudo apt-get install google-chrome-stable
        启动 => /usr/bin/google-chrome-stable
9. 安装Moeditor	=>详见Moeditor.md
10. 安装RubyMine
		tar -zxvf xxx
        cd RubyMine-2017.2.4/bin
        ./rubymine.sh