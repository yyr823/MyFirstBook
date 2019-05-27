* #### [原文链接](https://blog.csdn.net/qq_43135507/article/details/90600759)
* 前台使用的是layui  由于后台jpa多表查询使用的是 List&lt;Map&lt;String, Object&gt;&gt; 自定义字段输出 因此时间create\_time方面会出现问题,template定义的有解决方法.

* 前台部分代码

```js
    table.render({
            elem: '#demo',
            url: server + 'orders/getAllOrders',
            cellMinWidth: 80,
            size: 'lg',
            title: 'orders',
            cols: [
                [ //标题栏
                    {
                        checkbox: true
                    },
                    {
                        field: 'order_no',
                        title: 'orderNo',
                            sort: true
                        },
                    {
                        field: 'uno',
                        title: 'uno',
                        sort: true,
                        align: 'center'
                    },
                    {
                        field: 'create_time',
                        title: 'createTime',
                            sort: true,
  //特殊日期格式转换2018-12-03T17:17:36.000+08:00 转化为2018-12-03 00:00:00(正则表达式的方法)
                        templet: function(d) { 
                            var dateee = new Date(d.create_time).toJSON();    
                            var date = new Date(+new Date(dateee) + 8 * 3600 * 1000).toISOString().replace(/T/g, ' ').replace(/\.[\d]{3}Z/, '') 
                            return date;
                        },
                        align: 'center'
                    }
                    ,.....
                    ]]
                    });
```

* 实体类接收前台传来条件

```java
/**
 @ClassName：ProductSelect
 @Author：yyr
 @Date：2019-04-16 9:54
 @Description：分页查询使用条件类
 */
@Data
public class ProductSelect {
    //当前第几页
    private int page;
    //每页多少条数据
    private int limit; 
    //模糊查询名称条件
    private String name="";
    //订单类型
    private String selectType="";
    //按某一列进行排序
    private String field;
    //排序方式(ASC/DESC)
    private String order;
}
```

* Controller方法定义

```java
   @ApiOperation(value = "条件查询订单详细信息并进行分页", notes = "条件查询订单详细信息并进行分页")
    @ApiImplicitParam(name = "pro", value = "查询的条件", required = true, dataType = "ProductSelect")
    @RequestMapping(value = "/getAllOrders", method = RequestMethod.GET)
    public Object getAllOrders(ProductSelect pro) {
        Sort sort=null;
        if (pro.getField() == null) {
        //默认时间降序排序
            sort=new Sort(Sort.Direction.ASC,"create_time");
        } else {
            String s="desc";
            if(pro.getOrder().equals(s)){
                 sort=new Sort(Sort.Direction.DESC,pro.getField());
            }else{
                sort=new Sort(Sort.Direction.ASC,pro.getField());
            }
        }
       String type = pro.getSelectType();
        String order_type = "";
        if (type != "") {
            switch (type) {
                case "pro":
                    order_type = "PI";
                    break;
                case "point":
                    order_type = "GI";
                    break;
                case "demand":
                    order_type = "DE";
                    break;
                default:
                    System.out.println("没有啦");
            }
        }
        //接收的名称
        String name = pro.getName();
        //分页和排序
        Pageable pageable= PageRequest.of(pro.getPage() - 1,pro.getLimit(),sort);
        //条件查询后排序和分页后的数据
        List<Map<String, Object>> list = productOrderDao.getAllOrders(name, order_type,pageable);
        //条件查询后数据总条数
        int total = productOrderDao.getTotal(name, order_type);
        return MapTool.paging(list, total);
    }
```

* MapTool工具类 \(layui前台接收数据时有一定格式要求的,所以要按一定格式返回\)

```java
public class MapTool {
    private static Map<String, Object> map = new HashMap<>();
    public static Object paging(List<?> list, long count) {
        map.put("count", count);
        map.put("code", 0);
        map.put("msg", "返回信息成功");
        map.put("data", list);
        return map;
    }
    }
```

* 接口:原生sql多表条件查询

```java
public interface ProductOrderDao extends JpaRepository<ProductOrder,Integer> {
/**
     * 获取条件查询后的订单
     *  @param name 订单编号/客户编号/业务编号(产品订单+积份订单+需求订单 取三种订单的共同字段-订单编号,客户编号,订单状态,创建时间,业务编号)
     *  @param type 订单类型
     *  @param sort 分页排序
     *  @return
     */
    @Query(value = "select * from (SELECT p.order_no ,p.uno,p.order_status ,p.create_time ,(SELECT sno FROM users WHERE uno=p.uno)sno  " +
            " FROM product_order p UNION  " +
            "SELECT g.order_no,g.uno,g.status,g.charge_time,(SELECT sno FROM users WHERE uno=g.uno)sno FROM gift_charge g  " +
            "UNION  SELECT  d.orderno,d.uno,d.status,d.createtime, (SELECT sno FROM users WHERE uno=d.uno)sno FROM demands d " +
            " ) p   WHERE (order_no LIKE  concat('%',?1,'%') OR uno LIKE concat('%',?1,'%') OR sno LIKE concat('%',?1,'%')) " +
            "  AND  order_no LIKE concat('%',?2,'%')  ",nativeQuery = true)
    List<Map<String, Object>> getAllOrders( String name, String type, Pageable sort);
    /**
     * 获取条件查询后订单的总数
     * @param name 订单编号/客户编号/业务编号
     * @param type 订单类型
     * @return
     */
    @Query(value = "select count(*) from (SELECT p.order_no,p.uno,p.order_status,p.create_time,(SELECT sno FROM users WHERE uno=p.uno)sno  " +
            " FROM product_order p   UNION  " +
            "SELECT g.order_no,g.uno,g.status,g.charge_time,(SELECT sno FROM users WHERE uno=g.uno)sno FROM gift_charge g " +
            "UNION  SELECT  d.orderno,d.uno,d.status,d.createtime, (SELECT sno FROM users WHERE uno=d.uno)sno FROM demands d )t" +
            " WHERE (order_no LIKE  concat('%',?1,'%') OR uno LIKE concat('%',?1,'%') OR sno LIKE concat('%',?1,'%')) " +
            "    AND  order_no LIKE concat('%',?2,'%')  " ,nativeQuery = true)
    int getTotal(String name, String type);
}
```

* 经测试可用,但需注意getAllOrders\(\)sql编写:排序时可先正常编写sql,运行后检查控制台sql语句后跟随的排序是如何定义的,以创建时间升序为例-本接口下sql语句后跟随的是

```java
 order by p.create_time asc limit ?
```

后台sql中会自动给字段找了个别名引用,或许跟接口定义有关吧

```java
 ProductOrderDao extends JpaRepository<ProductOrder,Integer>
```

* 因此将查询后的数据重新放进另一张表并定义好别名p: 这样sql语句运行时就不会出现字段异常

```java
select * from (需要查询的数据) p
```

* 原接口本想使用

```java
Page<Map<String, Object>> getAllOrders( String name, String type, Pageable sort);
```

这样count就不需要手动再次编写,但是查询总数时出现问题 count查询语句不正确,因此放弃

最后分两步走,先条件查询数据,再条件查询count

