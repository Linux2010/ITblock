## Redis 单节点安装-linux服务器

### 1, 将redis-5.0.9.tar.gz包上传到A服务器 /install-pkgs文件下
### 2，解压redis-5.0.9.tar.gz

>tar -zxvf redis-5.0.9.tar.gz

### 3，编译安装

```shell
cd redis-5.0.9
make
如果报错，可能没有gcc环境，请先安装gcc环境
```
### 4，修改redis.conf配置文件，需要修改4处

```shell
cd /install-pkgs/redis-5.0.9
vim redis.conf

##关闭保护模式（88行）
protected-mode no
#开启后台启动（136行）
daemonize yes
#更改绑定ip，讲127.0.0.1 改为 0.0.0.0，不然连不进来（69行）
bind 0.0.0.0
#增加一个节点requirepass，表示将密码改为123456  （508行）
requirepass 123456

```




### 5.启动redis服务

```shell
cd /install-pkgs/redis-5.0.9/src
./redis-server ../redis.conf &
```

