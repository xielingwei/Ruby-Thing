### `bundle exec rspec spec/requests/static_pages_spec.rb`

	报错信息：
    `/home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/selenium-webdriver-2.0.0/lib/selenium/webdriver/common/zipper.rb:1:in ``require': cannot load such file -- zip/zip (LoadError)`
    `from /home/xlw/.rvm/gems/ruby-2.0.0-p648/gems/selenium-webdriver-2.0.0/lib/selenium/webdriver/common/zipper.rb:1:in `<top (required)>`
    ...
    
    解决办法：
    在Gemfile中添加下行代码
    gem 'rubyzip',  "~> 0.9.9"
 
 ### 