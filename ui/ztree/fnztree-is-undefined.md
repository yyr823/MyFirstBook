### $.fn.zTree is undefined

> #### 场景

**在使用ztree做目录树功能的时候,在初始化的时候报 $.fn.zTree is undefined 错误**

> #### 原因及解决办法

* [x] **在父页面引用的jquery相关js文件,layui弹出层引用页面,子页面同时引用了jquery和ztree相关的js**

* **子页面引入js库放到body标签中,保存后再运行**

* [x] **把jquery的js放在了ztree的下面,ztree覆盖了jquery里面的一些内容**

* **把jquery的js放在前面即可**



