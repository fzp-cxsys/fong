---
title: "Docker Machine"
date: 2019-01-09
categories: [platform, docker]
tags: [Docker, Docker Machine]
---

### 记录几个问题

1. docker-machine下载问题，docker-machine工具以及boot2docker镜像的下载国内较慢。
2. host主机网络连接问题，疑似防火墙问题；并没有防火墙问题，根据hostname无法连接，因为没有配置hostname和ip的映射，两个虚拟机与host主机处于同一虚拟局域网内，可以通过ip连接。
3. zookeeper服务间网络连接问题，经排查发现，通过container内部hostname获取的ip不一致，此处需详细学习了解unix网络状态。不是这个问题导致的，但是这个问题什么原因不知道。经过对日志的分析服务启动失败是因为有个节点的myid配置错误，因为myid是配置在挂载的volume中的，第一次配置错误，后面重启docker service依然使用旧的volume，导致错误配置无法被覆盖。
