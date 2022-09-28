---
title: 搭建一个属于自己的开源远程桌面服务-Rustdesk
date: 2022-09-29 00:09:31
tags: Docker
categories:
cover: http://tuchuang-10g.dongxiquan.cn/202209290012533.png
---
> 官网：[RustDesk | 开源远程桌面软件](https://rustdesk.com/zh/)

## 搭建

创建一下安装的目录：

```
mkdir -p /root/data/docker_data/rustdesk

cd /root/data/docker_data/rustdesk

nano docker-compose.yml

```

docker-compose.yml填入以下内容：

```
version: '3'

networks:
  rustdesk-net:
    external: false

services:
  hbbs:
    container_name: hbbs
    ports:
      - 21115:21115
      - 21116:21116
      - 21116:21116/udp
      - 21118:21118
    image: rustdesk/rustdesk-server:latest
    command: hbbs -r hbbs.example.com:21117   # hbbs.example.com改成自己的服务器IP
    volumes:
      - ./hbbs:/root
    networks:
      - rustdesk-net
    depends_on:
      - hbbr
    restart: unless-stopped

  hbbr:
    container_name: hbbr
    ports:
      - 21117:21117
      - 21119:21119
    image: rustdesk/rustdesk-server:latest
    command: hbbr
    volumes:
      - ./hbbr:/root
    networks:
      - rustdesk-net
    restart: unless-stopped

```

没问题的话，ctrl+x退出，按y保存，enter确认。

打开防火墙的端口21115、21116、21117、21118、21119

查看端口是否被占用（以21115为例），输入：

```
lsof -i:21115  #查看21115端口是否被占用，如果被占用，重新自定义一个端口

```

如果出现：

```
-bash: lsof: command not found

```

运行：

```
apt install lsof  #安装lsof

```

如果端口没有被占用，我们接着可以运行：

```
cd /root/data/docker_data/rustdesk

docker-compose up -d  

```

来源引用

* [【好玩儿的Docker项目】开箱即用！TeamViewer、向日葵的替代品，20分钟自建一个开源远程桌面服务——RustDesk ](https://blog.laoda.de/archives/docker-compose-install-rustdesk)
