## install
> 只做参考路径，一切以官网为准 
- [es官网安装手册](https://www.elastic.co/guide/cn/elasticsearch/guide/current/running-elasticsearch.html)
- [Kibana安装](https://www.elastic.co/guide/cn/kibana/current/targz.html)
### 启停
```shell
# 后台启动
bin/elasticsearch -d
# 测试启动情况
curl 'http://localhost:9200/?pretty'

# kibana 后台启动，无输出启动
nohup bin/kibana >/dev/null 2>&1 &

# kibana 后台启动，只输出错误信息
nohup bin/kibana >/dev/null 2>log &

```

### 单节点


### linux集群
