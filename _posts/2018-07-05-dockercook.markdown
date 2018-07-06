---
layout: post
title:  "docker基本使用命令"
date:   2018-07-05 23:00:00 +0800
categories: docker
---
### 强大的help
```
docker --help
```
会列出所有的命令及说明，如下：
```
Usage:	docker COMMAND

A self-sufficient runtime for containers

Options:
      --config string      Location of client config files (default "/Users/lujiafeng/.docker")
  -D, --debug              Enable debug mode
      --help               Print usage
  ...

Management Commands:
  checkpoint  Manage checkpoints
  config      Manage Docker configs
  ...

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  ...
```
### 启动镜像成容器
```
docker run -it --rm -p 8888:8080 tomcat:latest
```
* 其中“-it”代表开启交互功能，即容器内tomcat启动日志你将能看到。
* 其中“—rm”代表当启动的容器停止后自动删除该容器（不是镜像哦）。
* 其中“-p 8888:8080”代表将容器中的8080端口映射到本地机器的8888端口上，即我们可以通过localhost:8888端口访问到tomcat，甚至我可以改变本地端口来启动多个tomcat容器。
* 最后的“tomcat:latest”代表启动的容器名称及其版本标签。
### 查看docker容器
```
docker ps # 查看运行中的容器
docker ps -a # 查看所有容器
```
### 进入容器内部执行命令
```
docker exec -it [container id] /bin/bash
```
### 停止运行中的容器
```
docker stop [container id]
```
### 启动停止状态的容器
```
docker start [container id]
```
### 删除容器
```
docker rm [container id]
```
