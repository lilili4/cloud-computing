## 安装Apache Web服务器

<u>dockerfile:</u>

`#Comment`

`FROM centos:7`
`#`
`RUN yum install sudo -y`
`#安装Apache Web服务器`
`RUN yum install httpd -y`

`ADD start.sh /root`
`RUN chmod 777 /root/start.sh`
`#暴露端口`
`EXPOSE  80`

`CMD sh /root/start.sh`

<u>start.sh</u>

`#!/bin/sh`
`systemctl start httpd.service`
`touch /root/test.c`

将这两个文件放到同一个文件夹下面：

构建镜像：

`docker build -t mycentos:test1 .`

运行镜像：

`ocker run -tid --privileged=true --name test1 -p 8884:80 -d mycentos:test1 /usr/sbin/init`

![1](./images/实验3/19.png)

访问web(端口号为8884):

http://106.54.102.51:8884/

![1](./images/实验3/20.png)

