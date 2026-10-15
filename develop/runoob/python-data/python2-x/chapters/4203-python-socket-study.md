# Python2.x：Python 网络编程

- 来源：[Python 网络编程](https://www.runoob.com/python/python-socket.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：学习笔记
- 章节序号：4203

## 本章内容

Python 提供了两个级别访问的网络服务：

- 低级别的网络服务支持基本的 Socket，它提供了标准的 BSD Sockets API，可以访问底层操作系统 Socket 接口的全部方法。
- 高级别的网络服务模块 SocketServer， 它提供了服务器中心类，可以简化网络服务器的开发。


## 什么是 Socket?

Socket又称"套接字"，应用程序通常通过"套接字"向网络发出请求或者应答网络请求，使主机间或者一台计算机上的进程间可以通讯。


## socket()函数

Python 中，我们用 socket（）函数来创建套接字，语法格式如下：

```text
socket.socket([family[, type[, proto]]])
```


### 参数

- family: 套接字家族可以使 AF_UNIX 或者 AF_INET。
- type: 套接字类型可以根据是面向连接的还是非连接分为 SOCK_STREAM 或 SOCK_DGRAM。
- protocol: 一般不填默认为 0。


### Socket 对象(内建)方法


## 简单实例


### 服务端

我们使用 socket 模块的 socket 函数来创建一个 socket 对象。socket 对象可以通过调用其他函数来设置一个 socket 服务。

现在我们可以通过调用 bind(hostname, port) 函数来指定服务的 port(端口)。

接着，我们调用 socket 对象的 accept 方法。该方法等待客户端的连接，并返回 connection 对象，表示已连接到客户端。

完整代码如下：


## 实例

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 文件名：server.py

import socket               # 导入 socket 模块

s = socket.socket()         # 创建 socket 对象
host = socket.gethostname() # 获取本地主机名
port = 12345                # 设置端口
s.bind((host, port))        # 绑定端口

s.listen(5)                 # 等待客户端连接
while True:
    c,addr = s.accept()     # 建立客户端连接
    print '连接地址：', addr
    c.send('欢迎访问菜鸟教程！')
    c.close()                # 关闭连接
```


### 客户端

接下来我们写一个简单的客户端实例连接到以上创建的服务。端口号为 12345。

socket.connect(hostname, port ) 方法打开一个 TCP 连接到主机为 hostname 端口为 port 的服务商。连接后我们就可以从服务端获取数据，记住，操作完成后需要关闭连接。

完整代码如下：


## 实例

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 文件名：client.py

import socket               # 导入 socket 模块

s = socket.socket()         # 创建 socket 对象
host = socket.gethostname() # 获取本地主机名
port = 12345                # 设置端口号

s.connect((host, port))
print s.recv(1024)
s.close()
```

现在我们打开两个终端，第一个终端执行 server.py 文件：

```text
$ python server.py
```

第二个终端执行 client.py 文件：

```text
$ python client.py
欢迎访问菜鸟教程！
```

这时我们再打开第一个终端，就会看到有以下信息输出：

```text
连接地址： ('192.168.0.118', 62461)
```


## Python Internet 模块

以下列出了 Python 网络编程的一些重要模块：

更多内容可以参阅官网的 Python Socket Library and Modules。


## 复习重点

- 能说明 `Python 网络编程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
