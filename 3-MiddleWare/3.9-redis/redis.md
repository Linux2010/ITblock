# redis

- [单节点安装](install/singel.md)
- [哨兵模式安装](install/Redis-Sentinel.md)
- [集群模式安装]
- [哨兵模式内存升级](install/redis-update.md)

### Q&A

- [【Redis】批量删除Key的三种方式](https://blog.csdn.net/qq_25106373/article/details/115404827)
- [redis哨兵模式怎么重启](http://www.bigdeal.cn/plus/news.php?aid=783708)

- [Redis主从复制高可用，哨兵的使用 | Sentinel 哨兵的快速搭建 | 哨兵的两种启动方式](https://blog.csdn.net/succing/article/details/121265307)
- [【redis】redis 主从哨兵架构重启](https://www.jianshu.com/p/23cfb803a6d9)

#### redis哨兵模式 60G以上主从同步优化方案
```shell
# 设置环形缓冲区
config set client-output-buffer-limit "slave 2147483648 1073741824 60"
# 提高传输速率
config set repl-backlog-size 80mb
```

