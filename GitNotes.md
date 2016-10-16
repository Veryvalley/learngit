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

## 分支管理
- 严格意义上讲，HEAD是指向当前分支的，而分支是指向某一个提交的。
- 查看分支：git branch
- 创建分支：git branch <name>
- 切换分支：git checkout <name>
- 创建+切换分支：git checkout -b <name>
- 合并某分支到当前分支：git merge <name>
- 删除分支：git branch -d <name>

- git merge --no-ff -m "..." dev //将dev分支合并到当前分支。禁用Fast forward模式，Git就会在merge时生成一个新的commit，所以要注释-m''
- git log --graph --pretty=oneline --abbrev-commit // 可以看到分支的合并过程

## 多人协作
- 查看远程库信息，使用git remote -v；
- 本地新建的分支如果不推送到远程，对其他人就是不可见的；
- 从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；
- 在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；
- 建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；
- 从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。

## 放弃本地修改，强制更新
```
git fetch --all
git reset --hard origin/master
// git fetch 只是下载远程的库的内容，不做任何的合并 git reset 把HEAD指向刚刚下载的最新的版本
```
