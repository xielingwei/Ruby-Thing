1. 参照README执行后台操作。
2. 打开服务器进入前台操作。 
    3. 新建标签页（设置/应用设置/创建/标签页）
	4. 新建应用（设置/应用设置/创建/应用）
	5. License勾选（设置/Cloud管理/运维中心License）
	6. 简档配置（设置/管理设置/管理用户/简档）	//可先创建【超级管理员】简档及【默认系统建档】系统建档
	7. 为Ironmine更换【超级管理员】简档（设置/管理设置/管理用户/用户），此时可见到所有添加进应用的标签页
	8. 新建组（设置/管理设置/管理用户/组），在查看组界面将已有用户添加进组
	9. 新建支持组（设置/管理设置/事故管理/支持组），将已有组扩建为支持组
	10. 新建应用系统（设置/管理设置/应用系统/应用系统），在查看应用系统界面将已有用户及已有支持组添加进应用系统
	11. 新建事故单分类（设置/管理设置/事故管理/事故单分类设置）


- 初始化系统(清空数据):
	- `rake irm:clear_system_data`
	- `rake irm:init_system`
- `ps -ef|grep unicorn`	=>	查看unicorn的进程号
- `kill -9 unicorn的进程号`
- `sudo systemctl restart nginx`
- `sudo service nginx restart`
- `ps -ef | grep nginx`
- `unicorn_rails -E production -D -c /home/roo/hi_test/hisuite/config/unicorn.rb`