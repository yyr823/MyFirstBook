### JavaScript中创建对象主要有3种方式

> #### 使用 new关键字调用构造器创建对象

```js
<script type="text/javascript">
function Student(name,age) {
this.name=name;
this.age=age;
}
var  s1=new Student();//没有传入参数
var  s2=new Student("haogeshuai",30) ;
document. write(s1.name+"--"+s1.age+"<br/>");
document. write(s2.name+"--"+s2.age) ;
</script>
```

> #### 使用Object直接创建对象

```js
<script type="text/javascript">
var myObj=new Object() ;
myObj.name="haogeshuai"; 
myObj.age=34;
myObj.info=function(){
document. write("我的名字叫: "+this.name+"<br/>") ; 
document. write("今年"+this.age+"岁<br/>") ;
}
myObj.info();

</script>
```

> #### **JavaScript使用JSON创建对象的语法**

* [x] `JSON(JavaSoript Objeot Notation)`是一种轻量级的数据交换,易于人阅读和编写.

* [x] **JSON的格式**

  JSON对象是以一对`”大括号”`括起来,  
  大括号内以多个”名值对”组成,多个名值对之问用`“逗号”`隔开,名所对应的值可以是各种数据类型的值,  
  也可以是JSON对象。 JSON数组用`“[]”`括起来.

* ##### **语法**

```js
object={属性名1:属性值1,属性名2:属性值2,...}
```

**示例:**

```js
var p={
name: "haogeshua i,
gender: "male",
info: function (){
document.write("姓名:"+this.name+",性别:"+this.gender);
}
}
 p.info();
```

* 对象是 JavaScript的特性之一,它是一种非常重要的数据类型,是自我包含的数据集合。这里介绍两个实用的具体对象
  `Date和Math`

> #### 创建Date对象方法

| new Date\(\) |
| :--- |
| new Date\(month dd,yyyy hh:mm:ss\) |
| new Date\(yyyy,mth,dd,hh,mm.ss\) |
| new Date\(yyyy,mth,dd\) |
| new  Date\(ms\) |

> #### Date对象设置时间方法

| setDate\(\) | 设置Date对象中月的某一天\(1~31\) |
| :---: | :---: |
| setMonth\(\) | 设置Date对象中月份\(0~11\) |
| setFullYear\(\) | 设置Date对象中的年份\(四位数字\) |
| setHours\(\) | 设置Date对象中的小时\(0~23\) |
| setMinutes\(\) | 设置Date对象中的分钟\(0~59\) |
| setSeconds\(\) | 设置Date对象中的秒钟\(0~59\) |
| setMilliseconds\(\) | 设置Date对象中的亳秒\(0~999\) |

> #### Date对象获取时间细节方法

| getDate\(\) | 从Date对象返回一个月中的某一天\(1~31\) |
| :---: | :---: |
| getDay\(\) | 从Date对象返回一周中的某一天\(0~6\) |
| getMonth\(\) | 从Date对象返回月份\(0~11\) |
| getFullYear\(\) | 从Dae对象以四位数字返回年份 |
| getHours\(\) | 返回Date对象的小时\(0~23\)。 |
| getMinutes\(\) | 返回Date对象的分钟\(0~59\) |
| getSeconds\(\) | 返回Date对象的秒数\(0~59\) |
| getTime \(\) | 返回1970年1月1日至今的亳秒数 |

> #### Math对象的常用方法

| abs\(x\) | 返回数的绝对值 |
| :---: | :---: |
| ceil\(x\) | 对数进行上舍入 |
| floor\(x\) | 对数进行下舍入 |
| max\(x,y\) | 返回x和y的最高值 |
| min\(x,y\) | 返回x和y的最低值 |
| pow\(x,y\) | 返回x的y次幂 |
| random\(\) | 返回0~1之间的随机数 |
| round\(x\) | 把数四舍五入为最接近的整数 |
| sqrt\(x\) | 返回数的平方根 |



