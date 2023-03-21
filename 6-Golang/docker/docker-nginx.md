# docker-nginx

- [docker-nginx安装](https://blog.csdn.net/BThinker/article/details/123507820)

  

## 1-下载和安装



```
docker pull nginx

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

