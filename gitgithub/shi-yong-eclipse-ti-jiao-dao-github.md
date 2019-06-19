> #### 原文链接

* #### [小白使用eclipse提交到GitHub \(详细步骤\)](https://blog.csdn.net/bendanany/article/details/78891804)
* [x] 首先登陆GITHub创建一个新的repository \(Start a project\),复制地址备用。`https://github.com/xxxx/TestDemo.git`

**注意,红色标识部分不要勾选,否则后续提交代码时会出现冲突。**

![](/assets/g1.png)

* [x] Eclipse:**项目名称必须与git中一致**

Eclipse 高级版本自带Git,不需要安装插件。\(如使用低级版本,请自己百度安装Git插件\)

将本地项目上传到Git,**流程：需要先通过Commit 传到本地仓库,然后再从本地仓库push到Git。**

* [x] 实例：

* 项目右键,Team -&gt; Share Project

![](/assets/g2.png)

* 选择Git,随后配置GIT, Configure Git Repository

![](/assets/g3.png)

**在此目录下会生成一个.git 的文件夹,此时Eclipse中文件显示?号。**

* 为新建的文件添加Index, 右键项目-＞Team-&gt;Add to Index, 这里将所有文件会带个+号, 对于不需要提交的文件,可以通过右键-&gt;Team-&gt;Remove from Index 移除。

* 提交代码到本地仓库

右键项目-&gt;Team-&gt;Commit,  add commit message, 如果遇到下面这种情况,先去Window-&gt;Preference-&gt;Team-&gt;Git-&gt;Committing, 将第一个默认勾选去掉。

![](/assets/g5.png)![](/assets/g6.png)

以下面作为参考提交:

![](/assets/g7.png)

注意,代码只需要提交图片中标识的文件即可。也可以通过编辑.gitignore将不需要提交的文件筛除。

例如:使用Notepad输入需要忽略的文件或文件名,如下所示：

\#\#ignore this file\#\#

/target/

.classpath

.project

.settings

commit后, 这时,可以看到文件带有圆柱形标志。

![](/assets/k10.png)

* 从本地代码提交到Git

项目右键,Team-&gt;Remote-&gt;Push, 输入Git地址,以及登陆凭证

![](/assets/g8.png)

点击Next,Source ref和Destination ref下拉框中选择master,点击Add Spec,点击Next。

![](/assets/g9t.png)

* 项目提交到Git成功

![](/assets/g10.png)

* 打开GitHub,查看是否项目是否上传成功。



