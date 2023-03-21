## docker-mysql安装
### 流程安装
- [docker-mysql安装](https://juejin.cn/post/7031188920511660063)

- 1. 启动docker-mysql

```shell
docker pull mysql:8.0.23

sudo docker run -p 3306:3306 --name mysql \
-v /docker/mysql/mysql-files:/var/lib/mysql-files \
-v /docker/mysql/conf:/etc/mysql \
-v /docker/mysql/logs:/var/log/mysql \
-v /docker/mysql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql:8.0.23 --lower-case-table-names=1


```
- 2，设置外部访问

```shell
sudo docker exec -it mysql bash
mysql -uroot -p
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root'; 
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root'; 

```
- 3，添加my.cnf的方法
  * 3.1，以docker配置参数 -v /docker/mysql/conf:/etc/mysql 为例 
  * 3.2，在/docker/mysql/conf中添加空文件 my.cnf 
  * 3.3，vim my.cnf 添加如下配置 
```shell
[mysqld]
# 解决docker版本链接慢
skip-name-resolve
# 设置时区
default-time-zone=Asia/Shanghai
# show variables like '%max_connections%';查看最大连接数
max_connections=1024
# 配置闲置链接超时时间
wait_timeout=31536000
interactive_timeout=31536000
# 服务端使用的字符集默认为UTF8
character-set-server=utf8mb4
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
default-character-set=utf8mb4

```


