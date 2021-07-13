---
title: ssh连接远程服务器
author: Jianghe
top: true
hide: false
mathjax: false
toc: true
date: 2021-07-05 20:49:45
img:
summary: ssh 断连
categories: Linux
tags: 
	- ssh
keywords:
---
## ssh 连接后长时间不操作自动断开
这个问题烦得很，隔一小会儿不操作，就卡死了，只能重新连接。

## 解决方法

### 1.修改服务器端参数

修改服务器端配置文件：`/etc/ssh/sshd_config`，添加如下内容：

```shell
# 每 60 秒向客户端发送一次保持连接的信号
ClientAliveInterval    60

# 设置断开时间,客户端 60 次未响应就断开连接（可选）
ClientAliveCountMax    60
```

### 2.修改本地参数

修改本地配置文件：`/etc/ssh/ssh_config` :

```shell
# 每 60 秒向服务器端发送一次保持连接的信号
ServerAliveInterval    60
# 60 次为响应则断开连接
ServerAliveCountMax    60
```

### 3.使用 ssh 登录时设置参数

使用`-o` 选项可以设置相应的参数

```shell
$ ssh -o ServerAliveInterval=30 root@123.123.123
```

## 参考

- [1] [Hustcw Blog](https://blog.csdn.net/hustcw98/article/details/79325878)

