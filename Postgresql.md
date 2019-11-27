# postgres创建用户，修改用户密码，创建数据库

## 1.创建用户
	sudo -s -u postgres
	psql
	postgres# CREATE USER xxxx1 WITH PASSWORD 'xxxx';
	postgres# CREATE DATABASE xxxx2;
	postgres# GRANT ALL PRIVILEGES ON DATABASE xxxx2 to xxxx1;

## 2.修改密码
	alter user postgres with password 'foobar';

## 3.创建数据库
	createdb--encoding=UTF8 --owner=foo --template=template_postgis -Ufoo
	参数： --encoding=UTF8 设置数据库的字符集
	--owner=foo 设置数据库的所有者
	--tmplate=template_postgis 设置建库的模板，该模板支持空间数据操作
	--Ufoo 用foo用户身份建立数据库
## 4. 修改PostgreSQL数据库默认用户postgres的密码
   * 步骤一：登录PostgreSQL
	* sudo -u postgres psql
   * 步骤二：修改登录PostgreSQL密码
	* ALTER USER postgres WITH PASSWORD 'postgres';
   * 步骤三：退出PostgreSQL客户端
	* \q
## 5. 修改linux系统postgres用户的密码
   * 步骤一：删除用户postgres的密码
	* sudo  passwd -d postgres
   * 步骤二：设置用户postgres的密码
	* sudo -u postgres passwd
