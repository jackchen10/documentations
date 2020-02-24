# Windows常用命令行
## Windows中杀死指定端口 cmd 命令行 taskkill
 

  ### 方法 :  
    #### 1 查询端口占用,2 强行杀死进程
      netstat -aon|findstr "8080"
      taskkill /pid 4136 -t -f
