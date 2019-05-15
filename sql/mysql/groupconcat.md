### 根据某个字段将多条记录的某个字段拼接成一个字段

![](/assets/1.png)![](/assets/2.png)

![](/assets/3.png)

SQL代码：\(注意：_**group by**_ 进行分组\)

```
SELECT NAME,GROUP_CONCAT(r.roleName)roleName FROM users u 
JOIN user_role ur ON u.id=ur.uid JOIN role r ON ur.rid=r.id  GROUP BY u.id
```

查询效果：

![](/assets/4.png)

