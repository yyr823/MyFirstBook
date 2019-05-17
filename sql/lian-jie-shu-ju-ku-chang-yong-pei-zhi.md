* **数据库连接字符编码**

```java
url ="jdbc:mysql://localhost:3306/test?useUnicode=true&characterEncoding=UTF-8"
```

* java.sql.SQLException: Value   '0000-00-00 '异常解决方法

\(原因:数据库查询的timestamp时间字段数据内容为0000-00-00,Java实体类Date映射不成功,默认是抛出异常,所以直接赋值为null\)

```java
url="jdbc:mysql://localhost:3306/test?zeroDateTimeBehavior=convertToNull"
```



