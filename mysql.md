- `mysqldump -uroot -pC3KQgC2Jh12VPNyU -h114.55.9.221 hisuite_michelin > ./michelin.sql`
- `mysql -uroot -proot michelin < ./michelin.sql`


- `mysqldump -uroot -proot -h172.20.0.70 irm_prod_sap > ./irm_prod_sap.sql`
- `mysql -uroot -proot irm_prod_sap < ./irm_prod_sap.sql`

- 关机时忘记关掉mysql服务，导致重启后mysql密码变更。
	- 系统偏好设置中关闭mysql
	- cd /usr/local/mysql/bin
	- sudo su
	- sh-3.2#目录下执行./mysqld_safe --skip-grant-tables &
	- 此时系统偏好设置中mysql服务已经重启
	- command + D
	- mysql -u -root
		- mysql> FLUSH PRIVILEGES;
		- mysql> SET PASSWORD FOR root@'localhost' = PASSWORD('root');
		- -或
		- mysql>USE mysql
		- UPDATE user SET Password = PASSWORD('newpwd')
		- WHERE Host = 'localhost' AND User = 'root';
		- -或
		- mysql>USE mysql
		- UPDATE user SET Password = PASSWORD('newpwd')
		- WHERE Host = '%' AND User = 'root';
		- -或
		- UPDATE mysql.user SET authentication_string = PASSWORD('root')
		- WHERE User = 'root' AND Host = 'localhost';
		- -最后
		- mysql> FLUSH PRIVILEGES;