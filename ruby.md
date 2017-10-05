1.	`to_i`可将任意对象转化为数字,而所有非数字对象`to_i`后结果均为0;

2.	`a = "123/456/789"`
    `a.split("/")  = ["123","456","789"];`

3.	`"allocation".pluralize = "allocations"`
	`"allocations".singularize = "allocation"`
4. Ruby不会对单引号字符串进行插值操作，如果需要转义则需要写两个‘\\’，先将‘\’本身转义

