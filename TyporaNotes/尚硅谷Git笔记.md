# 上传本地笔记到github方法

1 在github上建立自己的仓库

2 在待上传的代码文件(工作区)下，右键git bash，运行git init

3 将文件下的所有文件添加到暂存区 git add .，可以使用git status查看状态

4 将暂存区文件提交到本地库，添加注释git commmit -m "日志信息" 文件名，比如git commit -m "TyporaStudy first commit"

5 将本地的仓库关联到github，git remote add 别名 https://github.com/用户名/仓库名.git：git remote add TyporaStudy https://github.com/NqqStudy/TyporaStudy.git

git branch -M master(main)

git push -u TyporaStudy master(main)

# 账号

谷歌账号

```
使用8617315790411登录，不用邮箱
账号qiqiniu41@gmail.com
辅助邮箱：2739149808@qq.com
电话17315760411
密码19970224a_b
```

gitee 

```
用户名NqqStudy
密码19970224a
```

github 

```
用户名 NqqStudy
邮件地址2739149808@qq.com
密码19970224ab
```

# Linux快捷键

- ctrl + L 清屏
- ll 查看文件
- ll -a 查看隐藏文件
- vim hello.txt进行文本编辑
- i进入编辑，esc退出编辑

- 复制yy之前要先esc退出，然后p进行粘贴
- :wq保存文件

# 学习目录

![课程内容](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\课程内容.png)

[Git官网](https://git-scm.com/download)

# 1 Git概述

## 1.1 Git工作机制

![Git工作机制](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\Git工作机制.png)

**工作区是代码存放的磁盘的目录的位置，添加暂存区，提交本地库。还可以继续推送push代码从本地库到远程库**。

## 1.2 Git和代码托管中心

**代码托管中心是基于网络服务器的远程代码仓库，一般简单称为远程库**

- 局域网：GitLab
- 互联网：GitHub（外网）、Gitee 码云（国内网站）  

# 2 Git常用命令

|               命令名称               |      作用      |
| :----------------------------------: | :------------: |
| git config --global user.name 用户名 |  设置用户签名  |
| git config --global user.email 邮箱  |  设置用户签名  |
|             **git init**             |  初始化本地库  |
|            **git status**            | 查看本地库状态 |
|          **git add 文件名**          |  添加到暂存区  |
| **git commit -m "日志信息" 文件名**  |  提交到本地库  |
|            **git reflog**            |  查看历史记录  |
|     **git reset --hard 版本号**      |    版本穿梭    |

## 2.1 设置用户签名

```
git config --global user.email 2739149808@qq.com
git config --global user.name NqqStudy
git config --global user.name 用户名
git config --global user.email 邮箱
这里设置用户名为NqqStudy，邮箱273914808@qq.com
```

- 案例实操

全局范围的签名设置：

```
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/SH0720 (master)
```

![设置用户签名](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\设置用户签名.png)

说明：

- 签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看到，以此确认本次提交是谁做的。 Git 首次安装必须设置一下用户签名，否则无法提交代码。
- 注意： 这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任何关系  

## 2.2 初始化本地库(git init)

![初始化本地库](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\初始化本地库.png)

在E盘创建Git-Space文件夹，在里面创建git-demo，然后文件夹内右键git bash here即可。

## 2.3 查看本地库状态(git status)

### 2.3.1 首次查看(工作区没有任何文件)

```
git status
```

### 2.3.2 新增文件(hello.txt)

```
vim hello.txt
```

### 2.3.3 再次查看(检测到未追踪的文件)

```
git status
```

![查看本地库状态](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\查看本地库状态.png)

### 2.3.4 文本编辑过程(重点)

- ctrl + L 清屏

- vim hello.txt进行文本编辑
- i进入编辑，esc退出编辑
- 复制yy之前要先esc退出编辑，然后p进行粘贴
- :wq保存文件

![hello_txt编辑](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\hello_txt编辑.png)

- ll 查看文件
- cat hello.txt查看文件内容

![hello_txt查看](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\hello_txt查看.png)

- ctrl + l：先进行清屏
- tail -n 1 hello.txt 查看文件第1行

- git status

![hello_txt状态](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\hello_txt状态.png)

## 2.4 添加暂存区

### 2.4.1 工作区的文件添加到暂存区(git add)

在E盘创建Git-Space文件夹，在里面创建git-demo，git-demo是工作区

```
git add 文件名 // 添加到暂存区
```

windows区换行符是CRLF，linux换行符是LF，转换换行符

![工作区添加暂存区](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\工作区添加暂存区.png)

### 2.4.2 查看状态(检测到暂存区有新文件)

- git status：hello.txt变绿色，暂存区文件可以删掉

![暂存区查看状态](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\暂存区查看状态.png)

- git rm --cached hello.txt 可删除暂存区文件，使用git status文件变红

## 2.5 提交到本地库

### 2.5.1 将暂存区的文件提交到本地库

```
git commmit -m "日志信息" 文件名
git commmit -m "first commit" hello.txt
```

![暂存区提交本地库](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\暂存区提交本地库.png)

### 2.5.2 查看状态(git reflog/log)

![工作区查看状态](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\工作区查看状态.png)

- **git reflog：查看版本信息**，c150031是版本号前7位
- **git log：查看详细**

![工作区查看信息](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\工作区查看信息.png)

## 2.6 修改文件(vim hello.txt)

- vim hello.txt
- 按i进入编辑模式，修改代码
- 按esc退出编辑
- :wq进行保存

### 2.6.1 查看状态(检测到工作区有文件被修改)

- 红色说明这次文件的修改还没有添加到暂存区

![修改查看状态](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\修改查看状态.png)

### 2.6.2 将修改的文件再次添加暂存区

- git add hello.txt，此时文件从红色变成绿色

### 2.6.3 查看状态(工作区的修改添加到暂存区)

![修改文件添加暂存区](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\修改文件添加暂存区.png)

- git commit -m "second commit" hello.txt：第2次从暂存区提交到本地库

![修改后提交](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\修改后提交.png)

- 查看提交到本地库后的文件信息get reflog

![修改文件查看信息](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\修改文件查看信息.png)

## 2.7 历史版本

### 2.7.1 查看历史版本(git reflog/log)

```
git reflog 查看版本信息
git log 查看版本详细信息  
```

![查看历史版本](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\查看历史版本.png)

### 2.7.2 版本穿梭

```
git reset --hard 版本号
```

输完命令，选中版本号，点击鼠标滚轮直接复制粘贴

![版本穿梭](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\版本穿梭.png)

- git reflog 查看历史版本
- git reset --hard c15003：此时head从second指向first
- cat hello.txt：查看指向版本的内容

![版本穿梭2](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\版本穿梭2.png)

# 3 Git分支操作

![Gitf分支操作](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\Gitf分支操作.png)

## 3.1 什么是分支

在版本控制过程中，同时推进多个任务，为每个任务，我们就可以创建每个任务的单独分支。使用分支意味着程序员可以把自己的工作从开发主线上分离开来， 开发自己分支的时候，不会影响主线分支的运行。对于初学者而言，分支可以简单理解为副本，一个分支就是一个单独的副本(**分支底层其实也是指针的引用**)

![分支概念](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\分支概念.png)

## 3.2 分治好处

- 同时并行推进多个功能开发，提高开发效率
- 各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可  

## 3.3 分支的操作

|      命令名称       |             作用             |
| :-----------------: | :--------------------------: |
|  git branch 分支名  |           创建分支           |
|    git branch -v    |           查看分支           |
| git checkout 分支名 |           切换分支           |
|  git merge 分支名   | 把指定的分支合并到当前分支上 |

### 3.3.1 查看分支

```
git branch -v
```

![查看分支](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\查看分支.png)

### 3.3.2 创建分支

```
git branch 分支名
```

![创建分支](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\创建分支.png)

- hot-fix：刚创建的新的分支，并将主分支master的内容复制一份

### 3.3.3 修改分支

![修改分支1](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\修改分支1.png)

![修改分支2](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\修改分支2.png)

自己操作

- git checkout hot-fix：切换到hot-fix分支(末尾从master变成hot-fix)
- vim hello.txt进行文本编辑修改hot-fix
- i进入编辑，esc退出编辑
- :wq保存文件
- git status
- git add hello.txt：提交暂存区
- git commit -m "hot-fix first commit" hello.txt
- cat hello.txt

![修改分支3](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\修改分支3.png)

![修改分支4](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\修改分支4.png)

### 3.3.4 切换分支(checkout)

```
git checkout 分支名
```

![切换分支](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\切换分支.png)

### 3.3.5 合并分支

```
git merge 分支名：在 master 分支上合并 hot-fix 分支
```

站在master位置进行合并。这里正常原因是master没有修改，hot-fix是基于master进行修改，所以没有产生合并冲突

```
git merge hot-fix；先切换到master再合并
```

![合并分支](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\合并分支.png)

### 3.3.6 冲突合并

- 冲突产生的表现： 后面状态为 MERGING  

- 冲突产生的原因：合并分支时，两个分支在同一个文件的同一个位置有两套完全不同的修改。 Git 无法替我们决定使用哪一个。必须人为决定新代码内容。  
- 自己理解：master进行修改后，hot-fix也进行修改，且修改的位置完全不同，产生合并冲突

### 3.3.7 解决冲突

![解决冲突1](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\解决冲突1.png)

![解决冲突2](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\解决冲突2.png)

- 编辑有冲突的文件，删除特殊符号
- 添加到暂存区
- git commit -m "merge hot-fix"：注意不能带文件名
- 合并后的只会修改matser不会修改hot-fix

## 3.4 图解

- master、hot-fix 其实都是指向具体版本记录的指针。当前所在的分支，其实是由 HEAD决定。所以创建分支的本质就是多创建一个指针
- HEAD 如果指向 master，那么我们现在就在 master 分支上
- HEAD 如果执行 hotfix，那么我们现在就在 hotfix 分支上

head指针指向分支，比如master，master指向具体版本

# 4 Git 团队协作机制

## 4.1 团队内协作

![团队内协作](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\团队内协作.png)

## 4.2 跨团队协作

![跨团队协作](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\跨团队协作.png)

# 5 GitHub 操作

GitHub 网址： https://github.com/
Ps:全球最大同性交友网站， 技术宅男的天堂， 新世界的大门， 你还在等什么?

| 账号               | 姓名     | 验证邮箱                   |
| ------------------ | -------- | -------------------------- |
| atguiguyueyue      | 岳不群   | atguiguyueyue@aliyun.com   |
| atguigulinghuchong | 令狐冲   | atguigulinghuchong@163.com |
| atguigudongfang1   | 东方不败 | atguigudongfang@163.com    |

注:此三个账号为讲师使用账号， 同学请自行注册， 然后三个同学为一组进行团队协作！

## 5.1 创建远程仓库

![创建远程库1](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\创建远程库1.png)

![创建远程库2](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\创建远程库2.png)

## 5.2 远程库操作

|              命令名称              |                           作用                            |
| :--------------------------------: | :-------------------------------------------------------: |
|           git remote -v            |                 查看当前所有远程地址别名                  |
|    git remote add 别名 远程地址    |                          起别名                           |
|         git push 别名 分支         |              推送本地分支上的内容到远程仓库               |
|         git clone 远程地址         |                将远程仓库的内容克隆到本地                 |
| git pull 远程库地址别名 远程分支名 | 将远程仓库对于分支最新内容拉下来后与 当前本地分支直接合并 |

### 5.2.1 创建远程仓库别名(git-demo)

如果新建文件到新的库，需要init、add、commit三个操作

```
git remote -v // 查看当前所有远程地址别名
git remote add 别名 远程地址 

git remote add git-demo https://github.com/NqqStudy/TyporaStudy.git
// 给地址http后面的东西创建别名是git-demo

git remote add Typora https://github.com/NqqStudy/Typora.git // 别名是Typora
```

![创建远程库别名](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\创建远程库别名.png)

![创建远程库别名2](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\创建远程库别名2.png)

### 5.2.2 推送本地分支到远程仓库(push)

```
git push 别名 分支
```

- git push git-demo master：git-demo这里是别名

![本地分支提交远程仓库](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\本地分支提交远程仓库.png)

### 5.2.3 拉取远程库内容(pull)

首先在github上修改hello.txt，提交改变

```
git pull 远程库地址别名 远程库分支名
git pull git-demo master
```

- git status
- cat hello.txt

![拉取远程库内容1](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\拉取远程库内容1.png)

![拉取远程库内容2](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\拉取远程库内容2.png)

### 5.2.4 克隆远程仓库到本地

```
git clone 远程地址
克隆代码不需要登录
git clone https://github.com/NqqStudy/TyporaStudy.git
```

![克隆远程库到本地](E:\BaiduSyncdisk\计算机学习\TyporaStudy\TyporaPages\尚硅谷Git笔记图片\克隆远程库到本地.png)

### 5.2.5 SSH免密登录

