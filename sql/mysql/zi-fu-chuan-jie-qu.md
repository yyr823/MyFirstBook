### MySQL 字符串函数：字符串截取

* #### [原文链接](https://www.cnblogs.com/duanc/archive/2018/04/09/8760372.html)
* left\(name,4\)截取左边的4个字符

```Sql
SELECT LEFT(201809,4) 年   -- 2018
```

* right\(name,2\)截取右边的2个字符

```Sql
SELECT RIGHT(201809,2) 月份 -- 09
```

* SUBSTRING\(name,5,3\) 截取name这个字段从第五个字符开始,只截取之后的3个字符

```Sql
SELECT SUBSTRING('成都融资事业部',5,3)  -- 事业部
```

* SUBSTRING\(name,3\) 截取name这个字段从第三个字符开始,之后的所有的字符

```Sql
SELECT SUBSTRING('成都融资事业部',3) -- 融资事业部
```

* SUBSTRING\(name, -4\) 截取name这个字段的第 4 个字符位置（倒数）开始取，直到结束

```Sql
SELECT SUBSTRING('成都融资事业部',-4) -- 资事业部
```

* SUBSTRING\(name, -4，2\) 截取name这个字段的第 4 个字符位置（倒数）开始取，只截取之后的2个字符

```Sql
SELECT SUBSTRING('成都融资事业部',-4,2) -- 资事
```

**注意:我们注意到在函数 **`substring(str,pos, len)`**中,pos 可以是负值,但 len 不能取负值。**

* substring\_index\('www.baidu.com', '.', 2\) 截取第二个 '.' 之前的所有字符

```Sql
SELECT substring_index('www.baidu.com', '.', 2) -- www.baidu
```

* substring\_index\('www.baidu.com', '.', -2\) 截取第二个 '.' （倒数）之后的所有字符

```
SELECT substring_index('www.baidu.com', '.', -2) -- baidu.com
```

* SUBSTR\(name, 1, CHAR\_LENGTH\(name\)-3\) 截取name字段,取除name字段后三位的所有字符

```Sql
SELECT SUBSTR('成都融资事业部', 1, CHAR_LENGTH('成都融资事业部')-3)  -- 成都融资
```



