> 查询最近的一条信息

```sql
SELECT * FROM table_name ORDER BY create_time DESC LIMIT 1; //limit 1 提高查询效率，避免全表扫描
```

> 查询今天

```sql
#方法一：
SELECT * FROM table_name WHERE DATE_FORMAT( create_time,'%Y-%m-%d') = DATE_FORMAT(NOW(), '%Y-%m-%d');

#方法二：
SELECT * FROM table_name WHERE DATE(create_time) =DATE(NOW());

#方法三：
SELECT * FROM table_name WHERE TO_DAYS(create_time) =TO_DAYS(NOW());
```

* DATE\_FORMAT\(date,format\)函数用于以不同的格式显示日期/时间数据

* date参数是合法的日期。

* format规定日期/时间的输出格式

* NOW\(\)函数返回当前的日期和时间

* TO\_DAYS\(date\)  返回当前日期的毫秒数
* DATE\(date\) 提取日期或日期/时间表达式的日期部分

> 查询昨天

```sql
CURDATE()-1  //参考查询今天的方法 在今天的天数是-1
```

* CURDATE\(\)  返回当前的日期

> 查询一个星期内/一个月内的数据的数据

```sql
SELECT * FROM table_name WHERE DATE_SUB(CURDATE(),INTERVAL 7 DAY/INTERVAL 1 MONTH) <=DATE(create_time) ORDER BY create_time DESC;
```

* DATE\_SUB\(date,INTERVAL expr unit\) 从日期里减去指定的时间间隔

> 返回date的星期索引\(1 = Sunday, 2 = Monday, ... 7 = Saturday\)

```sql
SELECT DAYOFWEEK(create_time) FROM table_name ORDER BY create_time DESC
```

> 给日期添加指定的时间间隔

```sql
SELECT * FROM table_name WHERE DATE_ADD(create_time,INTERVAL 1 DAY) <= DATE(NOW());
```

* DATE\_ADD\(date,INTERVAL expr unit\)  给日期添加指定的时间间隔

> 返回两个日期之间的天数

```sql
SELECT * FROM table_name WHERE DATEDIFF(NOW(),create_time)=0  //0代表查询的是当天,1 查询的就是昨天..
```

* DATEDIFF\(expr1,expr2\) 返回两个日期之间的天数

> **查询本季度数据**

```sql
select * from table_name  where QUARTER(create_time)=QUARTER(NOW());

#查询上季度数据
select * from table_name  where QUARTER(create_time)=QUARTER(NOW())-1;
或者:
select * from table_name   where QUARTER(create_time)=QUARTER(DATE_SUB(NOW(),interval 1 QUARTER));
```

* QUARTER\(date\)    1=1季度\(1-2-3月\)...

> **查询本年数据**

```sql
select * from table_name  where YEAR(create_time)=YEAR(NOW());
#查询上年数据
select * from table_name  where YEAR(create_time)=YEAR(NOW())-1;
或者:
select * from table_name   where YEAR(create_time)=YEAR(date_sub(NOW(),interval 1 YEAR));
```

* YEAR\(date\) 获取日期的年份  MONTH\(date\) 获取日期的月份 Day\(date\) 获取日期的天数  TIME\(NOW\(\)\)获取时间

> **查询当前这周的数据**

```sql
SELECT * FROM table_name   WHERE YEARWEEK(date_format(create_time,'%Y-%m-%d')) = YEARWEEK(NOW());
```

> **查询距离当前现在6个月的数据**

```sql
select * from table_name  where create_time between date_sub(NOW(),interval 6 MONTH) and NOW();
```

* [ ] 日期：CURDATE\(\)= DATE\(NOW\(\)\)

* [ ] 日期+时间：NOW\(\)

* [ ] 时间：CURTIME\(\)=TIME\(NOW\(\)\)


