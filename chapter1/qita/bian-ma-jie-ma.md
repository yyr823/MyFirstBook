> ### 编码解码

#### **参考文章:**

* #### [编码,解码,乱码,问题详解](https://blog.csdn.net/Marksinoberg/article/details/52254401)\(详情点击\)
* #### [服务器中的编码解码问题](https://blog.csdn.net/qwe5810658/article/details/80297383)

> #### **编码和解码是什么**

用utf-8来举例：

阿伦 → &\#x963F;&\#x4F26; 由左到右的过程,叫编码\(就是把看得懂的内容,转换成看不懂的内容\)

阿伦 ← &\#x963F;&\#x4F26; 由右到左的过程,叫解码\(就是把看不懂的内容,转换成看懂的内容\)

```java
byte[] bytes=  name.getBytes("ISO-8859-1");     //采用ISO方式    编码
name = new String(bytes,"UTF-8");              //采用utf-8方式     解码
```

* 编码和解码的方式必须一样才能避免出现乱码.假如你用utf-8编码,却用gbk来解码,那显示出来就会是乱码

> #### 服务器与浏览器交互时对数据的处理方式\(乱码出现的原因\)

![](/assets/b2.png)

1.浏览器发送数据

html使用的编码格式时utf-8,所以浏览器中输入了某一数据,浏览器会先将这个数据以utf-8作为编码表将它进行编码,然后把编码后的01数据发送到服务器;

2.tomcat服务器的特点

tomcat服务器默认使用的是ISO-8859-1的编码表,因此当服务器接收到浏览器发送的01数据时,服务器会默认使用ISO-8859-1的编码表将其进行解码。

3.英文与标点不会乱码的原因

因此就会出现我们常见的情况:ISO-8859-1与utf-8都是兼容ASCII码,因此从浏览器发送到服务器中属于ASCII码的内容是不会乱码,因为他们编解码都是按照ASCII码;

4.汉字会出现乱码的原因:

ISO-8859-1不支持汉字,即使是GBK这种支持汉字的通过他们编码再使用utf-8编码也是会出现乱码,因为ISO-8859-1不支持汉字,没有汉字对应的编码表,GBK中同一个汉字对应的01代码与utf-8对应的01代码不一致,因为他们单个字符的占的字节数是不同的。

5.例如:用户输入“阿伦”,浏览器采用utf-8将其编码为&\#x963F;&\#x4F26; 然后发给tomcat, tomcat理应用同样的utf-8来解码,但它不管不顾,依旧采用自己ISO的方式来解码,比如解码成了 ^-^ 然后显示出来,这就是所谓的乱码。

程序员的解决办法:先用tomcat的ISO方式解码再将 ^-^ 进行编码,恢复成 &\#x963F;&\#x4F26; 然后再用浏览器的utf-8方式将&\#x963F;&\#x4F26; 解码, 就成功得到了 “阿伦”;

`整个流程:“阿伦” (用户)→ &#x963F;&#x4F26;(浏览器) → ^-^ (tomcat)→ &#x963F;&#x4F26;(程序员) → 阿伦(浏览器)`

> #### 如何防止乱码

* [x] **数据库**

**修改字符集设置\(MySql\)**:可以先输入查询语句SHOW VARIABLES LIKE ‘character\_set\_%’;查看所有的编码是否是UTF-8.

如果不是,可以使用Server Instance Config 把默认的字符集设置为utf-8或者修改/MySQL/MySQL Server 5.0/my.ini中的default-character-set=gbk,character-set-server=gbk改成utf-8;然后重新启动mysql的服务;

* [x] **JSP乱码**

* 在jsp页面里加上:

```jsp
<%@page pageEncoding="UTF-8" contentType="text/html; charset=UTF-8" %>
```

* 或者使用HTML标签来声明

```
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
```

* 借用工具

![](/assets/b1.png)

* [x] **数据库连接语句**

设置characterencoding为UTF-8:

```java
jdbc.mysql.url=jdbc:mysql://localhost:3306/db?useUnicode=true&amp;characterEncoding=UTF8
```

* [x] **Tomcat方面**

为了保证get/post数据都采用相同的UTF8编码,在server.xml中进行如下设置:

```java
<Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000"redirectPort="8443" URIEncoding="UTF-8" />
```

* [x] **使用过滤器Filter**

**有些时候,使用过滤器可以一劳永逸的解决乱码问题,原理就是强化了通信双方的编码一致性**

```java
//在doFilter方法中添加这样的代码
HttpServletRequest request = (HttpServletRequest )req;
HttpServletResponse response = (HttpServletResponse )resp;
request.setCharacterEncoding("UTF-8");
response.setHeader("Content-Type:text/htmlcharset=UTF-8");
response.setCharacterEncoding("UTF-8");
//放行
chain.doFilter(request,response);
```



