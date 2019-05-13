| 语法 | 描述 |
| :--- | :--- |
| git status | 掌握仓库当前的状态 |
| git diff  fileName | 查看文件内容不同之处 |
| git add fileName | 把文件添加到仓库 |
| git commit -m '备注信息' | 告诉git把文件提交到仓库 |
| git log | 显示从最近到最远的提交日志 |
| git log --pretty=oneline | 简化日志信息输出 |
| git reset --head HEAD^ | 把当前最新的提交回退上一个版本 |
| git reset --hard  1094a\(commit id前几位\) | 指定回到所填写 的版本处 |
| cat fileName | 查看文件内容 |
| git reflog | 查看记录日志（命令历史） |

文件名称+后缀：fileName

#### 版本库（Repository）

工作区有一个隐藏目录`.git`，这个不算工作区，而是Git的版本库。

Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。

![](/assets/import.png)

我们把文件往Git版本库里添加的时候，是分两步执行的：

第一步是用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；

第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一个`master`分支，所以，现在，`git commit`就是往`master`分支上提交更改。

你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

