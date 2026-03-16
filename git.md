# 01 基础指令



 初始化

git init

查看状态（以及历史提交）

git status

添加工作区到暂存区

提交

git commit -m "(标记)"

提交到哪

git log

![image-20260313092028990](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260313092028990.png)

# 02 常见指令

###### 3.3.1、*查看修改的状态（status）

作用：查看的修改的状态（暂存区、工作区）
命令形式：git status

###### 3.3.2、*添加工作区到暂存区(add)

作用：添加工作区一个或多个文件的修改到暂存区
命令形式：git add 单个文件名|通配符
将所有修改加入暂存区：git add .

###### 3.3.3、*提交暂存区到本地仓库(commit)

作用：提交暂存区内容到本地仓库的当前分支
命令形式：git commit -m '注释内容'

###### 3.3.4、*查看提交日志(log)

在3.1.3中配置的别名 git-log 就包含了这些参数，所以后续可以直接使用指令 git-log 作用:查看提交记录
命令形式：git log [option]
options
--all 显示所有分支
--pretty=oneline 将提交信息显示为一行
--abbrev-commit 使得输出的commitId更简短 

--graph 以图的形式显示

###### git-log的配置

1. 打开用户目录，创建.bashrc文件
部分windows系统不允许用户创建点号开头的文件，可以打开gitBash,执行 touch ~/.bashrc

![image-20260316155816560](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316155816560.png)

2. 在.bashrc文件中输入如下内容：

![image-20260316155835346](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316155835346.png)

3. 打开gitBash，执行 source ~/.bashrc

![image-20260316155853133](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316155853133.png)

###### 3.3.5、版本回退

作用：版本切换
命令形式：git reset --hard commitID
commitID 可以使用 git-log 或 git log 指令查看 如何查看已经删除的记录？

clear之后，之前reset之后的提交记录就删除了

git reﬂog
这个指令可以看到已经删除的提交记录

![image-20260313084553605](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260313084553605.png)

###### 3.3.6、添加文件至忽略列表

一般我们总会有些文件无需纳入Git 的管理，也不希望它们总出现在未跟踪文件列表。 通常都是些自动 生成的文件，比如日志文件，或者编译过程中创建的临时文件等。 在这种情况下，我们可以在工作目录 中创建一个名为 .gitignore 的文件（文件名称固定），列出要忽略的文件模式。下面是一个示例：

# 03 分支

几乎所有的版本控制系统都以某种形式支持分支。 使用分支意味着你可以把你的工作从开发主线上分离
开来进行重大的Bug修改、开发新的功能，以免影响开发主线。

###### 3.4.1、查看本地分支

命令：git branch

###### 3.4.2、创建本地分支

命令：git branch 分支名

###### 3.4.4、*切换分支(checkout)

命令：git checkout 分支名
我们还可以直接切换到一个不存在的分支（创建并切换）
命令：git checkout -b 分支名

###### 3.4.6、*合并分支(merge)

一个分支上的提交可以合并到另一个分支
命令：git merge 分支名称

###### 3.4.7、删除分支

不能删除当前分支，只能删除其他分支
git branch -d b1 删除分支时，需要做各种检查
git branch -D b1 不做任何检查，强制删除

###### 3.4.8、解决冲突

当两个分支上对文件的修改可能会存在冲突，例如同时修改了同一个文件的同一行，这时就需要手动解
决冲突，解决冲突步骤如下：

1. 处理文件中冲突的地方

2. 将解决完冲突的文件加入暂存区(add)

3. 提交到仓库(commit)
  黑马程序员 北京昌平校区
    冲突部分的内容处理如下所示：

###### 3.4.9、开发中分支使用原则与流程

  几乎所有的版本控制系统都以某种形式支持分支。 使用分支意味着你可以把你的工作从开发主线上分离
  开来进行重大的Bug修改、开发新的功能，以免影响开发主线。
  在开发中，一般有如下分支使用原则与流程：
  master （生产） 分支
  线上分支，主分支，中小规模项目作为线上运行的应用对应的分支；
  develop（开发）分支
  是从master创建的分支，一般作为开发部门的主要开发分支，如果没有其他并行开发不同期上线
  要求，都可以在此版本进行开发，阶段开发完成后，需要是合并到master分支,准备上线。
  feature/xxxx分支
  从develop创建的分支，一般是同期并行开发，但不同期上线时创建的分支，分支上的研发任务完
  成后合并到develop分支。
  hotfix/xxxx分支，
  黑马程序员 北京昌平校区
  从master派生的分支，一般作为线上bug修复使用，修复完成后需要合并到master、test、
  develop分支。
  还有一些其他分支，在此不再详述，例如test分支（用于代码测试）、pre分支（预上线分支）等
  等。

![image-20260313112021010](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260313112021010.png)

# 04 git远程仓库

## 4.4、配置SSH公钥

生成SSH公钥
ssh-keygen -t rsa
不断回车
如果公钥已经存在，则自动覆盖
Gitee设置账户共公钥
获取公钥
cat ~/.ssh/id_rsa.pub

### 生成isa： ssh-keygen -t rsa

### isa位置：/Users/liutianming/.ssh/id_rsa



Last login: Fri Mar 13 09:50:38 on ttys000

liutianming@PeterLiuMacBook-Air ~ % ssh-keygen -t rsa

Generating public/private rsa key pair.

Enter file in which to save the key (/Users/liutianming/.ssh/id_rsa): 

Enter passphrase for "/Users/liutianming/.ssh/id_rsa" (empty for no passphrase): 

Enter same passphrase again: 

Your identification has been saved in /Users/liutianming/.ssh/id_rsa

Your public key has been saved in /Users/liutianming/.ssh/id_rsa.pub

The key fingerprint is:

SHA256:Jqliaa8q+s/Yr9dJsFRJDRZXXcQPI3Vj9VUkp7ke/0g liutianming@PeterLiuMacBook-Air.local

The key's randomart image is:

+---[RSA 3072]----+

|    .==...ooB%|

|    .o.. . =*=|

|    .   .ooo|

|   o.    ..|

|   .ooS   o |

|  . ..o.  . o |

| = . o .  E .|

|.o * . o  . ..|

|=o+o*+.    . .|

+----[SHA256]-----+

### 查看isa：cat ~/.ssh/id_rsa.pub

liutianming@PeterLiuMacBook-Air ~ % cat ~/.ssh/id_rsa.pub

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC7GeWOxew7NkZHcoi/liXo7qthAlYQbqYEpurssz/RB/vSwtUwL8VIE2/C/RxWsyhO/2PuXOj3re7V+w3cd6P8QCknoKU5ewoJ2IoGO0ex5kpPQ2eISzkJBhgCtb/QYwJyzpVgYDkA7ltPxwX17qC5ba1doUNSpqtTLAf7rjNk5MFQA1+DUAmMSyNQMD5zCCTRGU5sfHz65zJHm3uLXFZa/CXIpyE6oWbyu0iTZO/xglzxYaHlDzLHoI2tDW/x3+b6mgtAcWg+HNR2Ypy4g3p5YP4XqZQ4GhbgC+CW5pNEw8NLrkD06HCFtyVvsLQvr8DrT4whqdKmGugwV0LdDy5hDJDvZl5r2Gf6N2XpAvDgzoqIBVn7JJtSyAnL8GaWWGjdxnAoo4TMWnn5Ll2vgsdM/ciSzYGo7otO86U0wLX5txqx5vrCCnOjb/D+xCK1u8lm4Jyl97vd/6GjtZCv2/EIy1REq5rvO3jUTTB1MzxZ6qFJ4nJAnOGRZXayiBDqbzM= liutianming@PeterLiuMacBook-Air.local

liutianming@PeterLiuMacBook-Air ~ % 

### 通过SSH连接测试公钥配置是否正确：

liutianming@PeterLiuMacBook-Air ~ % ssh -T git@github.com

Hi liutianming0703! You've successfully authenticated, but GitHub does not provide shell access.

liutianming@PeterLiuMacBook-Air ~ % 

### 远程仓库

#### 新建远程仓库仓库

git@github.com:liutianming0703/repo.git

![image-20260316142401463](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316142401463.png)

#### 添加远程仓库

 git remote add origin git@github.com:liutianming0703/repo.git

![image-20260316145100766](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316145100766.png)



 #### git remote add <远端名称> <仓库路径>
远端名称，默认是origin，取决于远端服务器设置
仓库路径，从远端服务器获取此URL

git remote add origin git@github.com:liutianming0703/repo.git

#### 查看远程仓库
命令：git remote



#### 推送到远程仓库
命令：git push [-f] [--set-upstream] [远端名称 [本地分支名][:远端分支名] ]
如果远程分支名和本地分支名称相同，则可以只写本地分支
git push origin master
-f 表示强制覆盖
--set-upstream 推送到远端的同时并且建立起和远端分支的关联关系。
git push --set-upstream origin master
如果当前分支已经和远端分支关联，则可以省略分支名和远端名。
git push 将master分支推送到已关联的远端分支。



git push --set-upstream origin master:master    只需要第一次执行

git push     之后执行这个

![image-20260316151733314](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316151733314.png)

git branch -vv    显示对应关系

![image-20260316151427071](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316151427071.png)

图代表本地的master和远程origin处的master对应。



![image-20260316152317845](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316152317845.png)

#### github SSH地址：

git@github.com:liutianming0703/repo.git

#### 从远程仓库克隆

如果已经有一个远端仓库，我们可以直接clone到本地。
命令: git clone <仓库路径> [本地目录]
本地目录可以省略，会自动生成一个目录

#### git branch -a：查看远程分支

![image-20260316154248268](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316154248268.png)

#### 从远程仓库中抓取和拉取

##### 抓取

远程分支和本地的分支一样，我们可以进行merge操作，只是需要先把远端仓库里的更新都下载到本
地，再进行操作。
抓取 命令：git fetch [remote name] [branch name]
抓取指令就是将仓库里的更新都抓取到本地，不会进行合并
如果不指定远端名称和分支名，则抓取所有分支。

##### 拉取

拉取 命令：git pull [remote name] [branch name]
拉取指令就是将远端仓库的修改拉到本地并自动进行合并，等同于fetch+merge
如果不指定远端名称和分支名，则抓取所有并更新当前分支。

##### git pull = git fetch  +   git merge

### 解决合并冲突

在一段时间，A、B用户修改了同一个文件，且修改了同一行位置的代码，此时会发生合并冲突。
A用户在本地修改代码后优先推送到远程仓库，此时B用户在本地修订代码，提交到本地仓库后，也需要
推送到远程仓库，此时B用户晚于A用户，故需要先拉取远程仓库的提交，经过合并后才能推送到远端分
支,如下图所示。

![image-20260316162848617](https://cdn.jsdelivr.net/gh/liutianming0703/note01@main/img/image-20260316162848617.png)

