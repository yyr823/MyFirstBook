### layer弹出层父子页面事件相互调用方法

* #### [原文链接](https://www.jb51.net/article/145817.htm)

* **父页面**

```js
<body>
<a data-url="bbbb.html" id="parentIframe">小小提示层</a>
<input id="shuzhi" />
<button class="but_par">父页面</button>
</body>
<script src="../jquery-1.9.1.min.js"></script>
<script src="layer/layer.js"></script>
<script>
$(function(){
$("#parentIframe").click(function(){
var a = $(this).attr("data-url");
layer.open({
  type: 2,
  content: a,
  success: function(layero, index){
    var body = layer.getChildFrame('body', index);//获取子页面内容
    //得到iframe页的窗口对象,执行iframe页的方法：iframeWin.method();
    var iframeWin = window[layero.find('iframe')[0]['name']]; 
   body.find("#transmit").click();//执行子页面的方法
    body.find('input').val('Hi，我是从父页来的')
    $(".but_par").click(function(){
    alert(222);
    })
  }
}); 
});
});
</script>
```

* **子页面**

```js
<body>
<input id="name" value="不满意" />
<button id="transmit">给父层传值</button>
</div>
</body>
<script>
$(function(){
$(document).on("click","#transmit").click(function(){
parent.$("#shuzhi").val($("#name").val());
parent.location.reload(); 刷新父页面
//关闭layer弹出层
var index = parent.layer.getFrameIndex(window.name); //获取窗口索引
parent.layer.close(index);
})
window.parent.$(".but_par").click();//执行父页面的事件
})
</script>
```



