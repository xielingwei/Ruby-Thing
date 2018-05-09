- Rails默认文件结构
	
	文件/文件夹 | 说明
	:-:|:-:
	app/ | 程序的核心文件，包含模型、视图、控制器和帮助方法
	app/assets|程序的资源文件，如CSS、JavaScript和图片
	bin/|可执行文件
	config/|程序的设置
	db/|数据库文件
	doc/|程序的文档
	lib/|代码库文件
	lib/assets|代码库包含的资源文件，如CSS、JavaScript和图片
	log/|程序的日志文件
	public/|公共（例如浏览器）可访问的数据，如出错界面
	script/rails|生成代码、打开终端会话或开启本地服务器的脚本
	test/|程序的测试文件
	tmp/|临时文件
	vendor/|第三方代码，如插件和gem
	vendor/assets|第三方代码包含的资源文件，如CSS、JavaScript和图片
	README.rdoc|程序简介
	Rakefile|rake命令包含的任务
	Gemfile|该程序所需的gem
	Gemfile.lock|一个gem的列表，确保本程序的复制版使用相同版本的gem
	config.ru|Rack中间件的配置文件
	.gitignore|git忽略的文件类型
- RSpec运行测试时都要重新加载整个Rails环境，Spork测试服务器可以解决这个问题。
- `<%= stylesheet_link_tag "application", media: "all",
                          "data-turbolinks-track" => true %>`为所有的媒介类型引入application.css。传入两个参数一个是字符串，指明样式表的路径；另一个是Hash，包含两个元素，指明媒介类型，并启用Turbolink功能。
- 大多数情况下`'`和`"`的效果是一样的，但Ruby不会对`'`进行插值操作。
- `link_to`的第一个参数是`链接文本`第二个参数是`链接地址`，第三个参数是可选的，为一个`Hash`。