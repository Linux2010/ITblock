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

### grep操作
- [linux 用 grep 查找单个或多个字符串（关键字）](https://cloud.tencent.com/developer/article/1793323)
```
1、单个字符串进行查找：

1、查找当前目录文件名中的字符串：    grep  字符串  文件名

2、查找某个文件中字符串，并输出行号：grep -n 字符串 文件名

3、查找当前目录（包含子目录）的字符串：grep -r 字符串 *

4、查找当前目录（包含子目录）的字符串，并输出行号：grep -rn 字符串 *

* :通配符，表示当前目录所有文件，也可以按照某种模式进行匹配，例如：

    grep 字符串 *.txt   匹配所有文件后缀名为txt的字符串

-r ：递归查找

-n ：显示行号

-R ：查找所有文件包含子目录

-i ：忽略大小写

2、同时满足多个字符串查找：

grep 字符串1 文件名| grep 字符串2|grep 字符串3|grep ...

3、满足多个关键字之一

grep -E "字符串1|字符串2|字符串3|"  文件名   或者

egrep  "字符串1|字符串2|字符串3|"  文件名


```