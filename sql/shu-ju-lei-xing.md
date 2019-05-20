| ** 数据类型     **        |
| :---: |


| 数据类型 | 字节长度 | 范围或用法 |
| :---: | :---: | :---: |
| bigint | 8 | 无符号\[0,2^64-1\]，有符号\[-2^63 ,2^63 -1\] |
| binary\(M\) | M | 类似Char的二进制存储，只包含byte串而非字符串，它们没有字符集的概念，排序和比较操作都是基于字节的数字值 |
| bit | 1 | 无符号\[0,255\]，有符号\[-128,127\] |
| blob | Max:64K | 二进制的对象，大小写敏感 |
| char\(M\) |  M | 定长字符串 |
| date | 3 | 以YYYY-MM-DD的格式显示，比如：2009-07-19 |
| datetime | 8 | 以YYYY-MM-DD HH:MM:SS的格式显示，比如：2009-07-19 11：22：30 |
| decimal\(M,D\) | M+1或M+2 | 存储精确的数值 |
| double\(M,D\) | 8 | 双精度浮点 |
| enum | 1或2  | 最大可达65535个不同的枚举值，单选字符串数据类型，适合存储表单界面中的“单选值” |
| float\(M,D\) | 4  | 单精度浮点数 |
| geometry |  | 存储空间点数据 |
| geometrycollection |  | geometry集合类 |
| int | 4 | 无符号\[0,2^32-1\]，有符号\[-2^31,2^31-1\]  |
| integer | 4  | 无符号\[0,2^32-1\]，有符号\[-2^31,2^31-1\]  |
| json |  | json格式数据 |
| linestring |  | 点之间的线性插值曲线 |
| longblob | Max:4G  | 大小写敏感  |
| longtext | Max:4G | 大小写不敏感 |
| mediumblob | Max:16M | 大小写敏感 |
| mediumint | 3 | 无符号\[0,2^24-1\]，有符号\[-2^23,2^23-1\] |
| mediumtext | Max:16M | 大小写不敏感 |
| multilinestring |  | 点之间的线性插值曲线的集合  |
| multipoint |  | 点的集合  |
| multipolygon |  | 多边形的集合  |
| numeric\(M,D\) | M+1或M+2 | 精确存储数值，同decimal |
| point |  | 二维空间中的点  |
| polygon |  | 多边形  |
| real\(M,D\) |  | 浮点数，REAL就是DOUBLE ，如果SQL服务器模式包括REAL\_AS\_FLOAT选项，REAL是FLOAT的同义词而不是DOUBLE的同义词  |
| set |  | 多选字符串数据类型，适合存储表单界面的“多选值”insert into enum\_set\_table\(id,gender,hobby\) values\(null,'F','music,movie,footbal'\);  |
| smallint | 2  | 无符号\[0,65535\]，有符号\[-32768,32767\]  |
| text | Max:64K  | 大小写不敏感  |
| time | 3  | 以HH:MM:SS的格式显示。比如：11：22：30  |
| timestamp | 4  | 以YYYY-MM-DD的格式显示，比如：2009-07-19  |
| tinyblob | Max:255  | 大小写敏感  |
| tinyint | 1  | 整数\[0,255\]  |
| tinytext | Max:255  | 大小写不敏感  |
| varbinary\(M\) | M  | 类似varchar的变长二进制存储  |
| varchar\(M\) | M  | 变长字符串，MySQL要求一个行定义长度不能超过65535个字节，不包括text、blob等大字段类型，varchar长度受此长度限制，和其他非大字段加起来不能超过65535个字节。字符类型若为gbk，每个字符占用2个字节，字符类型若为utf8，每个字符最多占用3个字节。 |
| year | 1  | 以YYYY的格式显示。比如：2009  |



