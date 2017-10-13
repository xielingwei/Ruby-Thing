- 执行`bundle exec rspec spec/requests/static_pages_spec.rb`

	=>报错信息：
    	/home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/selenium-webdriver-2.0.0/lib/selenium/webdriver/common/zipper.rb:1:in 'require': cannot load such file -- zip/zip (LoadError)
        from /home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/selenium-webdriver-2.0.0/lib/selenium/webdriver/common/zipper.rb:1:in `<top (required)>
    ...
    
    =>解决办法：
    在Gemfile中添加下行代码
    `gem 'rubyzip',  "~> 0.9.9"`
   
- 嵌入式Ruby，简称ERb，因此HTML视图文件拓展名为`.html.erb`\
- `bundle exec guard init rspec`

	=>报错信息：
    	11:53:23 - ERROR - Could not load 'guard/rspec' or '~/.guard/templates/rspec' or find class Guard::Rspec
    
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
    	/home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/guard-spork-1.5.0/lib/guard/spork.rb:2:in'require': cannot load such file -- guard/guard (LoadError)
   
   =>解决方法：
    修改Gemfile中
    `gem 'guard-spork', :github => 'guard/guard-spork'`
    
	*LoadError一般为gem问题，Gemfile提供文件支持及版本，加载异常首要应先考虑Gemfile的版本是否有误*
    
- 执行`bundle exec spork`

	=>报错信息：
    	You are using capybara 2.1.0. RSpec requires version >= 2.2.0.
        (RSpec::Support::LibraryVersionTooLowError)
    
    =>解决方法：`gem 'capybara', '>= 2.2.0'`
    
- 执行`bundle exec guard`

	=>报错信息：
    	ERROR - No cmd option specified, unable to run specs!
    =>解决方法：修改Guardfile，添加`cmd: "bundle exec rspec"`。修改后为——`guard 'rspec', all_after_pass: false, cli: '--drb',cmd: "bundle exec rspec" do`
- `bundle exec rake db:migrate`

	=>报错信息：
    	rake aborted!
        NoMethodError: undefined method 'last_comment' for #<Rake::Application:0x0055ee13e52b88>
	=>解决方法：由于Rake11.0.1之后便移除了`last_comment`方法，因此我们需要先将rake调至11.0.1之前的版本。在Gemfile中添加`gem 'rake', '< 11.0 #>(>是为了格式加的)'`,执行`bundle update`,`grep rake Gemfile.lock`查看Rake的当前版本。
- `bundle exec rspec spec/`
	
    =>报错信息：
    	Failure/Error: visit root_path 
        NameError:
        undefined local variable or method 'root_path' for #<RSpec::ExampleGroups::StaticPages:0x005576c04a5768>
	=>解决方法：Named routes are not available in specs by default. Add the following code to `spec_helper.rb`:
    	RSpec.configure do |config|
        	config.include Rails.application.routes.url_helpers
        end
	=>报错信息：
    	Failure/Error: specify { expect(user_for_invalid_password).to be_false }
       expected false to respond to `false?` or perhaps you meant `be false` or `be_falsey`   
       
	=>解决方法：`be_false` => `be_falsey`
- `/app/assets/stylesheets/custom.css.scss`导入bootstrap报错

    =>报错信息：
		ActionView::Template::Error (undefined method `environment' for nil:NilClass
        (in /home/xlw/rails_projects/sample_app1/app/assets/stylesheets/custom.css.scss)):
        2: <html>
        3: <head>
        4:   <title><%= full_title(yield(:title)) %></title>
        5:   <%= stylesheet_link_tag "application", media: "all",
        6:                           "data-turbolinks-track" => true %>
        7:   <%= javascript_include_tag "application", "data-turbolinks-track" => true %>
        8:   <%= csrf_meta_tags %>
      app/views/layouts/application.html.erb:5:in '_app_views_layouts_application_html_erb___3300491497441746084_69910360596840' 
	=>解决方法：修改Gemfile，加入`gem 'sass-rails', '~> 4.0.2'`，执行`bundle install`即可。