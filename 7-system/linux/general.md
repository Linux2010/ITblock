## 通用命令

### linux用户创建删除操作   
- [linux创建新用户](https://blog.csdn.net/li_101357/article/details/69367457)
- [Linux中添加、修改和删除用户和用户组](https://blog.csdn.net/GMingZhou/article/details/78706439)
```shell
useradd -m username
passwd pwd
```
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
### df du
```
# 查看磁盘挂载
df -h
# 查看指定文件大小
du -sh filename
# 查询当前目录文件占用情况
du -lh 

1. df -lh

2. du -s /usr/* | sort -rn

这是按字节排序

3. du -sh /usr/* | sort -rn

这是按兆（M）来排序

4.选出排在前面的10个

du -s /usr/* | sort -rn | head

5.选出排在后面的10个

du -s /usr/* | sort -rn | tail
du -h –-max-depth=0 user
du -sh –-max-depth=2 | more

总结du常用命令

du -h --max-depth=1 |grep [TG] |sort   #查找上G和T的目录并排序
du -sh    #统计当前目录的大小，以直观方式展现
du -h --max-depth=1 |grep 'G' |sort   #查看上G目录并排序
du -sh --max-depth=1  #查看当前目录下所有一级子目录文件夹大小
du -h --max-depth=1 |sort    #查看当前目录下所有一级子目录文件夹大小 并排序
du -h --max-depth=1 |grep [TG] |sort -nr   #倒序排

本文具体介绍了linux中du命令參数的用法，并用演示例子进一步说明其用法。
Du命令功能说明：统计文件夹(或文件)所占磁盘空间的大小。
语法：du [-abcDhHklmsSx] [-L <符号连接>][-X <文件>][--block-size][--exclude=<文件夹或文件>] [--max-depth=<文件夹层数>][-

-help][--version][文件夹或文件]
常常使用參数：
-a或-all 为每一个指定文件显示磁盘使用情况，或者为文件夹中每一个文件显示各自磁盘使用情况。
-b或-bytes 显示文件夹或文件大小时，以byte为单位。
-c或–total 除了显示文件夹或文件的大小外，同一时候也显示全部文件夹或文件的总和。
-D或–dereference-args 显示指定符号连接的源文件大小。
-h或–human-readable 以K，M，G为单位，提高信息的可读性。
-H或–si 与-h參数同样，可是K，M，G是以1000为换算单位,而不是以1024为换算单位。
-k或–kilobytes 以1024 bytes为单位。
-l或–count-links 反复计算硬件连接的文件。
-L<符号连接>或–dereference<符号连接> 显示选项中所指定符号连接的源文件大小。
-m或–megabytes 以1MB为单位。
-s或–summarize 仅显示总计，即当前文件夹的大小。
-S或–separate-dirs 显示每一个文件夹的大小时，并不含其子文件夹的大小。
-x或–one-file-xystem 以一開始处理时的文件系统为准，若遇上其它不同的文件系统文件夹则略过。
-X<文件>或–exclude-from=<文件> 在<文件>指定文件夹或文件。
–exclude=<文件夹或文件> 略过指定的文件夹或文件。
–max-depth=<文件夹层数> 超过指定层数的文件夹后，予以忽略。
–help 显示帮助。
–version 显示版本号信息。
linux中的du命令使用演示例子:
1> 要显示一个文件夹树及其每一个子树的磁盘使用情况
du /home/linux
这在/home/linux文件夹及其每一个子文件夹中显示了磁盘块数。
2> 要通过以1024字节为单位显示一个文件夹树及其每一个子树的磁盘使用情况
du -k /home/linux
这在/home/linux文件夹及其每一个子文件夹中显示了 1024 字节磁盘块数。
3> 以MB为单位显示一个文件夹树及其每一个子树的磁盘使用情况
du -m /home/linux
这在/home/linux文件夹及其每一个子文件夹中显示了 MB 磁盘块数。
4> 以GB为单位显示一个文件夹树及其每一个子树的磁盘使用情况
du -g /home/linux
这在/home/linux文件夹及其每一个子文件夹中显示了 GB 磁盘块数。
5>查看当前文件夹下全部文件夹以及子文件夹的大小：
du -h .
“.”代表当前文件夹下。也能够换成一个明白的路径
-h表示用K、M、G的人性化形式显示
6>查看当前文件夹下user文件夹的大小，并不想看其它文件夹以及其子文件夹：
du -sh user
-s表示总结的意思，即仅仅列出一个总结的值
du -h --max-depth=0 user
--max-depth＝n表示仅仅深入到第n层文件夹，此处设置为0，即表示不深入到子文件夹。
7>列出user文件夹及其子文件夹下全部文件夹和文件的大小：
du -ah user
-a表示包含文件夹和文件
8>列出当前文件夹中的文件夹名不包含xyz字符串的文件夹的大小：
du -h –exclude='*xyz*'
9>想在一个屏幕下列出许多其他的关于user文件夹及子文件夹大小的信息：
du -0h user
-0（杠零）表示每列出一个文件夹的信息，不换行，而是直接输出下一个文件夹的信息。
10>仅仅显示一个文件夹树的全部磁盘使用情况
du -s /home/linux

以上内容就是小编给大家介绍的Linux du命令查看文件夹大小并按降序排列的全部叙述，希望大家喜欢



```

### zip压缩
```shell
#添加当前文件夹到 name.zip
zip -r name.zip *
```

### grep操作
- [linux 用 grep 查找单个或多个字符串（关键字）](https://cloud.tencent.com/developer/article/1793323)
```shell
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


### scp
- [使用scp命令在本地和服务器之间传输文件](https://blog.csdn.net/cm_mz/article/details/124461259)

- [关于linux：scp是否创建目标文件夹(如果不存在)](https://www.codenong.com/12920947/)

### crontab
- [crontab命令](https://www.laobuluo.com/9297.html)
- [cron表达式](https://cron.qqe2.com/)

### find
- 查找大文件
  - find / -type f -size +1G