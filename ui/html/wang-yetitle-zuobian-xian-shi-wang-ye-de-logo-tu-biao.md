### 在html&lt;title&gt;&lt;/title&gt;标签添加图标,网页title左边显示网页的logo图标

#### ![](/assets/hq1.png)

* #### [**原文链接**](https://segmentfault.com/a/1190000007952589)

* **步骤一：**在图片中显示图标，这里的图片只支持ico格式，需要转换图片格式.原始图像可以接受: .jpg .jpeg .gif .png等图像格式 在这个[**网址**](http://www.bitbug.net/)上传你的原始图片然后生成ico格式图标\(百度ico可以找到制作ico图标的网站\) **注意：图标要用 16\*16 的\(保证了兼容性,无论在哪个地方都可以显示\)**

* **步骤二：把图标放到网站根目录** 在&lt;head&gt;&lt;/head&gt;引入图标,网页标题左侧显示：

* [x] &lt;link rel="icon" href="图标地址" type="image/x-icon"&gt;

* [x] 收藏夹显示图标:&lt;link rel="shortcut icon" href="图标地址" type="image/x-icon"&gt;

```HTML
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8" />
            <title>一个有梦想咸鸭蛋</title>
            <!--网页标题左侧显示-->
            <link rel="icon" href="1111.ico" type="image/x-icon">
            <!--收藏夹显示图标-->
            <link rel="shortcut icon" href="1111.ico" type="image/x-icon">
        </head>
        <body>
        </body>
    </html>
```

**建议把生成的图标名称改掉,在引用;如生成后是bitbug\_favicon.ico改为你起的名字.ico.如果没有生效-关闭浏览器重新打开**

![](/assets/hq2.png)

* **怎么样获取别人的Logo**

在网站首页 打开开发者工具;在Elements里&lt;head&gt;&lt;/head&gt;里找到&lt;link rel="icon" href="图标名称.ico" type="image/x-icon"&gt;  
![](/assets/hq3.png)点击右键在新标签页打开链接\(Goolge是Open link in new tab\)注意要在href的链接地址右键不然没有Open link in new tab这个选项。



