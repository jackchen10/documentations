# MySQL常用命令

## 1 导出整个数据库
  * mysqldump -u 用户名 -p --default-character-set=latin1 数据库名 > 导出的文件名(数据库默认编码是latin1)
  * 举个栗子： mysqldump -u wcnc -p smgp_apps_wcnc > wcnc.sql
## 2 导出一个表
  * mysqldump -u 用户名 -p 数据库名 表名> 导出的文件名
  * 举个栗子： mysqldump -u wcnc -p smgp_apps_wcnc users> wcnc_users.sql
