### input file控件限制上传文件类型

* #### [**原文链接**](https://www.cnblogs.com/haocool/p/3431181.html)
* [x] 网页上添加一个input file HTML控件：

```html
<input id="File1" type="file" />
```

| 默认是这样的，所有文件类型都会显示出来，如果想限制它只显示我们设定的文件类型呢，比如“word“,”excel“,”pdf“文件 |
| :---: |


![](https://images0.cnblogs.com/blog/45145/201311/19115433-589a4a8a1d9141039322c1b2b5cf8612.jpg)

* [x] 解决办法是可以给它添加一个accept属性，比如：

```html
<input id="File1" type="file"  accept=".xls,.doc,.txt,.pdf"  />
```

这样选择的时候默认会显示为这样：

![](https://images0.cnblogs.com/blog/45145/201311/19114731-3c24c5f8244c4274851bb937d13c2ff4.jpg)

文件选择框内只显示出你自定义文件类型的文件，也还比较方便。But,这只是最简单的掩人耳目的做法，还是能选择其它文件类型：

![](https://images0.cnblogs.com/blog/45145/201311/19120049-c0bdf658c4fe47c994d240d53d7c81d5.jpg)

**所以，如果要做到真正意义上限制类型做法（其实这种算不上限制，只是把你要的文件类型默认显示出来而已，并不是说不能选择其它的）,还是要通过js或者后台来控制。**

* [x] 支持的文件类型:

```txt
*.3gpp  audio/3gpp， video/3gpp  3GPP Audio/Video
*.ac3   audio/ac3   AC3 Audio
*.asf   allpication/vnd.ms-asf  Advanced Streaming Format
*.au    audio/basic AU Audio
*.css   text/css    Cascading Style Sheets
*.csv   text/csv    Comma Separated Values
*.doc   application/msword  MS Word Document
*.dot   application/msword  MS Word Template
*.dtd   application/xml-dtd Document Type Definition
*.dwg   image/vnd.dwg   AutoCAD Drawing Database
*.dxf   image/vnd.dxf   AutoCAD Drawing Interchange Format
*.gif   image/gif   Graphic Interchange Format
*.htm   text/html   HyperText Markup Language
*.html  text/html   HyperText Markup Language
*.jp2   image/jp2   JPEG-2000
*.jpe   image/jpeg  JPEG
*.jpeg  image/jpeg  JPEG
*.jpg   image/jpeg  JPEG
*.js    text/javascript， application/javascript JavaScript
*.json  application/json    JavaScript Object Notation
*.mp2   audio/mpeg， video/mpeg  MPEG Audio/Video Stream， Layer II
*.mp3   audio/mpeg  MPEG Audio Stream， Layer III
*.mp4   audio/mp4， video/mp4    MPEG-4 Audio/Video
*.mpeg  video/mpeg  MPEG Video Stream， Layer II
*.mpg   video/mpeg  MPEG Video Stream， Layer II
*.mpp   application/vnd.ms-project  MS Project Project
*.ogg   application/ogg， audio/ogg  Ogg Vorbis
*.pdf   application/pdf Portable Document Format
*.png   image/png   Portable Network Graphics
*.pot   application/vnd.ms-powerpoint   MS PowerPoint Template
*.pps   application/vnd.ms-powerpoint   MS PowerPoint Slideshow
*.ppt   application/vnd.ms-powerpoint   MS PowerPoint Presentation
*.rtf   application/rtf， text/rtf   Rich Text Format
*.svf   image/vnd.svf   Simple Vector Format
*.tif   image/tiff  Tagged Image Format File
*.tiff  image/tiff  Tagged Image Format File
*.txt   text/plain  Plain Text
*.wdb   application/vnd.ms-works    MS Works Database
*.wps   application/vnd.ms-works    Works Text Document
*.xhtml application/xhtml+xml   Extensible HyperText Markup Language
*.xlc   application/vnd.ms-excel    MS Excel Chart
*.xlm   application/vnd.ms-excel    MS Excel Macro
*.xls   application/vnd.ms-excel    MS Excel Spreadsheet
*.xlt   application/vnd.ms-excel    MS Excel Template
*.xlw   application/vnd.ms-excel    MS Excel Workspace
*.xml   text/xml， application/xml   Extensible Markup Language
*.zip   aplication/zip  Compressed Archive
```



