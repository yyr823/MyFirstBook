#### HTML5文档有如下结构

```HTML
<!DOCTYPE html>
<html>
    <head>
    <meta charset="UTF-8">
    <title>页面标题</title>
    </head>
    <body>
    页面内容
    </body>
</html>
```

* **注意:**

* [x] **不要在**`<html>`**和**`<head>`**之间插入任何内容**

* [x] **不要在**`<head>`**和**`<body>`**之间插入任何内容**

* [x] **不要在**`<body>`**和**`<html>`**之间插入任何内容**

> #### HTML5语法变化

* **标签不区分大小写**
* **元素可以省略结束标签**
* **允许省略属性的属性值**
* **允许属性不使用引号**

* **提示:**

**HTML5的语法变化主要是为兼容互联网上成千上万的不遵守HTML语法规范的网站,所以可以认为HTML5制定的是一种”妥协式”的规范.     **

> #### 新增的常用语义性元素

| mark | 定义带有记号的文本,需要突出显示文本时使用&lt;mark&gt;标签 |
| :---: | :--- |
| progress | 标签定义运行中的任务进度\(进程\)  |
| time | 表示时间日期值 |
| details     | 此标签规定了用户可见的或者隐藏的需求的补充细节 |
| datalist    | 定义选项列表。请与input元素配合使用该元素,来定义input可能的值。 |
| ruby | 此标签定义 ruby注释,往往与&lt;rt&gt;和&lt;rp&gt;标签一起配合使用 |
| menu | 表示菜单列表 |
| command  | 可以定义用户可能调用的命令\(比如单选按钮、复选框或按钮\) |

> #### 新增的结构性元素

| section | 定义文档中的节。比如章节、页眉、页脚或文档中的其它部分。一般用于成节的内容, 会在文档流中开始一个新的节 |
| :---: | :--- |
| article | 它是一个特殊的sect i on标签, 它比sect i on具有更明确的语义, 它代表一个独立的,完整的相关内容块, 可独立于页面其它内容使用 |
| nav | 此标签代表页面的一个部分, 表示页面中导航链接的部分 |
| aside | 它用来装载非正文的内容, 被视为页面里面一个单独的部分。它包含的内容与页面的主要内容是分开的, 可以被删除, 而不会影响到网页的内容、章节或是页面所要传达的信息 |
| hgroup | 是对网页或区段section的标题元素 \(h1-h6\) 进行组合 |
| footer | 它定义section或文档的页脚, 包含了与页面、 文章或是部分内容有关的信息 |
| header | 定义文档的页眉, 通常是一些引导和导航信息。它不局限于写在网页头部, 也可以写在网页内容里面 |
| figure | 用于对元素进行组合。多用于图片与图片描述组合 |

> #### 新增的input输入类型

| list  | 属性引用&lt;datalist&gt;元素,其中包含&lt;input&gt;元素的预定义选项 |
| :---: | :--- |
| 新增的miN,max和step属性 | min:规定输入框所输入的最小值,max:规定输入框所输入的最大值,step:为输入框规定合法的数字间隔 |
| multiple | 属性规定允许用户输入到 &lt;input&gt; 元素的多个值 |
| pattern | 规定用于验证 &lt;i nput&gt; 元素的值的正则表达式 |
| pIaceholder | 规定可指述输入&lt;input&gt; 字段预期值的简短的提示信息 |
| required | 规定必需在提交表单之前填写输入字段 |
| autocomptete | 规定&lt;input&gt;元素输入字段是否应该启用自动完成功能 |
| autofocus | 规定当页面加载时&lt;input&gt;元素应该自动获得焦点 |
| form  | 规定 &lt;input&gt; 元素所属的一个或多个表单 |
| **formaction** | 规定当表单提交时处理输入控件的文件的 url |
| **formenctype** | 规定当表单数据提交到服务器时如何编码 |
| **formmethod** | 定义发送表单数据到 actionURL的 HTTP方法 |
| **formtarget** | 规定表示提交表单后在哪里显示接收到响应的名称或关键词 |
| **formnovalidate** | 覆盖&lt;form&gt;元素的写属性novalidate属性 |
| **除了formnovalidate属性** | **其它属性都是只针对 type="submit"和 type="image" ** |
| 新增的height和width属性 | 规定&lt;input&gt;元素的高度\(只针对type="image"\) |
| email | 定义用于 email地址的字段 |
| url | 定义用于输入 URL的字段 |
| number | 定义用于输入数手的手段 |
| range | 定义用于精确值不重要的输入数手的控件 |
| Date Pickers | 定义 date控件。month:定义 month和 year控件\(不带时区\) 。 week:定义 week和 year控件。 time:定义用于输入时间的控件。 datetime:定义 date和 time控件,基于uTC时区。datetime-looal:定义 date和 time控件,  不带时区 |
| search | 定义用于输入捜索字符串的文本字段 |
| tel | 定义用于输入电话号码的字段 |
| color | 定义拾色器 |

> #### HTML5废除的相关元素

* 能用css代替的元素,  比如:basefont、 big、 center、 font、 s、strike、 tt、 u。

* 不再使用frame框架, frameset、 frame、 noframes。 HTML5中不支持frame框架, 只支持 iframe框架 。

* 只有部分刘览器支持的元素, applet、 bgsound、 bl ink、 marquee等标签。

* 其他被废除的元素, 比如:废除rb使用ruby替代、废除acronym使用abbr替代、废除dir使用ul替代、废除listing使用pre替代等。



