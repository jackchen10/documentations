# MySQL常用命令

## 0 进入mysql数据库控制台
  * mysql -h localhost -u root -P 3306 -p
  * -p表示需要输入密码

## 1 导出整个数据库
  * mysqldump -u 用户名 -p --default-character-set=latin1 数据库名 > 导出的文件名(数据库默认编码是latin1)
  * 举个栗子： mysqldump -u wcnc -p smgp_apps_wcnc > wcnc.sql
## 2 导出一个表
  * mysqldump -u 用户名 -p 数据库名 表名> 导出的文件名
  * 举个栗子： mysqldump -u wcnc -p smgp_apps_wcnc users> wcnc_users.sql
## 3 导出一个数据库结构
  * mysqldump -u wcnc -p -d –add-drop-table smgp_apps_wcnc >d:wcnc_db.sql
  * -d 没有数据 –add-drop-table 在每个create语句之前增加一个drop table
## 4 导入数据库
  * 方法一： 使用source命令，后面参数为脚本文件(如这里用到的.sql)
    * 举个栗子： mysql>source wcnc_db.sql
  * 方法二： 使用mysqldump命令
    * 举个栗子： mysqldump -u username -p dbname < filename.sql
  * 使用mysql命令
    * 举个栗子： mysql -u username -p -D dbname < filename.sql
  
  
