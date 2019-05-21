#### 特殊日期格式转换2018-12-03T17:17:36.000+08:00 转化为2018-12-03 00:00:00\(正则表达式的方法\)

* #### [**原文链接**](https://blog.csdn.net/u012967454/article/details/84789206)

```js
// str=2018-12-03T17:17:36.000+08:00 转化为2018-12-03 00:00:00
function toDate(str){
 var dateee = new Date(str).toJSON();
  var date = new Date(+new Date(dateee)+8*3600*1000).toISOString().replace(/T/g,' ').replace(/\.[\d]{3}Z/,'')  
   console.log("时间2==="+date);
   return date ;
}
```



