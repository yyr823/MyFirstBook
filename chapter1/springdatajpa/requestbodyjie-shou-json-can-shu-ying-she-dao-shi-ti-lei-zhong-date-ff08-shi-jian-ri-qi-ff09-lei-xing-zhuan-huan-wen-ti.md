### @requestbody接收json参数 映射到 实体类中 Date（时间日期）类型转换问题

1. 场景：前台ajax提交, 后台@requestbody接收json参数 映射到 实体类中 Date（时间日期）类型转换
2. 解决方案：

   JsonFormat ：出参     DateTimeFormate ： 入参

```
@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss")
@JsonFormat(pattern = "yyyy-MM-dd HH:mm:ss", timezone = "GMT+8")
private Date startTime;
```

1. [x] pattern 指定转化的格式
2. [x] locale  主要指语言，如果中文的话，月份输出是五月，但是英文就是May
3. [x] timezone主要解决“8小时”问题\(时区问题\)

