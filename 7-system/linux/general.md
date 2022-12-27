## 通用命令

### linux用户创建删除操作   
- [linux创建新用户](https://blog.csdn.net/li_101357/article/details/69367457)
- [Linux中添加、修改和删除用户和用户组](https://blog.csdn.net/GMingZhou/article/details/78706439)

### rm 操作
- [Linux操作系统之rm命令详解 ](https://www.cnblogs.com/hls-code/p/16692397.html)
```shell
# 慎用，无法复原
rm -rf filename

# 使用以下操作比较安全
# 1,删除文件到回收站
rm -r filename
# 2，清理回收站
rm -rf ~/.local/share/Trash/filename
# 3，
```
### 查看文件磁盘占用情况
```shell
# 查看磁盘挂载
df -h
# 查看指定文件大小
du -sh filename
# 查询当前目录文件占用情况
du -lh 
```

### zip压缩
```shell
#添加当前文件夹到 name.zip
zip -r name.zip *
```