1. #### [原文链接](https://blog.csdn.net/wujiandao000/article/details/79068100)
2. #### 异常显示：

```
org.apache.catalina.connector.ClientAbortException: java.io.IOException: 您的主机中的软件中止了一个已建立的连接。
	at org.apache.catalina.connector.OutputBuffer.realWriteBytes(OutputBuffer.java:396)
	at org.apache.tomcat.util.buf.ByteChunk.flushBuffer(ByteChunk.java:426)
	at org.apache.catalina.connector.OutputBuffer.doFlush(OutputBuffer.java:345)
	at org.apache.catalina.connector.OutputBuffer.flush(OutputBuffer.java:320)
	at org.apache.catalina.connector.CoyoteOutputStream.flush(CoyoteOutputStream.java:110)
	at com.fasterxml.jackson.core.json.UTF8JsonGenerator.flush(UTF8JsonGenerator.java:1022)
	at com.fasterxml.jackson.databind.ObjectMapper.writeValue(ObjectMapper.java:2376)
	at ······
```

* ##### 原因：

在tomcat中出现这个错误是由于客户端在发送请求后，还没等服务器响应就断开了连接，有可能是因为网络原因，突然网断了，但是如果错误频繁出现的话，可能就是服务端的问题了。

tomcat中配置了一个连接超时时间**`connectionTimeout,`**如果在这个时间之后客户端还未得到服务器端的响应的话,就会**主动断开连接,**这样就会出现上述异常了,tomcat中默认的连接超时时间是20秒,我们一般最好设置为60秒,从而避免后台程序处理时间长导致连接断开

* ##### 解决方法：

可以通过设置tomcat下conf文件夹的server.xml文件，对请求连接数和请求超时时间进行设置。

```
<Connector port="8080" protocol="HTTP/1.1"   
              connectionTimeout="60000"   
              redirectPort="8443" acceptCount="500" maxThreads="400" />  
```

connectionTimeout以毫秒为单位，默认设置为20秒。通过修改该参数，可以修改tomcat的请求超时时间为60秒。

**关于修改最大并发请求连接数，需要修改`maxThreads`和`acceptCount`两个参数。**

其中，maxThreads的介绍如下：

The maximum number of request processing threads to be created by this Connector, which therefore determines the maximum number of simultaneous requests that can be handled. If not specified, this attribute is set to 200. If an executor is associated with this connector, this attribute is ignored as the connector will execute tasks using the executor rather than an internal thread pool.

此连接器要创建的请求处理线程的最大数量，因此决定可以处理的并发请求的最大数量。如果没有指定，则将此属性设置为200。如果执行器与此连接器关联，则忽略此属性，因为连接器将使用执行器而不是内部线程池执行任务。

而acceptCount的介绍为：

The maximum queue length for incoming connection requests when all possible request processing threads are in use. Any requests received when the queue is full will be refused. The default value is 100.

使用所有可能的请求处理线程时传入连接请求的最大队列长度。队列满时接收到的任何请求都将被拒绝。默认值是100。

* 所以两者的默认值分别是200和100，要调整Tomcat的默认最大连接数，可以增加这两个属性的值，并且使acceptCount大于等于maxThreads。

