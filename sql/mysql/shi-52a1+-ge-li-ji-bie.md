> #### 数据库事务具有ACID这4个特性：

* A：Atomic,原子性,将所有SQL作为原子工作单元执行,要么全部执行,要么全部不执行;
* C：Consistent,一致性,事务完成后,所有数据的状态都是一致的，即A账户只要减去了100,B账户则必定加上了100;
* I：Isolation,隔离性,如果有多个事务并发执行,每个事务作出的修改必须与其他事务隔离;
* D：Duration,持久性,即事务完成后,对数据库数据的修改被持久化存储.

> #### 隔离级别

对于两个并发执行的事务，如果涉及到操作同一条记录的时候，可能会发生问题。因为并发操作会带来数据的不一致性，包括脏读、不可重复读、幻读等。数据库系统提供了隔离级别来让我们有针对性地选择事务的隔离级别，避免数据不一致的问题。

SQL标准定义了4种隔离级别，分别对应可能出现的数据不一致的情况：

| Isolation Level | 脏读（Dirty Read） | 不可重复读（Non Repeatable Read） | 幻读（Phantom Read） |
| :---: | :---: | :---: | :---: |
| Read Uncommitted | Yes | Yes | Yes |
| Read Committed | - | Yes | Yes |
| Repeatable Read | - | - | Yes |
| Serializable | - | - | - |

* Read Uncommitted是隔离级别最低的一种事务级别。**在这种隔离级别下，一个事务会读到另一个事务更新后但未提交的数据，如果另一个事务回滚，那么当前事务读到的数据就是脏数据**，这就是**脏读**（Dirty Read）。

我们来看一个例子。

首先，我们准备好`students`表的数据，该表仅一行记录：

```sql
mysql> select * from students;
+----+-------+
| id | name  |
+----+-------+
|  1 | Alice |
+----+-------+
1 row in set (0.00 sec)
```

然后，分别开启两个MySQL客户端连接，按顺序依次执行事务A和事务B：

| 时刻 | 事务A | 事务B |
| :---: | :--- | :--- |
| 1 | SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED; | SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED; |
| 2 | BEGIN; | BEGIN; |
| 3 | UPDATE students SET name = 'Bob' WHERE id = 1; |  |
| 4 |  | SELECT \* FROM students WHERE id = 1; |
| 5 | ROLLBACK; |  |
| 6 |  | SELECT \* FROM students WHERE id = 1; |
| 7 |  | COMMIT; |

#### [video](http://liaoxuefeng.gitee.io/git-resources/read-uncommitted.mp4)

当事务A执行完第3步时，它更新了`id=1`的记录，但并未提交，而事务B在第4步读取到的数据就是未提交的数据。随后，事务A在第5步进行了回滚，事务B再次读取`id=1`的记录，发现和上一次读取到的数据不一致，这就是脏读。可见，在Read Uncommitted隔离级别下，一个事务可能读取到另一个事务更新但未提交的数据，这个数据有可能是脏数据。

* 在Read Committed隔离级别下，一个事务可能会遇到不可重复读（Non Repeatable Read）的问题。

**不可重复读是指，在一个事务内，多次读同一数据，在这个事务还没有结束时，如果另一个事务恰好修改了这个数据，那么，在第一个事务中，两次读取的数据就可能不一致**。

我们仍然先准备好`students`表的数据：

```sql
mysql> select * from students;
+----+-------+
| id | name  |
+----+-------+
|  1 | Alice |
+----+-------+
1 row in set (0.00 sec)
```

然后，分别开启两个MySQL客户端连接，按顺序依次执行事务A和事务B：

| 时刻 | 事务A | 事务B |
| :---: | :--- | :--- |
| 1 | SET TRANSACTION ISOLATION LEVEL READ COMMITTED; | SET TRANSACTION ISOLATION LEVEL READ COMMITTED; |
| 2 | BEGIN; | BEGIN; |
| 3 |  | SELECT \* FROM students WHERE id = 1; |
| 4 | UPDATE students SET name = 'Bob' WHERE id = 1; |  |
| 5 | COMMIT; |  |
| 6 |  | SELECT \* FROM students WHERE id = 1; |
| 7 |  | COMMIT; |

#### [video](http://liaoxuefeng.gitee.io/git-resources/read-committed.mp4)

当事务B第一次执行第3步的查询时，得到的结果是`Alice`，随后，由于事务A在第4步更新了这条记录并提交，所以，事务B在第6步再次执行同样的查询时，得到的结果就变成了`Bob`，因此，在Read Committed隔离级别下，事务不可重复读同一条记录，因为很可能读到的结果不一致。

* 在Repeatable Read隔离级别下，一个事务可能会遇到幻读（Phantom Read）的问题。

`幻读`**是指，在一个事务中，第一次查询某条记录，发现没有，但是，当试图更新这条不存在的记录时，竟然能成功，并且，再次读取同一条记录，它就神奇地出现了。**

我们仍然先准备好`students`表的数据：

```sql
mysql> select * from students;
+----+-------+
| id | name  |
+----+-------+
|  1 | Alice |
+----+-------+
1 row in set (0.00 sec))
```

然后，分别开启两个MySQL客户端连接，按顺序依次执行事务A和事务B：

| 时刻 | 事务A | 事务B |
| :---: | :--- | :--- |
| 1 | SET TRANSACTION ISOLATION LEVEL REPEATABLE READ; | SET TRANSACTION ISOLATION LEVEL REPEATABLE READ; |
| 2 | BEGIN; | BEGIN; |
| 3 |  | SELECT \* FROM students WHERE id = 99; |
| 4 | INSERT INTO students \(id, name\) VALUES \(99, 'Bob'\); |  |
| 5 | COMMIT; |  |
| 6 |  | SELECT \* FROM students WHERE id = 99; |
| 7 |  | UPDATE students SET name = 'Alice' WHERE id = 99; |
| 8 |  | SELECT \* FROM students WHERE id = 99; |
| 9 |  | COMMIT; |

#### [video](http://liaoxuefeng.gitee.io/git-resources/repeatable-read.mp4)

事务B在第3步第一次读取`id=99`的记录时，读到的记录为空，说明不存在`id=99`的记录。随后，事务A在第4步插入了一条`id=99`的记录并提交。事务B在第6步再次读取`id=99`的记录时，读到的记录仍然为空，但是，事务B在第7步试图更新这条不存在的记录时，竟然成功了，并且，事务B在第8步再次读取`id=99`的记录时，记录出现了。可见，幻读就是没有读到的记录，以为不存在，但其实是可以更新成功的，并且，更新成功后，再次读取，就出现了。

* Serializable是最严格的隔离级别。**在Serializable隔离级别下，所有事务按照次序依次执行**，因此，脏读、不可重复读、幻读都不会出现。虽然Serializable隔离级别下的事务具有最高的安全性，但是，由于事务是串行执行，所以**效率会大大下降**，应用程序的**性能会急剧降低**。如果没有特别重要的情景,**一般都不会使用Serializable隔离级别**。

* [x] **默认隔离级别**

如果没有指定隔离级别，数据库就会使用默认的隔离级别**。在MySQL中，如果使用**`InnoDB`**，默认的隔离级别是**`Repeatable Read`。

