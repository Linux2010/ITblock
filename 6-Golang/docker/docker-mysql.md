## docker-mysql安装
### 流程安装
- [docker-mysql安装](https://juejin.cn/post/7031188920511660063)
```shell
docker pull mysql:8.0.23

sudo docker run -p 3306:3306 --name mysql \
-v /root/mysql/mysql-files:/var/lib/mysql-files \
-v /root/mysql/conf:/etc/mysql \
-v /root/mysql/logs:/var/log/mysql \
-v /root/mysql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql:8.0.23


```


### 添加my.cnf的方法
1，以docker配置参数 -v /root/mysql/conf:/etc/mysql 为例 \
2，在/root/mysql/conf中添加空文件 my.cnf \
3，vim my.cnf 添加如下配置 \
```shell
default-time-zone=Asia/Shanghai
# show variables like '%max_connections%';查看最大连接数
max_connections=1024
# 配置闲置链接超时时间
wait_timeout=31536000
interactive_timeout=31536000

```
```shell
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=/usr/local/mysql
# 设置mysql数据库的数据的存放目录
datadir=/usr/local/mysql/mysqldb
# 允许最大连接数
max_connections=1000
# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=100
# 服务端使用的字符集默认为UTF8
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
default_authentication_plugin=mysql_native_password
#是否对sql语句大小写敏感，1表示不敏感
lower_case_table_names = 1
#MySQL连接闲置超过一定时间后(单位：秒)将会被强行关闭
#MySQL默认的wait_timeout  值为8个小时, interactive_timeout参数需要同时配置才能生效
interactive_timeout = 1800
wait_timeout = 1800
#Metadata Lock最大时长（秒）， 一般用于控制 alter操作的最大时长sine mysql5.6
#执行 DML操作时除了增加innodb事务锁外还增加Metadata Lock，其他alter（DDL）session将阻塞
lock_wait_timeout = 3600
#内部内存临时表的最大值。
#比如大数据量的group by ,order by时可能用到临时表，
#超过了这个值将写入磁盘，系统IO压力增大
tmp_table_size = 64M
max_heap_table_size = 64M
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8mb4
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4


```
