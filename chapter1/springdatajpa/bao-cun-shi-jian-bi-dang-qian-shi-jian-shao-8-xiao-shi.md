### 保存时间比当前时间少8小时

1. 原因：时区问题

2. 解决方案：

   在连接url增加时区设置参数\(时区GMT+8的设置\)

```
jdbc:mysql://localhost/database?useUnicode=true&characterEncoding=utf-8&serverTimezone=GMT%2b8
```



