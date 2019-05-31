### Spring Data JPA调用存储过程实例

* #### [原文链接](https://blog.csdn.net/chszs/article/details/50127823)
* SQL方面

假设调用的存储过程形式如下：

```Sql
call PROCEDURE in_only_test (inParam1 IN VARCHAR);
call PROCEDURE in_and_out_test (inParam1 IN VARCHAR, outParam1 OUT VARCHAR);
```

这里有两个存储过程：

* [x] in\_only\_test           它需要一个输入参数inParam1,但不返回值

* [x] in\_and\_out\_test    它需要一个输入参数inParam1,且返回值outParam1

* JPA方面

我们可以使用@NamedStoredProcedureQueries来调用存储过程。

```java
@Entity
@Table(name = "MYTABLE")
@NamedStoredProcedureQueries({
        @NamedStoredProcedureQuery(name = "in_only_test", procedureName = "in_only_test", parameters = {
                @StoredProcedureParameter(mode = ParameterMode.IN, name = "inParam1", type = String.class) }),
        @NamedStoredProcedureQuery(name = "in_and_out_test", procedureName = "in_and_out_test", parameters = {
                @StoredProcedureParameter(mode = ParameterMode.IN, name = "inParam1", type = String.class),
                @StoredProcedureParameter(mode = ParameterMode.OUT, name = "outParam1", type = String.class) }) })
public class MyTable implements Serializable {
}
```

**关键要点:    
**存储过程使用了注释`@NamedStoredProcedureQuery`并绑定到一个JPA表。`procedureName`是存储过程的名字  
`name`是JPA中的存储过程的名字  
使用注释`@StoredProcedureParameter`来定义存储过程使用的IN/OUT参数

* MyTableRepository仓库调用存储过程

```java
public interface MyTableRepository extends CrudRepository<MyTable, Long> {
    @Procedure(name = "in_only_test")
    void inOnlyTest(@Param("inParam1") String inParam1);
    @Procedure(name = "in_and_out_test")
    String inAndOutTest(@Param("inParam1") String inParam1);
}
```

**关键要点:**

* [x] **@Procedure的name参数必须匹配@NamedStoredProcedureQuery的name**

* [x] **@Param必须匹配@StoredProcedureParameter注释的name参数**

* [x] **返回类型必须匹配:in\_only\_test存储过程返回是void,in\_and\_out\_test存储过程必须返回String**

* **调用**

```java
// 向存储过程传递参数并返回值
String inParam = "Hi Im an inputParam";
String outParam = myTableRepository.inAndOutTest(inParam);
Assert.assertEquals(outParam, "Woohoo Im an outparam, and this is my inparam Hi Im an inputParam");
// 向存储过程传递参数不返回值
myTableRepository.inOnlyTest(inParam);
```

* #### 其它技巧
* [x] **原生sql查询**

```java
//本案例为自定义的结果数据
@Query(value = " call get_order(?1,?2,?3,?4)", nativeQuery = true)
List<Map<String, Object>>  showOrderMoney( String begin, String end,  String sno, String country);
```

**需注意:该存储过程本身主要针对的是select返回数据,即调用存储过程之后本身就有结果,所有与out参数无关.**

* [x] **定义自定义的Repository来调用存储过程    
  **

* 定义自定义的Repository:

```java
public interface MyTableRepositoryCustom {
    void inOnlyTest(String inParam1);
}
```

* 然后要确保主Repository类继承了这个接口。

```java
public interface MyTableRepository extends CrudRepository<MyTable, Long>, MyTableRepositoryCustom {
}
```

* 创建Repository实现类

```java
public class MyTableRepositoryImpl implements MyTableRepositoryCustom {
@PersistenceContext
private EntityManager em;
@Override
public void inOnlyTest(String inParam1) {
    this.em.createNativeQuery("BEGIN in_only_test(:inParam1); END;").setParameter("inParam1", inParam1)
            .executeUpdate();
}}
```

* 可以以常规的方式进行调用

```java
@Autowired
MyTableRepository myTableRepository;
// 调用存储过程
myTableRepository.inOnlyTest(inParam1);
```



