感谢廖雪峰老师的Git教程。

- 配置全局用户及邮箱（安装Git之后的最后一步）
```
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```
- 配置当前仓库用户及邮箱
```
git config user.name "Your Name"
git config user.email "email@xx.com"
```
- 创建版本库repository（可理解为目录,pwd可查看当前目录）
```
git mkdir repo_name
cd repo_name
pwd 
```
- 初始化版本库（把这个目录变成Git可以管理的仓库，此时多了一个.git的隐藏目录，使用ls -ah可查看所含文件）
```
git init  
ls -ah
```
- 把写好的xx.txt文件放到 git 仓库（分两步）
```
git add XX.txt  #把文件修改添加到暂存区
git commit -m "xxx"  #把暂存区的所有内容提交到当前分支
```
- 查看当前仓库状态
```
git status
```
- 查看文件修改的内容
```
git diff <file>
```
> 补充
```
git diff    #是工作区(work dict)和暂存区(stage)的比较
git diff --cached    #是暂存区(stage)和分支(master)的比较
git diff HEAD  #查看工作区和版本库里面最新版本的区别
```
- 查看提交日志
```
git log  #显示从最近到最远的提交日志
git log --pretty=oneline #HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，上100个版本是HEAD~100
```
- 版本回退到上一个版本，并查看当前文件内容
```
git reset --hard HEAD^
git reset --hard 3628164  #3628164为commit id（版本号）
cat xx.txt
```
- 查看命令日志（从建库对这个版本的所有操作记录），以便知道版本号
```
git reflog
```
- 丢弃工作区修改
```
git checkout -- xx.txt
```
- 撤销暂存区修改
```git
git reset HEAD file
```
- 删除暂存区文件
```
git rm <file>
git commit -m "xxxx"
```
- 从暂存区恢复删除文件
```
git checkout --<file>
```
- 创建一个ssh key
```
ssh-keygen -t rsa -C "email@example.com"
```
- 关联远程仓库
```
git remote add origin git@server-name:path/repo-name.git
```
- 首次 push 到远程仓库(当前分支master推送到远程)
```
 git push -u origin master 
```
- 非首次推送到远程仓库(推送最新修改)
```
git push origin master 
```
- 从远程仓库克隆到本地库
```
git clone git@server-name:path/repo-name.git
```
- 分支管理
```
查看分支：git branch
创建分支：git branch <name>
切换分支：git checkout <name>
创建+切换分支：git checkout -b <name>
合并某分支到当前分支：git merge <name>
删除分支：git branch -d <name>
查看分支合并图：git log --pretty=oneline --abbrev-commit
```
- 禁止使用 fast forward merge（快进模式） 方式(--no-ff参数，表示禁用Fast forward)
```
git merge --no-ff -m "xxx"  <branch name>
```
- 隐藏现场及回复现场
```
git stash #保存现场
git stash list  #查看现场
git stash apply #恢复现场，stash内容并不删除，需要用git stash drop来删
git stash pop #恢复现场，stash内容也删了，再用git stash list查看，就看不到任何stash内容
```
- 强制删除未合并分支
```
git branch -D <branch name>
```
- 多人协作
```git
git remote #查看远程库信息
git remote -v #查看远程库信息详细
git push origin master #推送本地 master 分支
git checkout -b dev origin/dev #创建本地 dev 并关联远程 dev 分支
git branch --set-upstream branch-name origin/branch-name #建立本地分支与远程分支得关联
git pull #抓取远程分支
```
- 创建标签
```
git tag <name>  #创建标签
git tag #查看所有标签
git tag v0.9 6224937 #对某一次 commit 打标签
git show <tagname> #查看标签信息
git tag -a v0.1 -m "version 0.1 released" 3628164 #创建有说明的标签
```
- 操作标签
```
git tag -d v0.1 #删除标签
git push origin <tagname> #推送标签到远程
git push origin --tags #推送本地所有未推送到远程的标签
git push origin :refs/tags/<tagname> #删除远程标签
```
- 自定义git别名
```
git config --global color.ui true #配置颜色开启
git config --global alias.st status #st表示status
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.br branch
git config --global alias.unstage 'reset HEAD'
git config --global alias.last 'log -1'
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit" #一个丧心病狂地的lg配置
git config --global core.quotepath false # 设置显示中文文件名
```

以上，欢迎大家继续添加~







