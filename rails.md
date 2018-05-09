- 生成一个`controller`及两个`action`，同时系统会为这两个`action`自动生成`route`，`--no-test-framework`选项禁止生成RSpec测试代码
			
		$ rails generate controller StaticPages home help --no-test-framework      		create  app/controllers/static_pages_controller.rb       		 route  get "static_pages/help"       		 route  get "static_pages/home"      		invoke  erb      		create    app/views/static_pages      		create    app/views/static_pages/home.html.erb      		create    app/views/static_pages/help.html.erb      		invoke  helper      		create    app/helpers/static_pages_helper.rb      		invoke  assets      		invoke    coffee      		create      app/assets/javascripts/static_pages.js.coffee
			invoke    scss			create      app/assets/stylesheets/static_pages.css.scss
- 以下两条命令是相互抵消的
- 		rails destroy controller FooBars baz quux
	 	  rails destroy controller FooBars baz quux
- 以下两条命令也能相互抵消
- 		rails generate model Foo bar:string baz:integer	
			此时会生成一个migration，如不指定字段，可在migration中编写，执行后生成相应字段
		  rails destroy model Foo
		  	删除模型可省略命令行剩余的参数
- 数据迁移
- 		rake db:migrate
	 	  rake db:rollback
		  rake db:migrate VERSION=0 --退回初始状态,数字代表版本
- rails以表单中字段的name属性的值为键，用户输入的内容为值，构成一个名为params的Hash，用于创建。
- `RAILS_ENV=production rake db:migrate`
- `RAILS_ENV=production rake irm:initdata`
- `RAILS_ENV=production script/delayed_job restart`
- `RAILS_ENV=production script/delayed_job stop`
- `RAILS_ENV=production script/delayed_job start`
- `RAILS_ENV=production rake sunspot:solr:start`
- `RAILS_ENV=production rake sunspot:solr:stop`
- `RAILS_ENV=production script/scheduler restart`
- `RAILS_ENV=production rake sunspot:reindex`
- `RAILS_ENV=production rake assets:precompile`
- `export NLS_LANG=american_america.AL32UTF8`
- validates
    - `validates_numericality_of`	文本框仅输入数字
