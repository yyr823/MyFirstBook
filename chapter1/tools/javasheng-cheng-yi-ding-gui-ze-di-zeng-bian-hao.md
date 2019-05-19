### Java生成一定规则递增编号

> #### [**参考链接**](#)

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

* 从上面代码中可以看到,首先我们**默认了一个初始设备编号**,当传入方法的最新设备编号为null或是空时将使用。 如果传入了数据库中最新设备编号,将首先Integer的`parseInt()`方法返回十进制整数,这样就可以对其+1。 最后通过String的`format()`方法进行字符串格式化返回就可以了。

> #### [生成ID模板：年月日时分秒+6位自增码](https://blog.csdn.net/moneyshi/article/details/46805433)

```java
private static int sequence = 0;

    private static int length = 6;

    /**
     * YYYYMMDDHHMMSS+6位自增长码(20位)
     * @author shijing
     * 2015年6月29日下午1:25:23
     * @return
     */
    public static synchronized String getLocalTrmSeqNum() {
        sequence = sequence >= 999999 ? 1 : sequence + 1;
        String datetime = new SimpleDateFormat("yyyyMMddHHmmss")
        .format(new Date());
        String s = Integer.toString(sequence);
        return datetime +addLeftZero(s, length);
    }

    /**
     * 左填0
     * @author shijing
     * 2015年6月29日下午1:24:32
     * @param s
     * @param length
     * @return
     */
    public static String addLeftZero(String s, int length) {
        // StringBuilder sb=new StringBuilder();
        int old = s.length();
        if (length > old) {
            char[] c = new char[length];
            char[] x = s.toCharArray();
            if (x.length > length) {
                throw new IllegalArgumentException(
                        "Numeric value is larger than intended length: " + s
                                + " LEN " + length);
            }
            int lim = c.length - x.length;
            for (int i = 0; i < lim; i++) {
                c[i] = '0';
            }
            System.arraycopy(x, 0, c, lim, x.length);
            return new String(c);
        }
        return s.substring(0, length);

    }
```

* 注意：如果你的ID是Long型,就要注意,Long的最大长度为19位,如果直接转的话会有问题，建议改为**年月日时分秒+5位随机数**

> #### [取当前时间与字母随机组合，并发少的情况足以胜任](https://blog.csdn.net/uucai/article/details/8264383)

```java
import java.util.Random;
 //随机组合16位ID
public class SeeId{
    public static void main(String[] args) {
        Long h = System.currentTimeMillis();//获得当前时间的毫秒数
        String str = h.toString();//转化为字符串
        int i = str.length();//总长度
        int j = i-7;//用来取此字符串的末尾7位数，因为前面的数是年份什么的基本不变，我们只用后面的7位
        char[] charArray = str.substring(j,i).toCharArray();//将取到的7位数做成数组
        //将26位字母做成数组
        String [] arr = {"a", "b", "c", "d","e", "f", "g", 
                    "h","i","g", "k", "l","m", "n", 
                    "o", "p","q", "r", "s", "t",
                    "u", "v", "w", "x","y", "z"};
        //将字母数组随机取3个字母组成一个字符串，一共组成3个字符串放到目标数组target中
        StringBuffer uniqueId = new StringBuffer();//用于生成唯一ID
        Random random = new Random();//用于取随机数和布尔值
        boolean insertflag = true;//用来控制是插入数字还是字母
        int timecount = 0;//用来控制插入数字的长度，别超过7
        int zimucount = 0;//用来控制插入字母的总数，别超过9 7个数字加上9个字母组合
        boolean timeflag = true;//判断时间是否插入了7位，默认true为不满
        boolean zimuflag = true;//判断字母是否插入了9位，默认true为不满
        while (zimucount<9||timecount<7) {//开始组合
            if(insertflag){//默认为ture，先加字母，你也可以先加数字
                if (zimucount<9) {//如果uniqueId插入的字母总数没超过9个
                    uniqueId.append(arr[random.nextInt(26)]);//则在字母数组中随机选一个插入
                    zimucount++;//对应加1
                    if(timeflag){//如果时间没有插入满7位则重新抓阄看插入时间还是数字
                    insertflag = random.nextBoolean();//重置flag，随机产生false还是true
                    }//如果timeflag=false,时间数字已经插入满7位，则不抓阄了。保持insertflag=true
                }else{//如果已经加够了否则不操作，
                    zimuflag = false;//将zimuflag变为已加够，false
                    insertflag = false;//将插入权判断给时间数字
                }
            }else{
                if (timecount<7) {//先加时间转化成的数组，你也可以先加字母
                    //此处取时间数字数组不能用random随机取。那样用时间来生成数组就没意义了
                    uniqueId.append(charArray[timecount]);//不可打乱顺序
                    timecount++;//对应加1
                    if(zimuflag){//如果字母没有插入满9位则重新抓阄看插入时间还是数字
                        insertflag = random.nextBoolean();
                    }//如果zimuflag=false,字幕已经插入满9位，则不抓阄了。保持insertflag=false
                }else{
                    timeflag = false;//将timeflag变为已加够，false
                    insertflag = true;//将插入权判断给字母
                }
            }
        }
        System.out.println(uniqueId.toString());//得到最终id
    }
}
```



