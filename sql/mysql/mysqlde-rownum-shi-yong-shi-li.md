### Mysql的Rownum使用示例

* #### [原文链接](https://blog.csdn.net/a80c51/article/details/80531291)

* ####  显示当前查询结果的行号

```Sql
SELECT  @rownum := @rownum +1 AS rownum,e.* FROM (SELECT @rownum := 0) r,employee e 
```

#### ![](/assets/s1.png)

#### 



