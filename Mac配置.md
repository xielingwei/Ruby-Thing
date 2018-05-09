#### mysql安装
* 官网下载安装包，双击安装

#### rubymine安装
* 官网下载安装包，双击安装

#### 环境配置
1. 安装系统需要的包

		# For Mac 
		# 先安装 [Xcode](http://developer.apple.com/xcode/) 开发工具，它将帮你安装好 Unix 环境需要的开发包
		# 然后安装 [Homebrew](http://brew.sh)
		$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
2. 安装 Rails 必要的一些三方库

		$ brew install libxml2 libxslt libiconv
3. 安装RVM
				
		$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
		$ curl -sSL https://get.rvm.io | bash -s stable`
		# 如果上面的连接失败，可以尝试: 
		$ curl -L https://raw.githubusercontent.com/wayneeseguin/rvm/master/binscripts/rvm-installer | bash -s stable
		
	4. 可能需要先安装gpg `brew install gpg`