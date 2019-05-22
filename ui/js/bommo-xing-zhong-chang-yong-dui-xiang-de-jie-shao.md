#### **BOM-javaScript是运行在浏览器中的, 所以提供了一系列对象用于和浏览器窗口进行交互, 这些对象主要包括window、document、screen、location、  navigator等.通常统称为浏览器对象模型\(Brower Object Model\)**

> #### window对象是整个JavaScript脚本运行的顶层对象, 它的常用属性如下

| document | 返回该窗口内装载的HTML文档 |
| :---: | :--- |
| location | 返回该窗口装载的HTML文档的uRL |
| navigator | 返回浏览当前页面的浏览器, 包含了一系列的浏览器属性, 包括名称、版本号和平台等 |
| screen | 返回当前浏览者屏幕对象 |
| history | 返回该浏览窗口的历史 |

> #### Iocation对象常用属性如下

| hostname | 文档所在地址的主机名 |
| :---: | :--- |
| href | 文档所在地址的uRL地址 |
| host | 文档所在地址的主机地址 |
| port | 文档所在地址的服务端口 |
| pathname | 文档所在地址的文件地址 |
| protocol | 装载该文档所使用的协议, 例如HTTP:等 |

![](/assets/bo4.png)

```
host name:localhost
href:http://1ooalhost:80l1l8/study/test.html
host adress:1ocalhost:8088
port:8088
protoco1 : http:
availHeight:920
availWidth:1280
colorDepth:24
appCodeName:Mozilla
appName:Netscape
appVersion:5.0  (Windows NT 6.1;  WOW64) AppleWebKit/537.36  (KHTML,like Gecko) Chrome/33.0.1750.117 Safari/537.36 
platform:Win32               
userAgent:Mozilla/5.0   (Windows NT 6.1;WOW64) AppleWebKit/537.36 (KHTML,like Gecko) Chrome/33.0.1750.117 Safari/537.36 
cookieEnabled:true
```

> #### screen对象常用属性如下

| availHeight | 窗口可以使用的屏幕高度, 单位像素 |
| :---: | :--- |
| availwidth | 窗口可以使用的屏幕宽度,单位像素 |
| colorDepth | 用户浏览器表示的颜色位数,通常为32位\(每像素的位数\) |

> #### navigator对象常用属性如下

| appcodeName | 浏览器代码名的字符串表示 |
| :---: | :--- |
| appName | 官方浏览器名的字符串表示 |
| appVersion | 浏览器版本信息的字符串表示 |
| platform | 浏览器所在计算机平台的字符串表示 |
| userAgent | 用户代理头的字符串表示 |
| cookieEnabled | 如果启用cookie返回true, 否则返回false |

> #### history对象常用方法如下

| back\(\) | 后退到上一个浏览的页面,如果该页面是第一个打开的,则无效果 |
| :---: | :--- |
| forward\(\) | 前进到下一个;刘览页面,如果该页面是第一个打开的,则无效果 |
| go\(IntValue\) | 该方法可指定前进或后退多少个页面,正前进,负后退 |

> #### window对象的常用方法

| alert\(\), confirm\(\),prompt\(\) | 分别用于弹出警告窗口、 确认对话框和提示输入对话框 |
| :---: | :--- |
| close\(\) | 关闭窗口 |
| moveBy\(\)、 moveTo\(\) | 移动窗口 |
| resizeBy\(\)、 resizeTo\(\) | 重设窗口大小 |
| scrollBy\(\)、 scrollTo\(\) | 滚动当前窗口的HTML文档 |
| open\(\) | 打开一个新的浏览器窗口加载新的uRL所指向的地址, 并可指定一系列新的属性, 包括隐藏菜单等 |
| setIntervaI\(\),clearInteral\(\) | 设置、删除定时器 |



