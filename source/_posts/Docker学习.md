---
title: Docker学习
date: 2022-07-11 12:20:15
tags: Study
categories: Study
author: Lcy
---

# Docker 学习

[toc]

## Docker 概述

[Docker文档](https://docs.docker.com)

[DockerHub](https://hub.docker.com)

| 特性                     | 传统                   | Docker                                                       |
| ------------------------ | ---------------------- | ------------------------------------------------------------ |
| 应用的更快速的交付和部署 | 一堆帮助文档，安装程序 | 打包镜像发布测试，一键运行                                   |
| 更便捷的升级和扩缩容     |                        | 项目打包为镜像，整体升级，直接扩展                           |
| 更简单的运维             |                        | 测试环境高度一致                                             |
| 更高效的计算资源利用     |                        | 同时运行几十个tomcat？！内核级别的虚拟化，可以在一个物理机上可以运行很多的容器实例。 |

## Docker 安装

### Docker 基本组成

**镜像(image)：**

可以类比于一个模板，可以通过模板创建容器服务。tomcat镜像-->run-->tomcat01容器（提供服务器），通过镜像可以创建多个容器（最终服务运行或者项目运行就在容器中）

**容器(container)：**

Docker利用容器技术，独立运行一个或者一个组应用，通过镜像来创建的。
启动，停止，删除，基本命令!

可以理解为简易的linux

**仓库(repository)：**

存放镜像

DockerHub（默认国外）

国内：阿里云/华为云容器服务（配置镜像加速）



**Ubuntu docker安装并配置阿里云镜像加速：**[(9条消息) Ubuntu安装docker教程并配置阿里云镜像加速_危机！的博客-CSDN博客](https://blog.csdn.net/qq_43648470/article/details/108171050)

```shell
# 测试是否安装完毕
docker version
# 测试能否run helloworld
docker run hello-world
# 返回hello from docker就成功了

# 查看下载的镜像
root@ubuntu:~# docker images
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
hello-world   latest    18e5af790473   7 weeks ago   9.14kB
```

### Docker Run 流程：

![image-20211117224115635](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20211117224115635.png)

### 底层原理：

**Docker是怎么工作的**

Docker是一个Client-Server结构的系统，Docker的守护进程运行在在主机上，通过Socket从客户端访问！

DockerServer接收到Docker-Client的指令，就会执行指令

![image-20211117224650062](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20211117224650062.png)

Docker更快的原因是因为有更少的抽象层。

![image-20211117224746559](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20211117224746559.png)

所以新建一个容器的时候，Docker不需要想虚拟机一样重新加载一个操作系统内核，避免引导。虚拟机是加载GuestOS，分钟级别的，而Docker是利用宿主机的操作系统，省略了这个复杂的过程，秒级 ! 

## Docker 命令

### 帮助命令

```shell
docker version      # 显示docker版本信息
docker info         # 显示docker的系统信息
docker 命令 --help   # 帮助命令
```

帮助文档地址[docker | Docker Documentation](https://docs.docker.com/engine/reference/commandline/docker/)

### 镜像命令

#### docker images 查看本地的主机上的镜像

```shell
root@ubuntu:~# docker images
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
hello-world   latest    18e5af790473   7 weeks ago   9.14kB
# 解释
REPOSITORY   镜像的仓库源
TAG          镜像的标签
IMAGE ID     镜像的ID
CREATED      镜像的创建时间
SIZE         镜像的大小

# 可选项
-a, --all    列出所有镜像
-q, --quiet  只显示镜像id
-aq          列出所有镜像id
```

#### docker search 搜索镜像

```shell
# 搜索 星星500以上的ubuntu镜像
root@ubuntu:~# docker search --filter=STARS=500 ubuntu
NAME                             DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
ubuntu                           Ubuntu is a Debian-based Linux operating sys…   13142     [OK]       
dorowu/ubuntu-desktop-lxde-vnc   Docker image to provide HTML5 VNC interface …   587                  [OK]

```

#### docker pull 下载镜像

```shell
root@ubuntu:~# docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
a39c84e173f0: Pull complete 
Digest: sha256:626ffe58f6e7566e00254b638eb7e0f3b11d4da9675088f4781a50ae288f3322
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

# 指定版本下载
root@ubuntu:~# docker pull mysql:5.7
```

#### docker rmi 删除镜像

```shell
docker rmi -f 镜像id # 删除指定镜像
docker rmi -f 镜像id 镜像id # 删除多个镜像
docker rmi -f $(docker images -aq) # 删除全部镜像
```

### 容器命令

#### 新建容器并启动

``` shell
docker run [可选参数] image

# 参数说明
--name="Name"    容器名字 tomcat01 tomcat02 用来区分容器
-d               后台方式运行
-p               指定容器的端口  -p 8080:8080
	-p ip:主机端口:容器端口
	-p 主机端口:容器端口（常用）
	-p 容器端口
	容器端口
-P               随即指定端口

# 测试并进入容器

root@ubuntu:~# docker run -it ubuntu /bin/bash
root@ce6aec3c0df9:/# ls
bin  boot  dev  etc  home  lib  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

# 退回主机
root@ce6aec3c0df9:/# exit
exit
```

#### 列出所有运行主机

```shell
# docker ps 命令
       # 列出当前正在运行容器
-a     # 列出当前+历史运行过的
-n=num # 显示最近创建的容器
-q     # 只显示容器编号
-aq    # 列出所有的编号
root@ubuntu:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@ubuntu:~# docker ps -a
CONTAINER ID   IMAGE         COMMAND       CREATED         STATUS                      PORTS     NAMES
ce6aec3c0df9   ubuntu        "/bin/bash"   2 minutes ago   Exited (0) 51 seconds ago             admiring_bell
e561bab36a3d   hello-world   "/hello"      15 hours ago    Exited (0) 15 hours ago               youthful_morse
23bd436c8cd4   hello-world   "/hello"      15 hours ago    Exited (0) 15 hours ago               sleepy_chatelet
69ea02fb97ce   hello-world   "/hello"      15 hours ago    Exited (0) 15 hours ago               stupefied_bardeen

```

#### 退出容器

```shell
exit    # 直接退出
ctrl + p + Q # 不停止退出
```

#### 删除容器

```shell
docker rm 容器id                 #删除指定容器，不能删除正在运行的
docker rm -f $(docker ps -aq)   #删除所有容器
docker ps -a -qlxargs docker rm # 删除所有容器
```

#### 启动和停止容器

```shell
docker start 容器id          # 启动容器
docker restart 容器id        # 重启容器
docker stop 容器id           # 停止当前运行的容器
docker kill 容器id           # 强制停止当前容器
```

### 常用其他命令

#### 后台运行程序

```shell
# 命令docker run -d 镜像名
root@ubuntu:~# docker run -d ubuntu
9879828e928e7a6f3ff0d0b7d8d917dfa9bc6ef640e9a6bc857ba052bf2fc81c
#问题docker ps， 发现centos 停止了

#常见的坑: docker 容器使用后台运行，就必须要有要一个前台进程，docker发现没有应用，就会自动停止
# nginx,容器启动后，发现自己没有提供服务，就会立刻停止，就是没有程序了
```

#### 查看日志命令

docker logs -f -t --tail 10 容器id

#### 查看容器进程

```shell
root@ubuntu:~# docker start ce6aec3c0df9
ce6aec3c0df9
root@ubuntu:~# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS        PORTS     NAMES
ce6aec3c0df9   ubuntu    "/bin/bash"   12 minutes ago   Up 1 second             admiring_bell
root@ubuntu:~# docker top
"docker top" requires at least 1 argument.
See 'docker top --help'.

Usage:  docker top CONTAINER [ps OPTIONS]

Display the running processes of a container
root@ubuntu:~# docker top ce6aec3c0df9
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                10273               10250               0                   05:36               pts/0               00:00:00            /bin/bash
```

#### 查看容器元数据

```shell
root@ubuntu:~# docker inspect ce6aec3c0df9
[
    {
        "Id": "ce6aec3c0df9d7f892f45c7ab1c1873f4c8d911037015812e4cff60e7213ba72",
        "Created": "2021-11-18T05:24:12.389591454Z",
        "Path": "/bin/bash",
        "Args": [],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 10273,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2021-11-18T05:36:54.956183355Z",
            "FinishedAt": "2021-11-18T05:25:27.062396275Z"
        },
        "Image": "sha256:d5ca7a4456053674d490803005766890dd19e3f7e789a48737c0d462da531f5d",
        "ResolvConfPath": "/var/lib/docker/containers/ce6aec3c0df9d7f892f45c7ab1c1873f4c8d911037015812e4cff60e7213ba72/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/ce6aec3c0df9d7f892f45c7ab1c1873f4c8d911037015812e4cff60e7213ba72/hostname",
        "HostsPath": "/var/lib/docker/containers/ce6aec3c0df9d7f892f45c7ab1c1873f4c8d911037015812e4cff60e7213ba72/hosts",
        "LogPath": "/var/lib/docker/containers/ce6aec3c0df9d7f892f45c7ab1c1873f4c8d911037015812e4cff60e7213ba72/ce6aec3c0df9d7f892f45c7ab1c1873f4c8d911037015812e4cff60e7213ba72-json.log",
        "Name": "/admiring_bell",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "docker-default",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/35f0fe271735c4c7e0d5f6ccbdaa577f78542787bfe7b7a6214e6fd37556759d-init/diff:/var/lib/docker/overlay2/11eb11ae3a068ff4e17db8fa46d97e151577353e72dd544a8d7b757740389bae/diff",
                "MergedDir": "/var/lib/docker/overlay2/35f0fe271735c4c7e0d5f6ccbdaa577f78542787bfe7b7a6214e6fd37556759d/merged",
                "UpperDir": "/var/lib/docker/overlay2/35f0fe271735c4c7e0d5f6ccbdaa577f78542787bfe7b7a6214e6fd37556759d/diff",
                "WorkDir": "/var/lib/docker/overlay2/35f0fe271735c4c7e0d5f6ccbdaa577f78542787bfe7b7a6214e6fd37556759d/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "ce6aec3c0df9",
            "Domainname": "",
            "User": "",
            "AttachStdin": true,
            "AttachStdout": true,
            "AttachStderr": true,
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": true,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "Image": "ubuntu",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "d9efa03479865798f9abfcac8cde759809d3a2b65de856dbe1dd82e96740a8e5",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {},
            "SandboxKey": "/var/run/docker/netns/d9efa0347986",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "0dd60f72f926dd734eb3e2a2fb664d6c3967399133ea8180407ba59ef361ad25",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "0bf5731d3c704ec72e742cb00a5297b5745f5fe55869c6fc432a61b70620a9a7",
                    "EndpointID": "0dd60f72f926dd734eb3e2a2fb664d6c3967399133ea8180407ba59ef361ad25",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]
```

#### 进入当前正在运行的容器

```shell
#我们通常容器都是使用后台方式运行的，需要进入容器，修改一些配置

#命令
docker exec -it 容器id bashShell 

#测试

root@ubuntu:~# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS         PORTS     NAMES
ce6aec3c0df9   ubuntu    "/bin/bash"   16 minutes ago   Up 4 minutes             admiring_bell
root@ubuntu:~# docker exec -it ce6aec3c0df9 /bin/bash
root@ce6aec3c0df9:/# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 05:36 pts/0    00:00:00 /bin/bash
root         9     0  1 05:41 pts/1    00:00:00 /bin/bash
root        17     9  0 05:41 pts/1    00:00:00 ps -ef

# 方式二
docker attach 容器id

# docker exec   # 进入容器后开启一个新的终端，可以在里面操作
# docker attach # 进入容器正在执行的终端，不会启动新的进程
```

#### 从容器内拷贝文件到主机上

```shell
docker cp 容器id:容器内路径 目的主机路径
# 可以使用-v卷的技术自动同步
```

## 容器数据卷

### 什么是容器数据卷

**docker理念回顾**

将应用打包成一个镜像

==需求：数据可以持久化==

可以做一个数据共享。Docker中的数据同步到本地

容器之间可以有一个数据共享的技术! Docker 容器中产生的数据，同步到本地!
这就是卷技术!目录的挂载，将我们容器内的目录，挂载到Linux上面! 

> 方式一：直接使用-v命令挂载

```shell
docker run -it -V /home/ceshi: /home ubuntu /bin/bash
```

> 方式二：Dockerfile 就是用来构建docker镜像的构建文件，就是一个命令脚本
>
> 通过脚本生成镜像，镜像是一层一层的，脚本一个个的命令都是一层

```shell
root@ubuntu:/home# mkdir docker-test-volume
root@ubuntu:/home# cd docker-test-volume
root@ubuntu:/home/docker-test-volume# pwd
/home/docker-test-volume
root@ubuntu:/home/docker-test-volume# vim dockerfile
root@ubuntu:/home/docker-test-volume# cat dockerfile
FROM ubuntu

VOLUME ["volume01","volume02"] # 匿名挂载

CMD echo "------end------"
CMD /bin/bash
root@ubuntu:/home/docker-test-volume# docker build -f dockerfile -t respifisco:1.0
"docker build" requires exactly 1 argument.
See 'docker build --help'.

Usage:  docker build [OPTIONS] PATH | URL | -

Build an image from a Dockerfile
root@ubuntu:/home/docker-test-volume# docker build -f dockerfile -t respifisco:1.0 .
Sending build context to Docker daemon  2.048kB
Step 1/4 : FROM ubuntu
 ---> d5ca7a445605
Step 2/4 : VOLUME ["volume01","volume02"]
 ---> Running in af0aca7a1acc
Removing intermediate container af0aca7a1acc
 ---> 886d53869a5f
Step 3/4 : CMD echo "------end------"
 ---> Running in 01d8de6fd880
Removing intermediate container 01d8de6fd880
 ---> db0ff6f6ca87
Step 4/4 : CMD /bin/bash
 ---> Running in 73439e670a07
Removing intermediate container 73439e670a07
 ---> 0fa242d56fe6
Successfully built 0fa242d56fe6
Successfully tagged respifisco:1.0

```

```shell
        "Mounts": [
            {
                "Type": "volume",
                "Name": "806c0f5e3d65489fbde5e2992f979a6bbb06bb05992ff359cfdb2470c691d6b6",
                "Source": "/var/lib/docker/volumes/806c0f5e3d65489fbde5e2992f979a6bbb06bb05992ff359cfdb2470c691d6b6/_data",
                "Destination": "volume01",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            },
            {
                "Type": "volume",
                "Name": "f51a8037b91db17579771a21403fa85c8a1aea3e1657a46b1cb9683d524ac42d",
                "Source": "/var/lib/docker/volumes/f51a8037b91db17579771a21403fa85c8a1aea3e1657a46b1cb9683d524ac42d/_data",
                "Destination": "volume02",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],
```

## Docker File（构建自己的镜像）

dockerfile是用来构建dokcer镜像的文件!命令参数脚本!
构建步骤:
1、编写一个dockerfile 文件
2、docker build构建成为一个镜像
3、docker run运行镜像
4、docker push发布镜像( DockerHub、阿里云镜像仓库! )

基础知识:
1、每个保留关键字(指令)都是必须是大写字母
2、执行从上到下顺序执行
3、#表示注释.
4、每一个指令都会创建提交一个新的镜像层,并提交!

![image-20211118224824710](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20211118224824710.png)

dockerfile是面向开发的,我们以后要发布项目,做镜像,就需要编写dockerfile文件,这个文件十分简单!
Docker镜像逐渐成为企业交付的标准,必须要掌握!
步骤: 开发，部署，运维。。。缺一不可!
DockerFile :构建文件，定义了一切的步骤，源代码
Dockerlmages :通过DockerFile构建生成的镜像，最终发布和运行的产品! 
Docker容器:容器就是镜像运行起来提供服务器
