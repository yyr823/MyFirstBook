### 根据指定的时间来跟当前时间比较计算倒计时

* #### [原文链接](https://www.cnblogs.com/cyl168/p/5091495.html)

```js
<!-- 指定的时间 -->

<span class="timeCount" data-enddate='<fmt:formatDate value="${dateTime}" pattern="yyyy-MM-dd HH:mm:ss"/>'>
00:00:00
</span>

<!-- jquery -->

<script type="text/javascript">

//初始化倒计时间
$(function(){
$(".menu li").each(function(){
if($(this).attr("class") == "checked"){
setInterval(GetRTime,1000); 
}
});
}); 

function GetRTime(){
var EndTime= new Date($(".timeCount").attr("data-enddate"));//new Date('2015/12/31 10:00:00'); //截止时间 前端路上 http://www.51xuediannao.com/qd63/
var NowTime = new Date();//当前时间
var t =EndTime.getTime() - NowTime.getTime();
//var d=Math.floor(t/1000/60/60/24);//天
var h=Math.floor(t/1000/60/60%24);//时
var m=Math.floor(t/1000/60%60);//分
var s=Math.floor(t/1000%60);//秒
if(parseInt(h)<10){
h="0"+h;
}
if(parseInt(m)<10){
m="0"+m;
}
if(parseInt(s)<10){
s="0"+s;
}
$(".timeCount").text(h + ":"+m + ":"+s );
}

</script>
```



