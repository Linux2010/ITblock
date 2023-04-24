# restart update
## 1, 关闭2台salve节点
```shell
#关闭redis-salve
./redis-cli -h 127.0.0.1 -p 6379
info replication
shutdown
ps -ef|grep java
kill sentinel的进程号

# 修改redis配置-maxmemory
maxmemory 不设置
如果不设置maxmemory或者设置为0，64位系统不限制内存，32位系统最多使用3GB内存。
Redis默认最大内存大小是应用程序可访问的内存大小, 32位windows下是2GB, linux下是3GB. 64位下可以访问的内存为2^64字节, Redis提供了maxmemory字段来限制使用的最大内存. 既然提供了最大内存限制, 那么当我们程序达到最大值时, Redis使用了多种策略进行置换.Redis建议最大内存设置为物理内存的一半。

# 修改redis配置（确认下使用哪个？）
volatile-lru : 对具有生存周期的key进行LRU算法置换.
volatile-lru 

#扩容后重启salve节点，重启redis-salve
./start-redis.sh 
./start-sentinel.sh

```

## 2,关闭1台master节点
```shell
#主动故障转移
redis-cli -p {sentinel_port} SENTINEL failover {cluster_name}

redis-cli -p 26379 SENTINEL failover  mymaster

#关闭redis-master
./redis-cli -h 127.0.0.1 -p 6379
info replication
shutdown
ps -ef|grep java
kill sentinel的进程号
#扩容后重启master节点，重启redis-salve
./start-redis.sh
./start-sentinel.sh

```

## 3， 检查参数
```shell
cat /proc/sys/vm/overcommit_memory
sysctl vm.overcommit_memory=1
# 添加
vim /etc/sysctl.conf
vm.overcommit_memory=1
```

## 参考
- [http://www.bigdeal.cn/plus/news.php?aid=783708](http://www.bigdeal.cn/plus/news.php?aid=783708)