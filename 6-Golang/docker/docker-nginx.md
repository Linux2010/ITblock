# docker-nginx

- [docker-nginx安装](https://blog.csdn.net/BThinker/article/details/123507820)



## 1-准备工作

- vim /opt/nginx/html/index.html

```html
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

- vim /opt/nginx/conf/nginx.conf

```bash
user  root;
worker_processes  auto;

error_log  /var/log/nginx/error.log notice;
pid        /var/run/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    keepalive_timeout  65;

    #gzip  on;

    include /etc/nginx/conf.d/*.conf;
    server{
       listen 80;
       charset utf-8;
       server_name localhost; 
       location /hope-web {
          add_header 'Access-Control-Allow-Origin' *;
          #允许带上cookie请求
          add_header 'Access-Control-Allow-Credentials' 'true';
          #允许请求的方法，比如 GET/POST/PUT/DELETE
          add_header 'Access-Control-Allow-Methods' *;
          #允许请求的header
          add_header 'Access-Control-Allow-Headers' *;
          root /usr/share/nginx/html;# 根⽬录
          index index.html index.htm;
          proxy_pass http://localhost:9527;
          proxy_redirect default; 
       }
    }
}

```

- vim /opt/nginx/conf/conf.d/*.conf
  - 添加业务配置，以下为示例

```
```



## 2-下载和安装



```
# 创建挂载目录
mkdir -p /opt/nginx/conf
mkdir -p /opt/nginx/log
mkdir -p /opt/nginx/html

docker run \
-p 80:80 \
--name nginx \
-v /opt/nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
-v /opt/nginx/conf/conf.d:/etc/nginx/conf.d \
-v /opt/nginx/log:/var/log/nginx \
-v /opt/nginx/html:/usr/share/nginx/html \
-d nginx:latest

```



## 2-	

