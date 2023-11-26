# nginx-install

## 1-安装对应依赖

- 1.1、登录dep-web-1（静态资源服务器）

- 1.2、确认gcc是否安装，如果提示未找到命令参考gcc安装文档[gcc安装](https://docs.qq.com/doc/DSGpCYkRpRE9LZE9Z)，已安装忽略即可。

```
[root@dep-web-1 ~]# gcc -v
-bash: gcc: 未找到命令
```

- 1.3、确认pcre-devel是否安装，如果提示未找到命令参考gcc安装文档[pcre-devel安装](https://docs.qq.com/doc/DT25ZSUlvZFJJb0FB)，已安装忽略即可。

```
[root@dep-web-1 opt]# rpm -qa pcre-devel
```

- 1.4、确认zlib-devel是否安装，如果提示未找到命令参考gcc安装文档[pcre-devel安装](https://docs.qq.com/doc/DT25ZSUlvZFJJb0FB)，已安装忽略即可。

```
[root@dep-web-1 lib]# yum list installed | grep zlib-devel
[root@dep-web-1 lib]#
```

## 2-安装、编译nginx

```shell
[root@dep-web-1 lib]# cd /opt
[root@dep-web-1 opt]# mkdir nginx #创建nginx目录
[root@dep-web-1 opt]# cd nginx/
[root@dep-web-1 nginx]# ll
总用量 1040
-rw-r--r--. 1 root root 1064925 6月   6 17:26 nginx-1.21.1.tar.gz
[root@dep-web-1 nginx]# tar -zxvf nginx-1.21.1.tar.gz #安装
[root@dep-web-1 nginx]# cd nginx-1.21.1/
[root@dep-web-1 nginx-1.21.1]# ./configure --prefix=/opt/nginx/  #编译、配置安装目录
[root@dep-web-1 nginx-1.21.1]# make && make install  #安装
[root@dep-web-1 nginx-1.21.1]# cd ..#返回上级nginx目录查看安装结果
[root@dep-web-1 nginx]# ll
 总用量 1044
drwxr-xr-x. 2 root root    4096 6月   6 17:32 conf #配置文件目录
drwxr-xr-x. 2 root root      40 6月   6 17:32 html
drwxr-xr-x. 2 root root       6 6月   6 17:32 logs
drwxr-xr-x. 9 1001 1001     186 6月   6 17:29 nginx-1.21.1
-rw-r--r--. 1 root root 1064925 6月   6 17:26 nginx-1.21.1.tar.gz
drwxr-xr-x. 2 root root      19 6月   6 17:32 sbin #可执行目录
[root@dep-web-1 nginx]#

```

## 3-**nginx配置**

```shell
[root@dep-web-1 nginx]# vim /opt/nginx/conf/nginx.conf  #修改配置文件，引入其他配置
```

在配置文件中插入  include /opt/nginx/conf.d/*.conf;

![1](img/nginx-install/1.png)

创建其他配置文件

```shell
[root@dep-web-1 nginx]# mkdir conf/conf.d #创建其他配置的目录
[root@dep-web-1 nginx]# cd conf/conf.d/
[root@dep-web-1 conf.d]# vim dep.conf  #创建交换前端配置，插入一下内容
server {
    listen       8888;
    server_name  localhost;
    location /dep-web {
        alias /home/dep/dep-server/dep-web; #此路径未前端资源存放路径
        autoindex on;
        client_max_body_size    1000m;
    }
}
```

校验配置文件格式是否正确

```shell
[root@dep-web-1 conf.d]# cd /opt/nginx/sbin/
[root@dep-web-1 sbin]# ./nginx -t  #假如执行时候报Permission denied错误就用 sudo  ./nginx -t
nginx: the configuration file /opt/nginx//conf/nginx.conf syntax is ok
nginx: configuration file /opt/nginx//conf/nginx.conf test is successful
```



## 4-启动、停止、重启nginx

```shell
[root@dep-web-1 sbin]# cd /opt/nginx/sbin
[root@dep-web-1 sbin]# ./nginx  #启动
[root@dep-web-1 sbin]# ./nginx  -s stop #停止
[root@dep-web-1 sbin]# ./nginx  -s reload #重启
```

## 5-验证

```she
ip:80
```

## 6-常见问题

- 6.1-nginx启动显示80端口被占用

```bash
解决办法：

使用netstat命令查看nginx服务是否已经启动

ps -ef|grep nginx

杀死对应的nginx进程

sudo kill -9 对应的进程号

启动nginx

./nginx -s start
```



- 6.2-网响应时间过长,浏览器无法访问nginx主页

```bash
解决办法

防火墙开启配置的80端口

开启端口

firewall-cmd --zone=public --add-port=80/tcp --permanent

重启防火墙：

firewall-cmd --reload

查询有哪些端口是开启的:

firewall-cmd --list-port
```



- 6.3-访问nginx网页错误403

```bash
原因：没有对应的权限，连接拒绝访问

解决办法

1.打开对应的nginx对应目录下的nginx配置文件:nginx.conf

2.修改配置文件

将对应的配置文件的注释去掉，并去掉nobody用户，添加root用户，之后保存重启nginx应用

user root;
worker_processes 1;
```

