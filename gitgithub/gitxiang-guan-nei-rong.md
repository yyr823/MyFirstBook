#### [集中式vs分布式](#集中式vs分布式) {#集中式vs分布式}

#### [安装Git](#安装git)

#### [版本库（Repository）](#版本库（repository）)

#### [远程仓库](#远程仓库)

#### [分支管理](#分支管理)

#### [注意小结](#注意小结)

####  {#u}

#### 集中式vs分布式 {#集中式vs分布式}

1. 集中式开发：是将项目集中存放在中央服务器中，在工作的时候，大家只在自己电脑上操作，从同一个地方下载最新版本，然后开始工作，做完的工作再提交给中央服务器保存。这种方式需要联网.

![](/assets/import1.png)

2.分布式开发：通常也有一台充当“中央服务器”的电脑，但这个服务器的作用仅仅是用来方便“交换”大家的修改，没有它也一样干活，只是交换修改不方便而已。而每一台电脑有各自独立的开发环境\(每个人电脑里都有完整的版本库，某一个人的电脑坏掉了不要紧，随便从其他人那里复制一个就可以了\)，不需要联网，本地直接运行，相对集中式安全系数高很多。

#### ![](/assets/import2.png)

#### 安装Git {#安装git}

最早Git是在Linux上开发的，很长一段时间内，Git也只能在Linux和Unix系统上跑。不过，慢慢地有人把它移植到了Windows上。现在，Git可以在Linux、Unix、Mac和Windows这几大平台上正常运行了。要使用Git，第一步当然是安装Git了.

* #### 在Linux上安装Git

首先，你可以试着输入`git`，看看系统有没有安装Git：

```
$ git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
```

像上面的命令，有很多Linux会友好地告诉你Git没有安装，还会告诉你如何安装Git。

如果你碰巧用Debian或Ubuntu Linux，通过一条`sudo apt-get install git`就可以直接完成Git的安装，非常简单。

老一点的Debian或Ubuntu Linux，要把命令改为`sudo apt-get install git-core`，因为以前有个软件也叫GIT（GNU Interactive Tools），结果Git就只能叫`git-core`了。由于Git名气实在太大，后来就把GNU Interactive Tools改成`gnuit`，`git-core`正式改为`git`。如果是其他Linux版本，可以直接通过源码安装。先从Git官网下载源码，然后解压，依次输入：`./config`，`make`，`sudo make install`这几个命令安装就好了。

* #### 在Mac OS X上安装Git

如果你正在使用Mac做开发，有两种安装Git的方法。

一是安装homebrew，然后通过homebrew安装Git，具体方法请参考homebrew的文档：[http://brew.sh/](http://brew.sh/)。

第二种方法更简单，也是推荐的方法，就是直接从AppStore安装Xcode，Xcode集成了Git，不过默认没有安装，你需要运行Xcode，选择菜单“Xcode”-&gt;“Preferences”，在弹出窗口中找到“Downloads”，选择“Command Line Tools”，点“Install”就可以完成安装了。

![](https://www.liaoxuefeng.com/files/attachments/919018691743136/0 "install-git-by-xcode")

Xcode是Apple官方IDE，功能非常强大，是开发Mac和iOS App的必选装备，而且是免费的！

* #### 在Windows上安装Git

在Windows上使用Git，可以从Git官网直接[下载安装程序](https://git-scm.com/downloads)，（网速慢请移步[国内镜像](https://pan.baidu.com/s/1kU5OCOB#list/path=%2Fpub%2Fgit)），然后按默认选项安装即可。

安装完成后，在开始菜单里找到“Git”-&gt;“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

![](https://www.liaoxuefeng.com/files/attachments/919018718363424/0 "install-git-on-windows")

安装完成后，还需要最后一步设置，在命令行输入：

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：**你的名字和Email地址**。你也许会担心，如果有人故意冒充别人怎么办？这个不必担心，首先我们相信大家都是善良无知的群众，其次，真的有冒充的也是有办法可查的。

注意`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

#### 版本库（Repository） {#版本库（repository）}

工作区有一个隐藏目录`.git`，这个不算工作区\(当前项目\)，而是Git的版本库\(这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”.\)

Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。

![](/assets/import.png)

我们把文件往Git版本库里添加的时候，是分两步执行的：

第一步是用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；

第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一个`master`分支，所以，现在，`git commit`就是往`master`分支上提交更改。

你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

#### 远程仓库 {#远程仓库}

只要注册一个GitHub账号，就可以免费获得Git远程仓库.

由于你的本地Git仓库和GitHub仓库之间的传输是通过SSH加密的，所以，需要一点设置：

第1步：创建SSH Key。在用户主目录\(在windows中就是 C:\Users\Administrator\，或者你新建了一个用户，那就是 C:\Users\用户名\\)下，看看有没有.ssh目录，如果有，再看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

```
$ ssh-keygen -t rsa - C "youremail@example.com"
```

你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。如果一切顺利的话，可以在用户主目录里找到`.ssh`目录，里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是SSH Key的秘钥对，`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥，可以放心地告诉任何人。

第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：

然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴`id_rsa.pub`文件的内容：

![](https://www.liaoxuefeng.com/files/attachments/919021379029408/0 "github-addkey-1")

点“Add Key”，你就应该看到已经添加的Key：

![](https://www.liaoxuefeng.com/files/attachments/919021395420160/0 "github-addkey-2")

为什么GitHub需要SSH Key呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。

当然，GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。最后友情提示，在GitHub上免费托管的Git仓库，任何人都可以看到喔（但只有你自己才能改）。所以，不要把敏感信息放进去。

#### 分支管理 {#分支管理}

1. ##### [**每次提交**](/ http://liaoxuefeng.gitee.io/git-resources/master-branch-forward.mp4)
2. ##### [创建与合并分支](https://liaoxuefeng.gitee.io/git-resources/master-and-dev-ff.mp4)

#### 注意小结 {#注意小结}

1. Git管理的是修改，而不是文件

2. 每次修改，如果不用`git add`到暂存区，那就不会加入到`commit`中

3. 合并分支时，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并就看不出来曾经做过合并

4. 多人协作的工作模式通常是这样：

   1. 首先，可以试图用`git push origin <branch-name>`推送自己的修改

   2. 如果推送失败，则因为远程分支比你的本地更新，需要先用`git pull`试图合并

   3. 如果合并有冲突，则解决冲突，并在本地提交

   4. 没有冲突或者解决掉冲突后，再用`git push origin <branch-name>`推送就能成功

   5. 如果`git pull`提示`no tracking information`，则说明本地分支和远程分支的链接关系没有创建，用命令`git branch --set-upstream-to= origin/<branch-name> <branch-name>`

5. 标签总是和某个commit挂钩。如果这个commit既出现在master分支，又出现在dev分支，那么在这两个分支上都可以看到这个标签

6. 忽略某些文件时，需要编写`.gitignore`该文件本身要放到版本库里，并且可以对`.gitignore`做版本管理

7. 配置Git的时候，加上`--global`是针对当前用户\(用户主目录下.gitconfig文件\)起作用的，如果不加，那只针对当前的仓库起作用。每个仓库的Git配置文件都放在`.git/config`文件中



