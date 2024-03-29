## socket简介

### 1. 不同电脑上的进程之间如何通信

首要解决的问题是如何唯一标识一个进程，否则通信无从谈起！

在1台电脑上可以通过进程号（PID）来唯一标识一个进程，但是在网络中这是行不通的。

其实TCP/IP协议族已经帮我们解决了这个问题，网络层的“ip地址”可以唯一标识网络中的主机，而传输层的“协议+端口”可以唯一标识主机中的应用进程（进程）。

这样利用ip地址，协议，端口就可以标识网络的进程了，网络中的进程通信就可以利用这个标志与其它进程进行交互

##### 注意：

> - 所谓`进程`指的是：运行的程序以及运行时用到的资源这个整体称之为进程（在讲解多任务编程时进行详细讲解）
> - 所谓`进程间通信`指的是：运行的程序之间的数据共享
> - 后面课程中会详细说到，像网络层等知识，不要着急

### 2. 什么是socket

socket(简称 `套接字`) 是进程间通信的一种方式，它与其他进程间通信的一个主要不同是：

它能实现不同主机间的进程间通信，我们网络上各种各样的服务大多都是基于 Socket 来完成通信的

例如我们每天浏览网页、QQ 聊天、收发 email 等等

![img](../Images/04day/5B1ZLMH51VK5_55.png)

![img](../Images/04day/20101130174614758.gif)

![img](../Images/04day/e89a8ffb13931691b73d16.png)

### 3. 创建socket

在 Python 中 使用socket 模块的函数 socket 就可以完成：

```python
import socket
socket.socket(AddressFamily, Type)
```

#### 说明：

函数 socket.socket 创建一个 socket，该函数带有两个参数：

- Address Family：可以选择 AF_INET（用于 Internet 进程间通信） 或者 AF_UNIX（用于同一台机器进程间通信）,实际工作中常用AF_INET
- Type：套接字类型，可以是 SOCK_STREAM（流式套接字，主要用于 TCP 协议）或者 SOCK_DGRAM（数据报套接字，主要用于 UDP 协议）

创建一个tcp socket（tcp套接字）

```python
import socket

# 创建tcp的套接字
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# ...这里是使用套接字的功能（省略）...

# 不用的时候，关闭套接字
s.close()
```

创建一个udp socket（udp套接字）

```python
import socket

# 创建udp的套接字
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

# ...这里是使用套接字的功能（省略）...

# 不用的时候，关闭套接字
s.close()
```

##### 说明

- 套接字使用流程 与 文件的使用流程很类似
    1. 创建套接字
    2. 使用套接字收/发数据
    3. 关闭套接字