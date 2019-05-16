* #### jQuery判断复选框是否被选中

```
方法一：
if ($("#checkbox-id").get(0).checked) {
    // do something
}


方法二：
if($('#checkbox-id').is(':checked')) {
    // do something
}


方法三：
if ($('#checkbox-id').attr('checked')) {
    // do something
}


在jQuery1.6版本之后，取复选框有没有被选中，要用prop
if($('#checkbox-id').prop('checked'))
{
　　//do something
}
 
```

* #### tr变色

```
$(function () {
    //input 单击事件
    $("input").click(function () {
        //获取checkbox选中项
        if ($(this).attr('checked')) {
            $(this).parent().parent().css("background", "#d4efff");
        } else {
            $(this).parent().parent().css("background", "");
        }
    });
});
```

**$\(this\).parent\(\)--&gt;找到当前行td   --&gt;$\(this\).parent\(\).parent\(\) --&gt;找到当前行td的父亲tr**



