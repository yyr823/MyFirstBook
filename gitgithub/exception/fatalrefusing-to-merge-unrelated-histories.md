#### fatal:refusing to merge unrelated histories\(拒绝合并不相关的历史\)

* [x] 原因:两个 根本不相干的 git 库, 一个是本地库,一个是远端库, 然后本地要去推送到远端, 远端觉得这个本地库跟自己不相干, 所以告知无法合并

* [x] 解决办法:

* 从远端库clone项目\(test\)到本地 ,本地把要加入的代码放到本地的库\(test\)下, 然后再提交上去

* git pull origin master --allow-unrelated-histories  \(把两段不相干的 分支进行强行合并\)



