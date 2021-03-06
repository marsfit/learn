# 从输入URL到页面渲染完成的整个过程

## 几个概念

在介绍整个流程之前，先解释一下可能会出现的常用的概念。

- http

  > http是基于TCP/IP，用于从万维网服务器传输超文本到本地浏览器的传送协议。默认端口号是80。 http是无连接的，即每次传输只处理一个请求服务器处理完客户的请求，并收到客户的应答后就断开连接。

- DNS

  > DNS，即域名解析服务器

- TCP

  > 需要了解的是TCP建立连接的三次握手。

简单点说，A与B建立TCP连接时：首先A向B发SYN（同步请求），然后B回复SYN+ACK（同步请求应答），最后A回复ACK确认，这样TCP的一次连接（三次握手）的过程就建立了！

## 整个过程

1. 域名解析、DNS服务器

  根据URL地址，通过域名解析，获取服务器的ip地址。获取ip地址有以下几个过程：

  - 查找浏览器自身的DNS缓存，若无，则进入下一步。
  - 读取操作系统自身的DNS缓存，若无，则进入下一步。
  - 读取本地HOST文件。
  - 最后发起一个DNS的系统调用，通过迭代DNS解析请求一级一级拿到目标地址的ip。
  - TCP建立连接，

2. 客户端与服务器通过三次握手建立稳定的TCP连接。

3. 客户端发起请求

  http请求方法大致分为：GET、POST、HEAD、OPTIONS、PUT、DELETE、TRACE、CONNECT。

  http请求消息包括：请求行（request line）、请求头（request head）、空行和请求数据四个部分组成。

4. 服务器响应请求

  响应消息包括：状态行、消息报头、空行和响应正文。

  http常见状态码：

  - 200：请求成功；
  - 301：请求的资源被永久转移到其他地方(重定向)；
  - 404：请求的资源不存在；
  - 500：服务器内部错误。

  http状态码分类：

  - 1开头：信息，服务器已经收到请求，需要请求者继续执行操作；
  - 2开头：成功，操作被成功接收并处理；
  - 3开头：重定向；
  - 4开头：客户端错误；
  - 5开头：服务器错误。

5. 客户端解析数据和渲染页面。
