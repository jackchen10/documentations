# ELK常用命令
## 启动elasticsearch命令：<br>
  cd /Applications/devtools/elasticsearch-node1/
  * 执行下面命令，在后台执行：
    bin/elasticsearch -d<br>
  * 在浏览器打开下面url，可以检查elasticsearch是否启动成功：
    http://localhost:9200/_cat

## 启动kibana命令：<br>
    cd /Applications/devtools/kibana-7.4.2-darwin-x86_64/
  * 执行下面命令：
    bin/kibana

## 启动logstash命令：<br>
  cd /Applications/devtools/logstash-7.4.2/
  * 执行下面命令:
    bin/logstash -f mysql/jdbc.conf 
