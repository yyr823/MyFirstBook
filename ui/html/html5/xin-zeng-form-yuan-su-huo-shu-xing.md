> #### 新增的form元素

* [x] **新增的datal ist元素**

data l ist元素用于为输入提供一个可选的列表, 用户可以直接选择列表中的某一选项, 从而免去了输入的麻烦 。

```HTML
请输入网址: <input aria-label="tt" type="text" list="url_list" />
  <datalist id="url_list">
    <option label="新浪" value="http://www.sina.com.cn"></option>
    <option label="搜狐" value="http://www.souhu.com"></option>
    <option label="网易" value="http://www.163.com"></option>
</datalist>
```

* [x] **新增的keygen元素**

keygen元素是秘钥对生成器, 能够使用户验证更为可靠。 用户提交表单时会生成两个键,一个私钥,一个公钥,私钥保存客户端而公钥会发送到服务端。 \(**浏览器兼容性差**,目测在**火狐上**可显示,其他不支持\)

```HTML
请选择加密强度:  <keygen name="security"/>
```

* [x] **新增的output元素**

output元素用于浏览器中显示计算结果或脚本输出, 包含完整的开始和结束标签。

`语法: <output  name="">text</output>`

```js
<script>
    function multi(){
      let a, b;
      a = parseInt(prompt("请输入第一个数字"));
      b=parseInt(prompt("请输入第二个数字"));
      document.forms["form"]["result"].value=a*b;
    }
</script>

<body onload="multi()">
<form action="#" method="get" name="form">
两数的乘积为:<output name="result"></output>
</form>
```

> #### 新增的form属性

* [x] **新增的autocomplete属性**

当此属性用于form元素时, 所有从属于该form的元素都具备自动完成功能。 如果要使用个别元素关闭自动完成功能, 则单独为该元素指定autocomplete=“off”即可。

```HTML
请输入用户名:<input type="text" name="user_name" autocomplete="on"/>
```

* [x] **新增的novalidate属性**

此属性用于提交表单时取消整个表单的验证, 即关闭对表单内所有元素的有效检查 。 如果只取消表单中较少部分内容的验证而不一妨碍提交的大部分内容, 则可以将此属性单独用于表单中的这些元素。

```HTML
<form action="#" enctype="application/x-www-form-urlencoded" id="testform" method="get" novalidate>
  请输入电子邮件地址:<input type="email" name="userid"><br>
  <input type="submit" value="formaction" formaction="http://www.souhu.com"/> <!--修改跳转的路径-->
  <input type="submit" value="formenctype" formenctype="multipart/form-data"/> <!-- 修改enctype类型-->
  <input type="submit" value="formmethod" formmethod="post"/>  <!--修改请求的方式-->
novalidate<===> <input type="submit" value="formnovalidate" formnovalidate="formnovalidate" >  <!--表单验证是否开启-->
</form>
```





