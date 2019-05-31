### Java去除字符串中的空格

* #### [原文链接](https://www.cnblogs.com/LiuChunfu/p/5661810.html)

```java
 String str=" Hello  World ! ";
 str=str.trim()  //trim()是去掉首尾空格
 str=str.replace(" ", ""); //去掉所有空格,包括首尾-中间
 str=str.replaceAll(" ",""); //去掉所有空格 
 str=str.replaceAll("\\s*", ""); //可以替换大部分空白字符， 不限于空格 \s可以匹配空格、制表符、换页符等空白字符的其中任意一个 
 System.out.println(str);
```



  


  


  




