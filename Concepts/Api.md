1.应用程序接口
```
应用层的应用程序接口有很多，并且发展很快，比较常见的如socket、FTP、HTTP以及telnet。这些接口从大类上可分为四类：
远程过程调用（RPC，Remote Procedure Call Protocol）
数据查询接口
文件类接口
数据通信接口
例如FTP协议就是文件类接口，基于FTP，用户可以实现文件在网络间的共享和传输。而socket和HTTP可归结为数据通信接口，基于这两种接口，用户可以开发网络通信应用程序，以及web页面交互程序。当然如果从编程开发角度看，无论是FTP、HTTP还是telnet，都是基于socket接口开发出来的应用层协议，是对socket接口的进一步封装和抽象，从而为用户提供更高一层的服务和接口。
socket有时称之为“Berkeley Socket”，它是最早由伯克利开发的应用程序接口。常用的socket类型有两种：流式socket（SOCK_STREAM）和数据报式socket（SOCK_DGRAM）。
流式socket是一种面向连接的socket，针对于面向连接的TCP服务应用。
数据报式socket是一种无连接的socket，对应于无连接的UDP服务应用。
从用户接口意义上讲，还有传输层的TLI接口，是由AT&T开发的，有时也称作XTI。它是传输层为用户提供的应用程序接口，可以用来在传输层进行应用开发。 [3]
```
