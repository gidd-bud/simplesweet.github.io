# Docker 随记

Docker 是一个开源的应用容器引擎，基于`Go 语言`并遵从`Apache2.0`协议开源。

## 常用命令

- 镜像操作

```bash
# 查找包
➜  docker search mysql

# 抽取指定版本包。":tag"表示软件的版本，默认为"latest"
➜  docker pull mysql:latest

# 查看所有本地镜像
➜  docker images

# 获取镜像的元信息，详细信息
➜  docker inspect 镜像id

# 删除指定的本地镜像，-f表示强制删除
➜  docker mi -f 镜像id或镜像名:tag
```

- 容器操作

```bash
# 运行。
➜  docker run --name 容器名 -i -t -p 主机端口:容器端口 -d -v 主机目录:容器目录:ro 镜 像id或镜像名称:tag
# --name 指定容器名，名称自定义，如果不指定会自动命名；
# -i 以交互模式运 行，即以交互模式运行容器；
# -t 分配一个伪终端，即命令行，通常组合使用-it ；
# -p 指定端口映射，将主机端口映射到容器内的端口；
# -d 表示后台运行，即守 护式运行容器；
# -v 指定挂载主机目录到容器目录；
# 默认为rw读写模式，ro表示 只读

# 查看正在运行的容器，-a表示显示所有容器，-q表示只显示容器id
➜  docker ps -a -q

# 启动容器
➜  docker start 容器id或容器名称

# 获取镜像的元信息，详细信息
➜  docker inspect 镜像id

# 删除指定的本地镜像，-f表示强制删除
➜  docker mi -f 镜像id或镜像名:tag
```
