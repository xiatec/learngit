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



