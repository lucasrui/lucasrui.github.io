---
layout: post
title:  "Docker快速安装部署zookeeper"
date:   2018-07-05 23:00:00 +0800
categories: zookeeper docker
---
1. 镜像下载
```
docker pull zookeeper
```
2. 启动 ZK 镜像
```
docker run --name my_zookeeper -d zookeeper:latest
```
* 这个命令会在后台运行一个 zookeeper 容器, 名字是 my_zookeeper, 并且它默认会导出 2181 端口.
3. 查看zk运行情况
```
docker logs -f my_zookeeper
```
输出如下内容表示启动成功
```
docker logs -f my_zookeeper
ZooKeeper JMX enabled by default
Using config: /conf/zoo.cfg
...
2016-09-14 06:40:03,445 [myid:] - INFO  [main:NIOServerCnxnFactory@89] - binding to port 0.0.0.0/0.0.0.0:2181
```
4. 连接、查看zk
```
docker run -it --rm --link my_zookeeper:zookeeper zookeeper zkCli.sh -server zookeeper
```
