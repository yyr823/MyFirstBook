> #### HTTP 简介

* HTTP协议是Hyper Text Transfer Protocol\(超文本传输协议\)的缩写,是用于从万维网\(WWW:World Wide Web \)服务器传输超文本到本地浏览器的传送协议。

* HTTP是一个基于TCP/IP通信协议来传递数据\(HTML 文件, 图片文件, 查询结果等\)

> #### HTTP 工作原理

* [x] **HTTP协议工作于客户端-服务端架构上。浏览器作为HTTP客户端通过URL向HTTP服务端即WEB服务器发送所有请求**。

* [x] Web服务器有:Apache服务器,IIS服务器\(Internet Information Services\)等。

* [x] Web服务器根据接收到的请求后,向客户端发送响应信息。

* [x] HTTP默认端口号为80,但是你也可以改为8080或者其他端口。

**HTTP三点注意事项：**

* **HTTP是无连接:**无连接的含义是限制每次连接只处理一个请求。服务器处理完客户的请求,并收到客户的应答后,即断开连接。采用这种方式可以节省传输时间。
* **HTTP是媒体独立的:**这意味着,只要客户端和服务器知道如何处理的数据内容,任何类型的数据都可以通过HTTP发送。客户端以及服务器指定使用适合的MIME-type内容类型。
* **HTTP是无状态:**HTTP协议是无状态协议。无状态是指协议对于事务处理没有记忆能力。缺少状态意味着如果后续处理需要前面的信息,则它必须重传。这样可能导致每次连接传送的数据量增大。另一方面,在服务器不需要先前信息时它的应答就较快。

**以下图表展示了HTTP协议通信流程:**

![](https://www.runoob.com/wp-content/uploads/2013/11/cgiarch.gif "cgiarch")

> **CGI\(Common Gateway Interface\) **是 HTTP 服务器与你的或其它机器上的程序进行**“交谈”**的一种工具,其程序须运行在网络服务器上。绝大多数的 CGI 程序被用来解释处理来自表单的输入信息,并在服务器产生相应的处理，或将相应的信息反馈给浏览器。CGI 程序使网页具有**交互功能**。

> #### HTTP 消息结构

* **HTTP是基于客户端/服务端（C/S）的架构模型,通过一个可靠的链接来交换信息,是一个无状态的请求/响应协议**。

* 一个HTTP"客户端"是一个应用程序\(Web浏览器或其他任何客户端\),通过连接到服务器达到向服务器**发送一个或多个**HTTP的请求的目的。

* 一个HTTP"服务器"同样也是一个**应用程序**\(通常是一个Web服务,如Apache Web服务器或IIS服务器等\),通过接收客户端的请求并向客户端发送HTTP响应数据。

* HTTP使用**统一资源标识符**\(Uniform Resource Identifiers, URI\)来传输数据和建立连接。一旦建立连接后,数据消息就通过类似Internet邮件所使用的格式\[RFC5322\]和多用途Internet邮件扩展（MIME）\[RFC2045\]来传送。
* HTTP 协议的 8 种请求类型介绍：HTTP 协议中共定义了八种方法或者叫“动作”来表明对 Request-URI 指定的资源的不同操作方式,具体介绍如下：

  * OPTIONS
    返回服务器针对特定资源所支持的HTTP请求方法。也可以利用向Web服务器发送'\*'的请求来测试服务器的功能性。
  * HEAD
    向服务器索要与GET请求相一致的响应,只不过响应体将不会被返回。这一方法可以在不必传输整个响应内容的情况下,就可以获取包含在响应消息头中的元信息。
  * GET
    向特定的资源发出请求。
  * POST
    向指定资源提交数据进行处理请求\(例如提交表单或者上传文件\)。数据被包含在请求体中。POST请求可能会导致新的资源的创建和/或已有资源的修改。
  * PUT
    向指定资源位置上传其最新内容。
  * DELETE
    请求服务器删除 Request-URI 所标识的资源。
  * TRACE
    回显服务器收到的请求,主要用于测试或诊断。
  * CONNECT
    HTTP/1.1 协议中预留给能够将连接改为管道方式的代理服务器。

  `虽然HTTP的请求方式有8种,但是我们在实际应用中常用的也就是`**`get`**`和`**`post,`**`其他请求方式也都可以通过这两种方式间接的来实现。`

* [x] **客户端请求消息**

客户端发送一个HTTP请求到服务器的请求消息包括以下格式:**请求行\(request line\)、请求头部\(header\)、空行和请求数据**四个部分组成,下图给出了请求报文的一般格式。

![](/assets/2012072810301161.png)

* [x] **服务器响应消息**

HTTP响应也由四个部分组成,分别是:**状态行、消息报头、空行和响应正文**。

![](/assets/h1.png)

* [x] 下面实例是一点典型的使用GET来传递数据的实例：

* **客户端请求:**

```
GET /hello.txt HTTP/1.1
User-Agent: curl/7.16.3 libcurl/7.16.3 OpenSSL/0.9.7l zlib/1.2.3
Host: www.example.com
Accept-Language: en, mi
```

* **服务端响应:**

```
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
ETag: "34aa387-d-1568eb00"
Accept-Ranges: bytes
Content-Length: 51
Vary: Accept-Encoding
Content-Type: text/plain
```

* **输出结果:**

```
Hello World! My payload includes a trailing CRLF.
```



