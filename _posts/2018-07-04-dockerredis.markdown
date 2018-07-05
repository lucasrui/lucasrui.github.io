---
layout: post
title:  "Docker快速安装部署redis"
date:   2018-07-05 23:00:00 +0800
categories: redis docker
---
1. 查找Docker Hub上的redis镜像
```
tuilu@tuilu:~/redis$ docker search  redis
NAME                      DESCRIPTION                   STARS  OFFICIAL  AUTOMATED
redis                     Redis is an open source ...   2321   [OK]       
sameersbn/redis                                         32                   [OK]
torusware/speedus-redis   Always updated official ...   29             [OK]
bitnami/redis             Bitnami Redis Docker Image    22                   [OK]
anapsix/redis             11MB Redis server image ...   6                    [OK]
webhippie/redis           Docker images for redis       4                    [OK]
clue/redis-benchmark      A minimal docker image t...   3                    [OK]
williamyeh/redis          Redis image for Docker        3                    [OK]
unblibraries/redis        Leverages phusion/baseim...   2                    [OK]
greytip/redis             redis 3.0.3                   1                    [OK]
servivum/redis            Redis Docker Image            1                    [OK]
...
```
2. 拉取官方的镜像,标签为3.2。需要几分钟时间进行下载
```
tuilu@tuilu:~/redis$ docker pull  redis:3.2
```
3. 运行容器
```
tuilu@tuilu:~/redis$ docker run -p 6379:6379 -v $PWD/data:/data  -d redis:3.2 redis-server --appendonly yes
43f7a65ec7f8bd64eb1c5d82bc4fb60e5eb31915979c4e7821759aac3b62f330
```
**参数说明**
    1. -p 6379:6379 : 将容器的6379端口映射到主机的6379端口
    2. -v $PWD/data:/data : 将主机中当前目录下的data挂载到容器的/data
    3. redis-server --appendonly yes : 在容器执行redis-server启动命令，并打开redis持久化配置
4. 查看容器启动情况
```
tuilu@tuilu:~/redis$ docker ps
CONTAINER ID   IMAGE        COMMAND                 ...   PORTS                      NAMES
43f7a65ec7f8   redis:3.2    "docker-entrypoint.sh"  ...   0.0.0.0:6379->6379/tcp     agitated_cray
```
5. 连接、查看容器
```
tuilu@tuilu:~/redis$ docker exec -it 43f7a65ec7f8 redis-cli
172.17.0.1:6379> info
# Server
redis_version:3.2.0
redis_git_sha1:00000000
redis_git_dirty:0
redis_build_id:f449541256e7d446
redis_mode:standalone
os:Linux 4.2.0-16-generic x86_64
arch_bits:64
multiplexing_api:epoll
...
```
