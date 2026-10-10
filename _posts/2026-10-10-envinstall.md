---
layout: post
title: 语言环境安装
date: 2026-10-10 10:00:00 +0800
categories: [技术杂谈]
tags: [博客, 开始, 记录]
description: 技术博客：语言环境安装。
keywords: 博客, 朱名斐, 开始
---

## 1、Python

1.  官网：https://www.python.org/
2.  下载页面：https://www.python.org/downloads/

```bash
# 安装版本：3.13.15
# 发布时间：2026年8月5日
# 安装方式：编译安装

# 安装依赖包、指定OpenSSL库的头文件和链接库路径
# apt install -y build-essential libssl-dev zlib1g-dev libncurses5-dev libsqlite3-dev libreadline-dev libbz2-dev libffi-dev liblzma-dev tk-dev
$ yum -y install gcc gcc-c++ make zlib* bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel xz-devel libffi-devel openssl-devel openssl11 openssl11-devel
$ export CFLAGS=$(pkg-config --cflags openssl11)
$ export LDFLAGS=$(pkg-config --libs openssl11)

# 编译安装Python
$ wget https://www.python.org/ftp/python/3.13.15/Python-3.13.15.tar.xz
$ tar xf Python-3.13.15.tar.xz && cd Python-3.13.15
$ ./configure --enable-shared --prefix=/usr/local/python3 --with-ssl
$ make -j 5 && make install

$ cat > /etc/profile.d/python3.sh <<'EOF'
export PATH=${PATH}:/usr/local/python3/bin
EOF
$ source /etc/profile
# 会报错,需要配置共享库文件
$ python3
python3: error while loading shared libraries: libpython3.11.so.1.0: cannot open shared object file: No such file or directory

$ echo '/usr/local/python3/lib' >> /etc/ld.so.conf.d/python3.conf
$ ldconfig

# 配置pip使用国内阿里云源
$ python3 -m pip config set global.index-url https://mirrors.aliyun.com/pypi/simple
# 升级pip版本
$ python3 -m pip install --upgrade pip
```

```bash
# docker镜像
$ docker pull python:3.13.15
$ docker pull python:3.13.15-alpine
```



## 2、Golang

1.  官网：https://go.dev/
2.  下载页面：https://go.dev/dl/

```bash
# 安装版本：1.26.5
# 发布时间：2026年7月7日
# 安装方式：二进制安装
$ wget https://go.dev/dl/go1.26.5.linux-amd64.tar.gz
$ tar xf go1.26.5.linux-amd64.tar.gz -C /usr/local/
$ cat > /etc/profile.d/golang.sh <<'EOF'
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
EOF

$ source /etc/profile
$ go version
go version go1.26.5 linux/amd64

# 设置国内源
https://goproxy.cn
https://goproxy.io
https://goproxy.me

# 环境变量方式
$ go env -w GOPROXY=https://goproxy.cn,direct
```

```bash
# docker镜像
$ docker pull golang:1.26.5
$ docker pull golang:1.26.5-alpine
```



## 3、Java

1.  官网（Oracle）：https://www.oracle.com/java/
2.  下载页面（Oracle需要登录）：https://www.oracle.com/cn/java/technologies/downloads/archive/

```bash
# 安装版本：8u491
# 发布时间：2026年4月21日
# 安装方式：二进制安装
# https://www.oracle.com/cn/java/technologies/javase/javase8u211-later-archive-downloads.html#license-lightbox
$ tar xf jdk-8u491-linux-x64.tar.gz -C /usr/local/
$ ln -s /usr/local/jdk1.8.0_491 /usr/local/java
$ cat > /etc/profile.d/java.sh <<'EOF'
export JAVA_HOME=/usr/local/java
export PATH=$PATH:$JAVA_HOME/bin
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tool.jar
EOF

$ java -version
java version "1.8.0_491"
Java(TM) SE Runtime Environment (build 1.8.0_491-b10)
Java HotSpot(TM) 64-Bit Server VM (build 25.491-b10, mixed mode)
```

```bash
# docker镜像
# OpenJdk
$ docker pull openjdk:8u342					# 不推荐,因为已停更
$ docker pull amazoncorretto:8u492			# 亚马逊云维护
$ docker pull amazoncorretto:8u492-alpine

# OracleJdk（需要登录并且勾选同意协议）
$ docker pull container-registry.oracle.com/java/jdk:8u491
```



## 4、Nodejs

1.  官网：https://nodejs.org/zh-cn
2.  下载页面：https://nodejs.org/zh-cn/download

```bash
# 安装版本：v16.20.2
# 发布时间：2023年8月10日
# 安装方式：二进制安装
$ wget https://nodejs.org/dist/v16.20.2/node-v16.20.2-linux-x64.tar.xz
$ tar xf node-v16.20.2-linux-x64.tar.xz -C /usr/local/
$ ln -s /usr/local/node-v16.20.2-linux-x64 /usr/local/nodejs
$ cat > /etc/profile.d/nodejs.sh <<'EOF'
export PATH=/usr/local/nodejs/bin:$PATH
EOF
$ source /etc/profile
$ node --version
v16.20.2

# npm设置阿里云源
$ npm config set registry http://registry.npmmirror.com
```

```bash
# docker镜像
$ docker pull node:16.20.2
$ docker pull node:16.20.2-alpine
```

