### layui表格内放置图片,并点击放大

* #### [**原文链接**](https://blog.csdn.net/weixin_44285250/article/details/86299108)

```js
cols: [[ //表头
		 {
            field: 'brand_img_url',
            title: '图片',
            sort: true,
            templet: function(d){
                return '<div onclick="show_img(this)" ><img src="'+d.brand_img_url+'" alt="" width="50px" height="50px"></a></div>';
            }
        }
		]]
		
  //显示大图片
        function show_img(t) {
            var t = $(t).find("img");
            //页面层
            layer.open({
                type: 1,
                skin: 'layui-layer-rim', //加上边框
                 area: ['80%', '80%'], //宽高
                shadeClose: true, //开启遮罩关闭
                end: function (index, layero) {
                    return false;
                },
                content: '<div style="text-align:center"><img src="' + $(t).attr('src') + '" /></div>'
            });
        }		
		
```





