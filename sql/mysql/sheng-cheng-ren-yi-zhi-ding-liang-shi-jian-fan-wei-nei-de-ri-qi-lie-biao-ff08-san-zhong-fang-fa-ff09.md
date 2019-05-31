### Mysql生成任意指定两时间范围内的日期列表（三种方法）

> #### 原文链接

* ##### [Mysql生成任意指定两时间范围内的日期列表（三种方法）](https://blog.csdn.net/Dai_Aixy/article/details/83144619)
* ##### [mysql 给定起止日期获取之间的连续日期](https://blog.csdn.net/boenwan/article/details/76268739)

> #### 创建一个临时的日历表

    DELIMITER $$
    DROP PROCEDURE IF EXISTS create_calendar $$
    CREATE PROCEDURE create_calendar (s_date DATE, e_date DATE)
    BEGIN
        SET @createSql = 'CREATE TABLE IF NOT EXISTS calendar (
                          `date` date NOT NULL,
                   UNIQUE KEY `unique_date` (`date`) USING BTREE
                       )ENGINE=InnoDB DEFAULT CHARSET=utf8'; 
        prepare stmt from @createSql; 
        execute stmt; 

        WHILE s_date <= e_date DO
            INSERT IGNORE INTO calendar VALUES (DATE(s_date)) ;
            SET s_date = s_date + INTERVAL 1 DAY ;
        END WHILE ; 

    END$$
    DELIMITER ;
    CALL create_calendar ('2018-03-01', '2018-12-30');

**总结:生成一张临时表,里面存放着你自己指定的时间范围内的所有日期。生成临时表，根据自己业务需求与数据进行各种操作得出某段时间范围内日期齐全的数据。**

> #### \(变量控制\)指定数据条数,生成连续的数字或日期

```Sql
SELECT DATE_FORMAT(DATE_SUB(NOW(), INTERVAL xc MONTH), '%Y-%m') as date
FROM ( 
            SELECT @xi:=@xi+1 as xc from 
            (SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5) xc1, 
            (SELECT 1 UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5) xc2,  
            (SELECT @xi:=0) xc0 
) xcxc
```

![](/assets/sq1.png)**总结：在如上的例子当中,涉及到的知识点是变量,DATE\_SUB\(\),DATE\_FORMAT\(\).使用以上方法的好处就是不用创建存储过程，也不涉及到任何表。缺点就是数据的条数控制并不灵活,不能和用户之间形成互动,即不能自定义日期区间,只能控制数据条数。**

> #### 利用数据量大的表做操作

* [x] 创建一个数字辅助表

```Sql
CREATE TABLE `manhour_record` (
  `key` int(11) NOT NULL,
  PRIMARY KEY (`key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='数字辅助表';
```

* [x] 创建一个存储过程为数字辅助表增加数据

```Sql
DELIMITER $$
CREATE DEFINER=`root`@`%` PROCEDURE `create_nums`(cnt int unsigned)
BEGIN
declare s int unsigned default 1;
    truncate table manhour_record;
    insert into manhour_recordselect s;
    while s*2<=cnt do
        begin
            insert into nums select `key`+s from manhour_record;
            set s=s*2;
        end;
    end while;
END$$
DELIMITER ;
```

* [x] 执行存储过程，增加1-50000进入数字辅助表

```Sql
call create_nums(50000);
```

* [x] 代码编写

![](/assets/sq2.png)

> #### oracle 求两个日期之间的所有日期

```Sql
SELECT TO_CHAR((TO_DATE('2019-05-28', 'yyyy-MM-dd') + (ROWNUM - 1)), 'yyyy-MM-dd') DT
  FROM DUAL
CONNECT BY ROWNUM <=
           (TO_DATE('2019-05-31', 'yyyy-MM-dd') - TO_DATE('2019-05-28', 'yyyy-MM-dd') + 1);
```



