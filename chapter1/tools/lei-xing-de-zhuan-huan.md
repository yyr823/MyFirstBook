> ### 字符串转化为整形、浮点类型

```java
 String s = "100";
 //方法一
 int   a = Integer.parseInt(String s);
 long  b=  Long.parseLong(String s);
 float c=  Float.parseFloat(String s);
 double d= Double.parseDouble(String s) 
 //方法二
 int   a  = Integer.valueOf(s).intValue();   
 float c  = Float.valueOf(s).floatValue();
```

* Integer.parseInt\(String s\)生成的是一个整形

* Integer.valueOf\(s\).intValue\(\)生成的是一个对象\(图示代码[**自动拆箱**](https://blog.csdn.net/qq_33591903/article/details/84259105)为基本数据类型\)

> ### 整形、浮点类型转化为字符串

```java
int i=11;
float b=2.5f;
     //方法一
    String s=i+"";
    //方法二
    String s=String.valueOf(i);
    //方法三
    String s=Integer.toString(i);
    String s2=Float.toString(b);
```



