## 撤消单个文件修改相关操作
- git checkout -- filename // 注意 “--” 不能少，否则就是切换分支的命令了。用仓库中的文件替换工作区的文件，但是如果工作区的文件已经add到缓存区，只是没有commit的话，工作区的文件不会被仓库中的文件替换，如果需要替换先用git reset HEAD filename，再用git checkout --file命令
- git reset HEAD filename  // 用仓库中的当前版本替换缓存区的文件，但是工作区的文件不变,要想工作区的文件与仓库一样，再用 git chekout -- file命令

## 将工作区恢复到某个时刻(提交,commit)
- git reset --hard commit_id // HEAD表示当前版本,HEAD^表示当前版本的前一个版本，HEAD^^当前版本的前两个版本。。。
- git log  // 查看当前版本的之前(包含当前版本)的提交记录
- git reflog // 查看git命令历史，可以用来回到当前版本之后的某个时刻。


## 提交
- commit -m'' // commit的作用是把`暂存区(stage)`的`所有修改`，一次性全部提交到仓库的`当前分支`。

## 删除
- git rm 相当于 rm filename + git add filename

## 远程仓库
- $ ssh-keygen -t rsa -C "youremail@example.com"   // 创建ssh key ，先cd ~ 再cd .ssh ,再cat *.pub查看ssh key
- git remote add origin git@server-name:path/repo-name.git // 将本地仓库和远程仓库关联 ，origin是给远程仓库起的名字，可以自己定义，默认是origin.
- git push -u origin master //第一次推送master分支的所有内容,以后推送本地仓库的内容不用 -u 
