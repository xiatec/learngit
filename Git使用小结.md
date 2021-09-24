## Git使用小结

#### 一.创建版本库

初始化一个git仓库

```
git init
```

添加文件到Git仓库

```
git add <file>
git commit -m <message>
```

#### 二.时光机回退

随时掌握工作区状态

```
git status
```

查看修改内容

```
git diff
```

版本回退

```
HEAD指向的版本是当前版本,使用git rest --hard commit_id
穿梭前,使用git log查看提交历史,以确定回退版本
重返未来,git log查看命令历史
```

管理修改

```
每次修改,如果不用git  add到暂存区,那就不会加入commit中
```

撤销修改

```
想直接丢弃工作区修改: git checkout -- file
文件已添加至暂存区,仍想丢弃修改: 1.git rest HEAD <file> 2. 按上一种操作
```

删除文件

```
git rm用于删除一个文件
```

#### 三.远程仓库

创建SSH Key

```
ssh -keygen -t rsa -C "youremail@example.com"
```

添加远程库

```
1.登录Github创建新的repo,填入一个文件名
2.运行命令: git remote add origin git@github.com:xiatec/xxx.git
(添加后,远程库的名字就是origin,是默认叫法)
3.将本地库内容推送到远端: git push -u origin master
4.此后,每次本地库提交后,使用git push origin master推送最新修改
```

克隆仓库

```
git clone , 但必须知道仓科的地址
```

#### 四.分支管理

创建与合并分支

```
查看分支: git branch
创建分支: git branch <name>
切换分支: git checkout <name> or git switch <name>
创建+切换分支: git checkout -b <name> or git switch -c <name>
合并某分支到当前分支: git merge <name>
删除分支: git branch -d <name>
```

解决冲突

```
当git无法自动合并分支时,就必须首先解决冲突,解决冲突后再提交
解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容,再提交
用git log --graph查看分支合并图
```

分支管理策略

```
合并分支时,加上--no-ff参数就可以使用普通模式进行合并,合并后的历史有分支,能看出曾做过合并,而fast forward合并看不出来曾做过合并
```

bug分支

```
修复bug时,通过创建新的bug分支进行修复,然后合并,最后删除
当手头有工作未完成时,先把工作现场git stash一下,然后去修复bug,修复后,再git stash pop,回到工作现场
在master分支上修复的bug,想要合并到当前dev分支,可以用git cherry-pick <commit>,把bug提交的修改复制到当前分支,避免重复劳动
```

Feature分支

```
开发一个新的feature,最好新建一个分支
如果要丢弃一个没有合并过的分支,通过git branch -D <name>强行删除
```

多人协作

```
查看远程库信息,使用git remote -v

本地新建的分支如果不推送到远程,其他人是看不见的

从本地推送分支,使用git push origin branch-name,如果推送失败,先git pull抓取远程的新提交

从本地创建和远程分支对应的分支,使用git checkout -b branch-name origin /branch-name,本地和远程分支名称尽量一致

建立本地和远程分支的关联,使用git branch --set-upstream branch-name origin/branch-name

从远程抓取分支,使用git pull,有冲突则先处理冲突

```



