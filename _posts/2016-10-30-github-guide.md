---
layout: post
title: GitHub Command
description: "Some command about github's operation"
tags: [GitHub,Git]
---

**注意几个要点：**
+ 1、origin 、 upsteam的区别
+ 2、fork的项目 和 自己新建的项目 的区别，可以和第1点一起理解
+ 3、更新到本地（commit） 和 推送到远程仓库（push） 的区别
+ 4、fetch 和 pull 的区别

## 命令行

#### 查看远端先有分支
```
$ git remote -v
```

#### 为fork的项目 或者 自己的项目 配置分支
```
$ git remote add upsteam https//github.com/xxx/xxx.git

//upsteam 为分支的名字
```

**这里需要理解 upsteam 和 origin 的区别

#### 更新分支到本地，得与 fetch 做区别
```
$ git remote update
```

#### 获取 upsteam 分支到本地
```
$ git fetch upsteam
```
**这里要理解 fetch 和 pull 的区别：两个都是相当于update代码。但 fetch 是不自动覆盖代码，而 pull 会自动覆盖掉

#### 切换到本地 master 分支
```
$ git checkout master
```

#### 合并分支到本地
```
$ git rebase upsteam/master
```

#### 同步到 主分支 upsteam
这个是指当前的项目是fork别人（简称主任）的，然后你需要把你的修改和主人的项目的分支进行合并：
```
$ git merge upsteam/master
```
**保持良好的习惯，请先fetch了别人的最新的代码，再去把自己的代码和别人的合并！！

#### 配置用户名和邮箱
配置提交时默认使用的用户名和邮箱
```
$ git config --global user.name "your name"
$ git config --global user.email "your email"
```

#### 新建repository初始化
```
$ git init
```

#### 查看当前是否有修改的文件还没推送push或者提交commit
```
$ git status
```

#### add
```
$ git add .
$ git add readme.md
```
**注意这里是add 后面有个 . 小数点，意思是提交全部修改的文件

#### 提交
```
$ git commit -m "注释内容"
```

#### 推送到远端仓库 origin 的 master 分支
```
$ git push origin master
$ git push -u origin master
```
**这一步是指真正的上传，不是commit的提交到本地而已。做这一步，需要保证origin是指向你的本地仓库，要和 upsteam 区别哦；如果没有分支的话，就使用 git remote add origin xxxxx 为项目配置分支。
**需要理解 -u 的含义

#### 查看日志
```
$ git log
```

### 协同工作

#### 创建分支
创建一个叫 myBranchName 的分支
```
$ git branch myBranchName
```

#### 把某个分支作为当前的分支
把 myBranchName 作为当前的分支
```
$ git checkout myBranchName
```

#### 合并多个分支
在当前分支下面，激活另外一个分支，然后再进行合并，合并之后你也可以把这个分支删除掉：
```
$ git checkout master
$ git merge myBranch  // 把 myBranch 和 master 分支合并
$ git branch -d myBranch
```

#### Pull Request
是指向fork的项目的主人发送请求，通知他，我做了你的项目的代码改变，你可以看看。

#### 删除这个项目
Setting -- Delete this repository

#### Git的SSH远程访问的方法：
1、首先在本地创建SSH KEY:
```
$ ssh-keygen -t rsa -C "your email address"
```
后面的邮箱地址改为你的邮箱地址，之后会要求确认路径和输入密码，这里一直使用回车就行了，成功的话会在~/下生成.ssh文件夹，进去，打开id_rsa.pub，复制里面的key。

2、为了验证是否成功，在git bash下输入：
```
$ ssh -T [email]git@github.com[/email]
```
如果是第一次的会提示是否continue，输入yes就会看到：You’ve successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。

3、回到github，进入Account Settings，左边选择SSH Keys，Add SSH Key,title随便填，粘贴key。

4、接下来我们要做的就是把本地仓库传到github上去，在此之前还需要设置username和email（上面已有config配置），因为github每次commit都会记录他们。





#### 查询git版本
```
$ git --version
```

#### 查询git路径
```
$ which git
```

**参考网址：**
+ [https://segmentfault.com/a/1190000003703918](https://segmentfault.com/a/1190000003703918)

+ [http://blog.csdn.net/dongdongdongjl/article/details/8565330](http://blog.csdn.net/dongdongdongjl/article/details/8565330)

+ ````[怎样在github上协同开发](http://blog.csdn.net/koffuxu/article/details/39010803)