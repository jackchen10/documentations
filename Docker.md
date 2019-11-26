# Docker Commands
Docker常用命令：

## 0 在docker仓库中搜索mysql的镜像：
	docker search mysql
	下载镜像： 
	docker pull mysql:5.7.21
	mysql:5.7.21:冒号后面加上:5.7.21表示下载指定版本的mysql

## 0-1 查看本地镜像：
	docker images -a 

## 0-2 查看运行中的容器：
	docker ps -a
	-a 表示所有已安装的镜像
	docker ps -s
	-s 表示已启动的镜像的容器

## 0-3 删除指定镜像通过下面命令：
	docker rmi image-id
	删除所有镜像通过下面命令：
	docker rmi $(docker images -q)


## 1 启动mysql实例
	docker run --name mysql_master -p 3316:3306 -e MYSQL_ROOT_PASSWORD=chenfeng1982 -d mysql:5.7
	注：
	docker run -d -p [本机端口]:[docker服务器端口] --name container-name image-name
	--name参数：是为容器取得名称；
	-d：表示detached，意味着执行完这句命令后控制台将不会被阻碍，可继续输入命令操作；
	image-name： 是要使用哪个镜像来运行容器。
	-p：端口映射
	本机端口： 对外暴露的端口
	docker服务器端口： 各个应用占用的端口，比如mysql占用3316


	mysql_master： 容器别名
	chenfeng1982：初始化设置的root用户的密码
	5.7：mysql的版本，不写默认使用最新版
	-p 3316:3306：表示在这个容器中使用3306端口(第二个)映射到本机的端口号为3316(第一个)

## 2 连接到本地mysql
	docker run -it --link mysql_master:mysql --rm mysql sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'

## 3 连接其他地方的mysql
	docker run -it --rm mysql mysql -hsome.mysql.host -usome-mysql-user -p

## 4 换到Docker Mysql的容器shell命令：
	docker exec -it mysql_master bash

	启动 mysql 容器，并进入 shell 命令交互界面：
	docker run -it mysql_master /bin/bash

## 5 退出输入：
	exit

## 6 查看日志
	docker logs mysql_master

## 7 删除容器
	docker rm -f mysql_master

## 8 重新启动mysql，并挂载配置文件到宿主机
	docker run --name mysql_master -p 3316:3306 -v /opt/webMysql/conf:/etc/mysql/conf.d -v /opt/webMysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=chenfeng1982 mysql:5.7

## 9 在docker运行下面命令，用来创建一个mysql容器，端口为3316：
	docker run --name mysql_master -p 3316:3306 -e MYSQL_ROOT_PASSWORD=chenfeng1982 -d mysql:5.7
	报错：
	docker: Error response from daemon: Conflict. The container name "/mysql_master" is already in use by container "7d904e5ed84b1ff4db4b8996ff152e1997277997594bda1e3020e130e6654c5d". You have to remove (or rename) that container to be able to reuse that name.
	See 'docker run --help'.
	说明已经存在这样的一个mysql container实例存在，只是没有运行起来
	此时，利用下面的命令启动docker中的这个mysql的container:
	docker start 7d904e5ed84b1ff4db4b8996ff152e1997277997594bda1e3020e130e6654c5d
	注：这里的7d904e5ed84b1ff4db4b8996ff152e1997277997594bda1e3020e130e6654c5d，是mysql的container id

## 10 查看docker中已经创建的容器：
	docker ps -a

## 11 查看docker中正在运行的容器
	docker ps -s

## 12 重启Docker中的mysql，或其他container
	首先查询mysql或待重启的容器的container id：
	docker ps -a
	比如我查询Docker中mysql的CONTAINER ID是： 7d904e5ed84b
	再执行下面的命令，进行重启：
	docker restart 7d904e5ed84b 
