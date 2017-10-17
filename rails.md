- `rails generate controller FooBars baz quux`
- `rails destroy controller FooBars baz quux`

- `rails generate model Foo bar:string baz:integer`
- `rails destroy model Foo`	--模型可省略命令行剩余的参数

- `rake db:migrate`
- `rake db:rollback`
- `rake db:migrate VERSION=0` --退回初始状态,数字可切换
- rails以表单中字段的name属性的值为键，用户输入的内容为值，构成一个名为params的Hash，用于创建。