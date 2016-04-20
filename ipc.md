
## 深刻理解Linux进程间通信（IPC）##
https://www.ibm.com/developerworks/cn/linux/l-ipc/
linux下的进程通信手段基本上是从Unix平台上的进程通信手段继承而来的。而对Unix发展做出重大贡献的两大主力AT&T的贝尔实验室及BSD（加州大学伯克利分校的伯克利软件发布中心）在进程间通信方面的侧重点有所不同。前者对Unix早期的进程间通信手段进行了系统的改进和扩充，形成了“system V IPC”，通信进程局限在单个计算机内；后者则跳过了该限制，形成了基于套接口（socket）的进程间通信机制。Linux则把两者继承了下来其中，最初Unix IPC包括：管道、FIFO、信号；System V IPC包括：System V消息队列、System V信号灯、System V共享内存区；Posix IPC包括：	Posix消息队列、Posix信号灯、Posix共享内存区。有两点需要简单说明一下：1）由于Unix版本的多样性，电子电气工程协会（IEEE）开发了一个独立的Unix标准，这个新的ANSI Unix标准被称为计算机环境的可移植性操作系统界面（POSIX）。现有大部分Unix和流行版本都是遵循POSIX标准的，而Linux从一开始就遵循POSIX标准；2）BSD并不是没有涉足单机内的进程间通信（socket本身就可以用于单机内的进程间通信）。事实上，很多Unix版本的单机IPC留有BSD的痕迹，如4.4BSD支持的匿名内存映射、4.3+BSD对可靠信号语义的实现等等。
图一给出了linux 所支持的各种IPC手段，在本文接下来的讨论中，为了避免概念上的混淆，在尽可能少提及Unix的各个版本的情况下，所有问题的讨论最终都会归结到Linux环境下的进程间通信上来。并且，对于Linux所支持通信手段的不同实现版本（如对于共享内存来说，有Posix共享内存区以及System V共享内存区两个实现版本），将主要介绍Posix API。

## system v && bsd ##
https://danielmiessler.com/blog/the-differences-between-bsd-and-system-v-unix/

## pipe ##
http://stackoverflow.com/questions/9029174/af-unix-equivalent-for-windows
The big difference is that the handle the waits a connection is the same that does communications to a client. I would have to create a new named pipe for the server to wait for the next client.

References:
http://msdn.microsoft.com/en-us/library/windows/desktop/aa365799%28v=vs.85%29.aspx
http://msdn.microsoft.com/en-us/library/windows/desktop/aa365588%28v=vs.85%29.aspx
http://msdn.microsoft.com/en-us/library/windows/desktop/aa365603%28v=vs.85%29.aspx

## Unix域套接字 ##
Unix domain socket 或者 IPC socket是一种终端，可以使同一台操作系统上的两个或多个进程进行数据通信。与管道相比，Unix domain sockets 既可以使用字节流，又可以使用数据队列，而管道通信则只能使用字节流。Unix domain sockets的接口和Internet socket很像，但它不使用网络底层协议来通信。Unix domain socket 的功能是POSIX操作系统里的一种组件。

Unix domain sockets 使用系统文件的地址来作为自己的身份。它可以被系统进程引用。所以两个进程可以同时打开一个Unix domain sockets来进行通信。不过这种通信方式是发生在系统内核里而不会在网络里传播。

## referto ##
Unix域套接字 https://zh.wikipedia.org/wiki/Unix%E5%9F%9F%E5%A5%97%E6%8E%A5%E5%AD%97
http://www.thomasstover.com/uds.html
UNIX Domain Socket IPC http://akaedu.github.io/book/ch37s04.html
Linux C编程一站式学习 https://akaedu.github.io/book/index.html
