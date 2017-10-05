- 执行`bundle exec rspec spec/requests/static_pages_spec.rb`

	=>报错信息：
    `/home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/selenium-webdriver-2.0.0/lib/selenium/webdriver/common/zipper.rb:1:in ``require': cannot load such file -- zip/zip (LoadError)`
    `from /home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/selenium-webdriver-2.0.0/lib/selenium/webdriver/common/zipper.rb:1:in `<top (required)>`
    ...
    
    =>解决办法：
    在Gemfile中添加下行代码
    `gem 'rubyzip',  "~> 0.9.9"`
   
- 嵌入式Ruby，简称ERb，因此HTML视图文件拓展名为`.html.erb`\
- `bundle exec guard init rspec`

	=>报错信息：
    `11:53:23 - ERROR - Could not load 'guard/rspec' or '~/.guard/templates/rspec' or find class Guard::Rspec`
    
    =>解决办法：
    修改Gemfile文件
    `instead of 
gem 'guard-rspec', '2.5.0'
replace on
gem 'guard-rspec', '4.6.0'`

	`instead of 
gem 'rspec-rails', '2.13.1'
replace on
gem 'rspec-rails', '3.3.2'`

	执行`bundle update`以及`bundle exec guard init rspec`
    
- 执行`time bundle exec rspec spec/requests/static_pages_spec.rb`

	=>报错信息：
    `/home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/guard-spork-1.5.0/lib/guard/spork.rb:2:in'require': cannot load such file -- guard/guard (LoadError)`
   
   =>解决方法：
    修改Gemfile中
    `gem 'guard-spork', :github => 'guard/guard-spork'`
    
	*LoadError一般为gem问题，Gemfile提供文件支持及版本，加载异常首要应先考虑Gemfile的版本是否有误*
    
- 执行`bundle exec spork`

	=>报错信息：
    `You are using capybara 2.1.0. RSpec requires version >= 2.2.0. (RSpec::Support::LibraryVersionTooLowError)`
    
    =>解决方法：`gem 'capybara', '>= 2.2.0'`
    
- 执行`bundle exec guard`

	=>报错信息：`ERROR - No cmd option specified, unable to run specs!`
    =>解决方法：修改Guardfile，添加`cmd: "bundle exec rspec"`。修改后为——`guard 'rspec', all_after_pass: false, cli: '--drb',cmd: "bundle exec rspec" do`
