### Java生成一定规则递增编号

* #### [**参考链接**](https://blog.csdn.net/qq_39949109/article/details/80482923)

* 项目需求中有时需要生成一定规则递增编号。例如生成设备编号：设备类型+五位编号（从1开始,不够前补0）,也就是SYXH000001/SYXH00002/SDOI00001类似这样。 

* 那么如何处理000001自增1变为000002呢？

```java
package com.lyf.test;
 
public class Test2 {
 
    /**
     * 生成规则设备编号:设备类型+五位编号（从1开始，不够前补0）
     * 
     * @param equipmentType
     *              设备类型
     * @param equipmentNo
     *              最新设备编号
     * @return
     */
    public static String getNewEquipmentNo(String equipmentType, String equipmentNo){
        String newEquipmentNo = "00001";
 
        if(equipmentNo != null && !equipmentNo.isEmpty()){
            int newEquipment = Integer.parseInt(equipmentNo) + 1;
            newEquipmentNo = String.format(equipmentType + "%05d", newEquipment);
        }
 
        return newEquipmentNo;
    }
 
    public static void main(String[] args) {
        String equipmentNo = Test2.getNewEquipmentNo("SYXH", "00032");
        System.out.println("生成设备编号：" + equipmentNo);
        //生成设备编号：SYXH00033
    }
 
}
```

* 从上面代码中可以看到,首先我们**默认了一个初始设备编号**,当传入方法的最新设备编号为null或是空时将使用。 如果传入了数据库中最新设备编号,将首先Integer的**`parseInt()`**方法返回十进制整数,这样就可以对其+1。 最后通过String的**`format()`**方法进行字符串格式化返回就可以了。



