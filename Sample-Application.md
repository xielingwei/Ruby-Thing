- 执行`bundle exec rspec spec/requests/static_pages_spec.rb`

		=>报错信息：
    		/home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/selenium-webdriver-2.0.0/lib/selenium/webdriver/common/zipper.rb:1:in 'require': cannot load such file -- zip/zip (LoadError)
        from /home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/selenium-webdriver-2.0.0/lib/selenium/webdriver/common/zipper.rb:1:in `<top (required)>
    	...
    
   	 	=>解决办法：
    		在Gemfile中添加下行代码
    			gem 'rubyzip',  "~> 0.9.9"
    			
    	=>报错信息：
    		Exception encountered: #<NameError: uninitialized constant RSpec::Core::CommandLine>
    		
    	=>解决办法：
    		修改Gemfile
    			在spork-rails上方增加
    				gem 'spork', github: 'sporkrb/spork', branch: 'master'
    			bundle install
   
- 嵌入式Ruby，简称ERb，因此HTML视图文件拓展名为`.html.erb`
- `bundle exec guard init rspec`

		=>报错信息：
    		11:53:23 - ERROR - Could not load 'guard/rspec' or '~/.guard/templates/rspec' or find class Guard::Rspec
    
    	=>解决办法：
    		修改Gemfile文件
    			instead of gem 'guard-rspec', '2.5.0' 
    				replace on gem 'guard-rspec', '4.6.0'

				instead of gem 'rspec-rails', '2.13.1'
					replace on gem 'rspec-rails', '3.3.2'
					
				执行bundle update以及bundle exec guard init rspec
    
- 执行`time bundle exec rspec spec/requests/static_pages_spec.rb`

		=>报错信息：
    		/home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/guard-spork-1.5.0/lib/guard/spork.rb:2:in'require': cannot load such file -- guard/guard (LoadError)
   
   		=>解决方法：
    		修改Gemfile中
    			gem 'guard-spork', :github => 'guard/guard-spork'
    
	* `LoadError`一般为gem问题，Gemfile提供文件支持及版本，加载异常首要应先考虑Gemfile的版本是否有误*
    
- 执行`bundle exec spork`

		=>报错信息：
    		You are using capybara 2.1.0. RSpec requires version >= 2.2.0.
        (RSpec::Support::LibraryVersionTooLowError)
    
    	=>解决方法：gem 'capybara', '>= 2.2.0'
    
- 执行`bundle exec guard`

		=>报错信息：
    		ERROR - No cmd option specified, unable to run specs!
    	=>解决方法：
    		修改Guardfile，添加 cmd: "bundle exec rspec"。
    		修改后为 guard 'rspec', all_after_pass: false, cli: '--drb',cmd: "bundle exec rspec" do
- `bundle exec rake db:migrate`

		=>报错信息：
    		rake aborted!
        	NoMethodError: undefined method 'last_comment' for #<Rake::Application:0x0055ee13e52b88>
	
		=>解决方法：由于Rake11.0.1之后便移除了last_comment方法，因此我们需要先将rake调至11.0.1之前的版本。在Gemfile中添加gem 'rake', '< 11.0',执行`bundle update`,`grep rake Gemfile.lock`查看Rake的当前版本。
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
       
		=>解决方法：
			be_false => be_falsey
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
		
		=>解决方法：
		修改Gemfile，加入 gem 'sass-rails', '~> 4.0.2' ，
			bundle install。
- Ruby中，括号是可省略的
- 在调用函数时，如果Hash是最后一个参数，它的花括号是可省略的
- 路由报错
		
		=>报错信息：
			Failure/Error: before {visit help_path}
     		NameError:
       			undefined local variable or method `help_path' for #<RSpec::ExampleGroups::StaticPages::HelpPage:0x007fdd354ed0d0>
		=>解决方法：
			在spec_helper.rb中添加
				config.include Rails.application.routes.url_helpers
- `rspec spec/requests/user_pages_spec.rb  -e "signup with invalid information"`报错

		=>报错信息：
		Failures:
			1) User pages signup with invalid information should not create a user
     			Failure/Error: expect {click_button submit}.not_to change(User, :count)
     			ActiveModel::ForbiddenAttributesError:
       				ActiveModel::ForbiddenAttributesError
		=>解决方法：
			将users_controller.rb文件中的
				def create
    				@user = User.new(user_params)
    				...
      			end
      		replace =>
      			def create
    				@user = User.new(user_params)
    				...
  				end
- `rspec spec/models/user_spec.rb`报错

		=>报错信息：
		/Users/lewis/.rvm/gems/ruby-2.0.0-p648/gems/rspec-core-3.3.2/lib/rspec/core/example_group.rb:656:in ‘method_missing’: undefined method ‘its’ for RSpec::ExampleGroups::User::RememberToken:Class (NoMethodError)
		=>解决方法：
		gem 'rspec-its'
		bundle install
