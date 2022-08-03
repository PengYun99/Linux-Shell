A - CentOS 7 命令

[Linux 命令大全 | 菜鸟教程 (runoob.com)](https://www.runoob.com/linux/linux-command-manual.html)

# CentOS 7 终端命令

| 功能                                         | 命令                                                         |
| -------------------------------------------- | ------------------------------------------------------------ |
| 打开终端（需要预先设置）                     | Alt+Ctrl+T                                                   |
| root模式                                     | su 仅切换root身份<br>su - 完全切换到root，shell、环境变量等都是root |
| 其他账户模式                                 | su - username                                                |
| 返回上一层                                   | exit                                                         |
| 关机                                         | shutdown -h now                                              |
| 重启                                         | shutdown -r now                                              |
| 查询磁盘使用情况                             | df -hl （随便在哪个路径都可）                                |
| 罗列使用CPU资源最多的linux任务 （输入q退出） | top                                                          |
| 以树状图显示程序                             | pstree                                                       |
| 查看参考手册（如ping命令）                   | man ping                                                     |
| 修改密码                                     | passwd                                                       |
| 显示前一月，当前月以及下个月的日历           | cal -3                                                       |
| 显示指定月、年的日历                         | cal 10 2021                                                  |
| 把相对于1970-01-01 00:00:00 的秒数转换成时间 | date -date ‘1970-01-01 UTC 1427888888 seconds’               |

# 文件及目录

| 功能             | 命令                                                         |
| ---------------- | ------------------------------------------------------------ |
| 进入`/home`目录  | cd /home                                                     |
| 进入下一级       | cd ./xxx(文件夹名)/xxx(文件夹名)                             |
| 返回上一级       | cd …                                                         |
| 返回上两级       | cd …/…                                                       |
| 返回上次所在目录 | cd -                                                         |
| 复制file1为file2 | cp file1 file2                                               |
| 复制文件夹       | cp -a dir1 dir2                                              |
| 显示文件夹内容   | ll或ls                                                       |
| 显示隐藏文件     | ls -a                                                        |
| 显示详细信息     | ls -l                                                        |
| 按时间显示文件   | ls -lrt (l - 详细列表，r - 反向排序，t - 按时间排序)         |
| 显示工作路径     | pwd                                                          |
| 创建文件夹       | mkdir newfilename<br>chmod 777 newfilename/ (给予新文件夹全部权限) |
| 创建一个目录     | mkdir dir1                                                   |
| 创建两个目录     | mkdir dir1 dir2                                              |
| 创建目录树       | mkdir -p /tmp/dir1/dir2                                      |
| 移动/重命名目录  | mv dir1 dir2                                                 |
| 删除文件/文件夹  | rm -r xxx/ (当前路径在xxx文件夹的父级，删除xxx文件夹及其文件)<br>rm -r ./xxxx/xxxx/xx (不管当前路径在哪里，指定删除xx文件夹) |
| 强制删除文件     | rm -f xx                                                     |
| 强制删除文件夹   | rm -rf xxx                                                   |
| 创建空白文件     | touch xxx.后缀名<br>vim xxx.后缀名                           |

## 查看文件内容

| 命令          | 功能                                 |
| ------------- | ------------------------------------ |
| cat file1     | 从第一个字节开始正向查看文件的内容   |
| head -2 file1 | 查看一个文件的前两行                 |
| more file1    | 查看一个长文件的内容                 |
| tac file1     | 从最后一行开始反向查看一个文件的内容 |
| tail -3 file1 | 查看一个文件的最后三行               |
| vi file       | 打开并浏览文件                       |

## 文本内容处理

| 命令                   | 功能                              |
| ---------------------- | --------------------------------- |
| grep str /tmp/test     | 在文件 test 中查找 str            |
| grep ^str /tmp/test    | 在文件 test 中查找以 str 开始的行 |
| grep \[0-9\] /tmp/test | 查找 test 文件中所有包含数字的行  |
| diff file1 file2       | 找出两个文件的不同处              |
| sdiff file1 file2      | 以对比的方式显示两个文件的不同    |

## vim编辑(vi file后)

| 命令 | 功能             |
| ---- | ---------------- |
| i    | 进入编辑文本模式 |
| Esc  | 退出编辑文本模式 |
| :w   | 保存当前修改     |
| :q   | 不保存退出vi     |
| :q!  | 强制退出         |
| :wq  | 保存并退出       |
| :wq! | 强制保存并退出   |

## 运行文件

| 命令         | 功能       |
| ------------ | ---------- |
| python **.py | 运行py文件 |

## 查询操作

| 命令                                             | 功能                                            |
| ------------------------------------------------ | ----------------------------------------------- |
| find / -name file1                               | 从 / 开始进入根文件系统查找文件和目录           |
| find / -user user1                               | 查找属于用户 user1 的文件和目录                 |
| find /home/user1 -name *.bin                     | 在目录 /home/user1 中查找以 .bin 结尾的文件     |
| find /usr/bin -type f -atime +100                | 查找过去100天内未被使用过的执行文件             |
| find /usr/bin -type f -mtime -10                 | 查找10天内被创建或者修改过的文件                |
| locate *.ps                                      | 寻找以 .ps 结尾的文件，先运行 updatedb 命令     |
| find -name ‘*.\[ch\]’ \| xargs grep -E ‘expr’    | 在当前目录及其子目录所有.c和.h文件中查找 ‘expr’ |
| find -type f -print0 \| xargs -r0 grep -F ‘expr’ | 在当前目录及其子目录的常规文件中查找 ‘expr’     |
| find -maxdepth 1 -type f \| xargs grep -F ‘expr’ | 在当前目录中查找 ‘expr’                         |

# 压缩解压

| 功能    | 命令                                                         |
| ------- | ------------------------------------------------------------ |
| tar     | tar -cvf xxx.tar file1 [//压缩.tar](//xn--omry82h.tar) (filename是指要压缩的文件名称) |
|         | tar -xvf **.tar //解压tar包                                  |
|         | tar -xvf **.tar -C newdir //解压tar包到指定路径(所有解压均可指定路径,-C 必须大写) |
| tar.gz  | tar -zcvf newfilename.tar.gz filename [//压缩tar.gz](//xn--tar-vo3e070r.gz) |
|         | tar -zxvf **.tar.gz // 解压tar.gz                            |
| zip     | zip -r newfilename.zip filename                              |
|         | unzip **.zip                                                 |
| tar.bz2 | tar -jcvf newfilename.tar.bz2 filename                       |
|         | tar -jxvf **.tar.bz2 //解压 tar.bz2                          |
| tar.z   | tar -xZvf **.tar.Z // 解压tar.z                              |
| gz      | gunzip **.gz //解压gz                                        |
| rar     | unrar **.rar //解压rar                                       |

# yum安装器

| 命令                             | 功能                                              |
| -------------------------------- | ------------------------------------------------- |
| yum -y install \[package\]       | 下载并安装一个 rpm 包                             |
| yum localinstall \[package.rpm\] | 安装一个rpm包，使用自己的软件仓库解决所有依赖关系 |
| yum -y update                    | 更新当前系统中安装的所有rpm包                     |
| yum update \[package\]           | 更新一个rpm包                                     |
| yum remove \[package\]           | 删除一个rpm包                                     |
| yum list                         | 列出当前系统中安装的所有包                        |
| yum search \[package\]           | 在rpm仓库中搜寻软件包                             |
| yum clean \[package\]            | 清楚缓存目录 （/var/cache/yum）下的软件包         |
| yum clean headers                | 删除所有头文件                                    |
| yum clean all                    | 删除所有缓存的包和头文件                          |

# 网络相关

| 命令                                            | 功能                   |
| ----------------------------------------------- | ---------------------- |
| ifconfig eth0                                   | 显示一个以太网卡的配置 |
| ifconfig eth0 192.168.1.1 netmask 255.255.255.0 | 配置网卡的IP地址       |
| ifdown eth0                                     | 禁用 ‘eth0’ 网络设备   |
| ifup eth0                                       | 启用 ‘eth0’ 网络设备   |
| iwconfig eth1                                   | 显示一个无线网卡的配置 |
| iwlist scan                                     | 显示无线网络           |
| ip addr show                                    | 显示网卡的IP地址       |

# 磁盘空间

| 命令      | 功能                                     |
| --------- | ---------------------------------------- |
| df -TH    | 查看每个可用分区大小、已用大小、剩余大小 |
| fdisk -l  | 显示当前分区情况                         |
| fdisk -lu | 显示每个分区情况                         |
