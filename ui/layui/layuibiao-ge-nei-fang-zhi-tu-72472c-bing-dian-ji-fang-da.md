### layui表格内放置图片,并点击放大

* #### [**原文链接**](https://blog.csdn.net/huangbaokang/article/details/80697341)

```js
      //layui  table:
       done:function(res,curr,count){
                hoverOpenImg();//显示大图
                }
    //显示大图片
      function hoverOpenImg(){
        var img_show = null; // tips提示
        $('td img').hover(function(){
            //alert($(this).attr('src'));
            var img = "<img class='img_msg' src='"+$(this).attr('src')+"' style='width:130px;' />";
            img_show = layer.tips(img, this,{
                tips:[2, 'rgba(41,41,41,.5)']
                ,area: ['160px']
            });
        },function(){
            layer.close(img_show);
        });
        $('td img').attr('style','max-width:70px');
    }
```





