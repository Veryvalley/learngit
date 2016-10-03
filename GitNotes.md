## 撤消单个文件修改相关操作
- git checkout -- filename // 注意 “--” 不能少，否则就是切换分支的命令了。用仓库中的文件替换工作区的文件，但是如果工作区的文件已经add到缓存区，只是没有commit的话，工作区的文件不会被仓库中的文件替换，如果需要替换先用git reset HEAD filename，再用git checkout --file命令
- git reset HEAD filename  // 用仓库中的当前版本替换缓存区的文件，但是工作区的文件不变,要想工作区的文件与仓库一样，再用 git chekout -- file命令

## 将工作区恢复到某个时刻(提交,commit)\
- git reset --hard commit_id // HEAD表示当前版本,HEAD^表示当前版本的前一个版本，HEAD^^当前版本的前两个版本。。。
- git log  // 查看当前版本的之前(包含当前版本)的提交记录
- git reflog // 查看git命令历史，可以用来回到当前版本之后的某个时刻。
