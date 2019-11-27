# postgres创建用户，修改用户密码，创建数据库

## 1.创建用户
	sudo -s -u postgres
	psql
	postgres# CREATE USER xxxx1 WITH PASSWORD 'xxxx';
	postgres# CREATE DATABASE xxxx2;
	postgres# GRANT ALL PRIVILEGES ON DATABASE xxxx2 to xxxx1;

