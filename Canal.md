# 配置canal参数

  ## 1 配置canal
	
	cd /Applications/devtools/canal/canal.deployer
	vim conf/canal.properties
	设置mysql对应地址用户名密码

    cd /Applications/devtools/canal/canal.deployer/conf/example
    vim instance.properties
    设置canal.instance.mysql.slaveId=2
    设置canal.instance.master.address=127.0.0.1:3316

  ## 2 启动canal
		
	cd /Applications/devtools/canal/canal.deployer
	bin/startup.sh

  ## 3 查看canal是否启动
		
	ps -ef|grep canal

  ## 4 查看canal端口是否已处于监听状态
		
	netstat -an | grep 11111

  ## 5 为canal用户授权远程访问
	mysql>grant select,replication slave,replication client on *.* to 'canal'@'%' identified by 'canal';
	mysql>flush privileges;
