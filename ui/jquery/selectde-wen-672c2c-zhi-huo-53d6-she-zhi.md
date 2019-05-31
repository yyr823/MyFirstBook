### Select的文本,值获取/设置/删除/清空

* #### [原文链接](https://www.cnblogs.com/zonglonglong/p/6274971.html)

* ####  获取select 

```js
//获取select 选中的 text :
    $("#ddlregtype").find("option:selected").text();

//获取select选中的 value:
    $("#ddlregtype ").val();

//获取select选中的索引:
    $("#ddlregtype ").get(0).selectedindex;
```

* ####  设置select

```js
//设置select选中的索引：
    $("#ddlregtype ").get(0).selectedindex=index;//index为索引值

//设置select 选中的value：
    $("#ddlregtype ").attr("value","normal“);
    $("#ddlregtype ").val("normal");
    $("#ddlregtype ").get(0).value = value;

//设置select 选中的text:
    var count=$("#ddlregtype option").length;
      for(var i=0;i<count;i++)
         {   if($("#ddlregtype ").get(0).options[i].text == text)
            {
                $("#ddlregtype ").get(0).options[i].selected = true;
                break;
            }
        }
    $("#select_id option[text='jquery']").attr("selected", true);

//设置select option项:

    $("#select_id").append("<option value='value'>text</option>");  //添加一项option
    $("#select_id").prepend("<option value='0'>请选择</option>"); //在前面插入一项option
```

* #### select删除/清空

```js
$("#select_id option:last").remove(); //删除索引值最大的option
$("#select_id option[index='0']").remove();//删除索引值为0的option
$("#select_id option[value='3']").remove(); //删除值为3的option
$("#select_id option[text='4']").remove(); //删除text值为4的option
$("#ddlregtype ").empty();//清空
```



