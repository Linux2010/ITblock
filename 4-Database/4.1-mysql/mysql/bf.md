# mysql迁移备份

- [Mysql三种常见备份表方式](https://blog.csdn.net/free_yx/article/details/123520109)

```shell
mysql -h -P 3306 -uroot -p 
mysqldump -h hope-db -P 3306 -uroot -pTianfs@2020!!  hope_engine  upload_instance > /root/upload_instance.sql

```