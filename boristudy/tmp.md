## linux 目录
/etc 配置文件，如mysql的my.ini
/var 数据文件，如mysql中的具体数据库
/bin 二进制执行文件，如数据库的一些命令工具
/opt 一些选安装的软件吧


## linux 命令
- echo
echo >   覆盖写
echo >>  追加写
more 分页看文件内容

- mkdir
mkdir -p a/b/c
递归创建

- tar
tar命令：tar -zcvf/-zxvf
-c创建 -x 解压
-z 表示使用gzip格式
-v 看具体的日志
-f 指定一个归档的名字

- stat
显示指定文件的相关信息，比ls命令显示内容更多

- who
显示在线登陆用户

- hostname
显示主机名称
- uname
显示系统信息

- ps
- ps -e
显示瞬间的进程状态（常用）

- du
显示指定的文件or目录已使用的磁盘空间的总量

- df
- df -h
显示文件磁盘系统空间的使用情况（-h 表示以human能理解的形式展示）

- free
显示当前内存和交换空间的使用情况

- ifconfig
- ip a
显示网络接口信息

- netstat
显示网络状态信息

- clear
清屏

- kill
- kill -9 top
杀死一个进程

- systemctl status mysql
查看mysql的运行状态

- systemctl restart mysql
重新mysql

- whereis mysql
查询mysql相关的地址


- tee命令
Linux tee命令用于读取标准输入的数据，并将其内容输出成文件。
tee指令会从标准输入设备读取数据，将其内容输出到标准输出设备，同时保存成文件。


## vim相关命令
- :set number
- :set nonumber
- /hello
搜索




## root账号
- sudo
提权

- sudo passwd root
设置密码

- su [username]
默认切换到root账号

- contorl + c
中断
- control + d
退出（包括su到的账号）





## 文件描述
``` bash
drwxr-xr-x  4 borisjin  staff   128B  4 12 00:54 docker
```
可以分成4段:
> r:read w:write x:excute
- d : 文件类型（-表示文件）
- rwx : 用户权限
- r-x : 所在组权限
- r-x : 其他用户权限
数字设定法：
- 0 无权限
- 1 执行
- 2 写
- 读


修改文件权限
- chmod
- chmod [who] [+|-|=] [mode] filename
chmod +x test.sh
给test.sh文件加可执行的权限

修改文件owener
- chown
- chown [-R] username filename|dirname
- chown [-R] username:user_group filename|dirname



shell文件开头固定写法
``` bash
#!/bin/bash
```





## 软件包管理
查看系统版本
- lsb_release -a
安装/卸载/清理
- apt-get install｜remove｜autoremove｜autoclean










##
