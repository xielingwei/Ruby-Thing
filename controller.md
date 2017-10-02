1. 使用事务防止批量操作中产生错误

   `begin`	 
   
   &emsp;`ActiveRecord::Base.transaction do`
   
   &emsp;&emsp;`xxx`
   
   &emsp;`end`
   
   &emsp;`rescue => ex`
   
   &emsp;&emsp;`err_msg = ex.message`
   
   `end`

2. action中使用`match_value`进行模糊匹配,类似于like;
