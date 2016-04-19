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
