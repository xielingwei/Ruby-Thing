- `rails generate controller FooBars baz quux`
- `rails destroy controller FooBars baz quux`

- `rails generate model Foo bar:string baz:integer`
- `rails destroy model Foo`	--模型可省略命令行剩余的参数

- `rake db:migrate`
- `rake db:rollback`
- `rake db:migrate VERSION=0` --退回初始状态,数字可切换