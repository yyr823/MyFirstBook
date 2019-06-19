> #### 原文链接

* #### [小白使用eclipse提交到GitHub \(详细步骤\)](https://blog.csdn.net/bendanany/article/details/78891804)
* #### [Eclipse生成SSH传输密钥并实现GitHub的SSH代码提交](https://blog.csdn.net/u014745069/article/details/79839202)\(部分参考\)
* #### [Eclipse使用egit插件通过ssh协议方式上传代码到gitLab](http://www.manongjc.com/article/32398.html)\(部分参考\)
* [x] 首先登陆GitHub创建一个新的repository \(Start a project\),复制地址备用。

**注意,红色标识部分不要勾选,否则后续提交代码时会出现冲突。**

![](/assets/g1.png)

* [x] Eclipse:**项目名称必须与git中一致**

Eclipse 高级版本自带Git,不需要安装插件。\(如使用低级版本,请自己百度安装Git插件\)

将本地项目上传到Git,**流程：需要先通过Commit 传到本地仓库,然后再从本地仓库push到Git。**

> #### 以https协议方式上传项目代码

`https://github.com/xxxx/TestDemo.git`

* [x] 项目右键,Team -&gt; Share Project\(项目提交通用\)

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

commit后, 这时,可以看到文件带有圆柱形标志。

![](/assets/k10.png)

* 从本地代码提交到Git

项目右键,Team-&gt;Remote-&gt;Push, 输入Git地址,以及登陆凭证

![](/assets/g8.png)

* [x] 点击Next,Source ref和Destination ref下拉框中选择master,点击Add Spec,点击Next。

![](/assets/g9t.png)

* 项目提交到Git成功

![](/assets/g10.png)

* 打开GitHub,查看是否项目是否上传成功。

> #### 以ssh协议方式上传项目代码

使用ssh方式可以不通过https协议,避免直接提供账号密码的方式上传项目到git在线服务器,如GitLab、Bitbucket、GitHub,同时极其可靠的保证账号安全性。

**操作步骤：**

* [x] Window-&gt;preferences-&gt;General-&gt;Network Connections-&gt;SSH2

* [x] 切换到Key Management页,选择点击 Generate DSA key 或 Generate RSA key 按钮,生成DSA或RSA算法的密钥,原则上是DSA或RSA都受支持的,个人感觉DSA甚至更好,毕竟两者中,DSA被美国NIST挑选作为数字签名标准,但是RSA在百度搜索出的纵多博文中被使用。

* [x] 生成了看上去满意的密钥后,填写Comment简要注释,填写Passphrase\(可选填项,相当于password,用于加密保护私钥,填写后每次上传服务器,将要求提供此密码验证私钥的使用权\),点击SavePrivateKey。

![](/assets/k12.png)如果之前已经生成文件,可重新定义文件位置或者进行覆盖。其中,id\_rsa代表非对称加密算法rsa的私钥,id\_rsa.pub代表公钥,私钥是需要自己保管的,而公钥可以任意发送给他人保管,这是为了让remote用户能够判断传输的加密数据是否为本人操作。

![](/assets/k13.png)

* [x] 【**关键步骤**】点击 Export Via SFTP ,按 user@host\[:port\] 形式输入公钥绑定的服务器域,如 git@bitbucket.org 或 git@github.com \(输入刚才的Passphrase,点击各种确定,ps:我绑定时没出现,如果报出 Failed to export ssh key to remote server 的错误,直接忽略\)**注意:push的时候报出 The authenticity of host 'github.org' can't be established. 之类的错误,阻止上传,基本都是没执行这一步的原因。**

* [x] 点击 Load Existing Key,选择刚才生成的私钥\(id\_rsa文件\),输入Passphrase,点击Apply。

* [x] 点击旁边的Known Hosts,应该能看到刚才绑定的服务器记录。

* [x] 返回General,确认Private keys中包含了刚才保存的私钥件id\_rsa,**没包含的话点击旁边的Add Private Key..添加进去**,最后点击Apply\(SSH2 home位置,用于存储SSH协议使用的非对称加密密钥文件\)

![](/assets/k11.png)

* [x] 最好重启一次Eclipse

* [x] 把生成的公钥\(刚才生成密钥的时候显示的那一串东西或者打开刚才生成的id\_rsa.pub文件将里面的内容全部复制下来\)绑定到git服务器上。

* [x] 添加GitHub公钥

![](/assets/k14.png)

![](/assets/k15.png)

![](/assets/k16.png)

![](/assets/k17.png)

* [x] elipse代码提交如上,只需更改路径,其余跟https提交代码一致,不需要再输入密码。

![](/assets/k18.png)

