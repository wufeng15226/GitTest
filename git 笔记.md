## git 笔记

### 前言

+ 之前和同学合作项目时偷懒使用gitKraken这一git图形化界面，基本满足了使用需求（唯一的好处是git的一些基本概念挺熟悉了
+ 但这次旁听OS课的配套项目是private项目，gitKraken免费版不支持，故速成了git
+ 参考：[廖雪峰的git教程](https://www.liaoxuefeng.com/wiki/896043488029600)

### 本地仓库命令

+ git 用户设置
  + 这里使用了ssh秘钥登入
+ 选取某一文件夹作为仓库，仓库初始化

``` cmake
git init
```

+ 为工作区的文件添加到暂存区，在commit前可多次添加
  + 下方的warning表示文件中的回车会自动转化为CRLF(\r\n)，这里其实没有改变
  + 之所以会出现这样的warning，是因为Linux系统中回车是LF(\n)，相同的文件可能在不同的系统上有不同的形式，这就很恶心人，所以git在处理时根据系统自动转化了

``` cmake
git add <文件名>
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory
```

+ 将已经暂存区的版本提交到本地仓库作为一个新版本，默认需要备注
  + -a命令可以跳过添加工作区到暂存区的过程直接把工作区作为版本提交到仓库

``` cmake
git commit -m "提交备注"
git commit -am "提交备注"
```

+ 查看仓库状态，对比本地工作区和暂存区的不同

```cmake
git status
```

+ 查看本地工作区和暂存区的不同，和git status相比只会查看已经add的文件

``` cmake
git diff
```

+ 查看commit历史

```
git log
```

+ 查看版本变化历史

``` cmake
git reflog
```

+ 版本回退与选择
  + HEAD表示当前版本，~n表示回退到前n个版本，不加n表示回退到上一个版本
  + 不加--hard则只会把版本回退到暂存区而不是工作区和暂存区
  + 也可以通过git log/reflog命令查看版本号再变化版本（只需要能唯一辨别的前几位即可）

``` cmake
git reset --hard HEAD~
git reset --hard <版本号>
```

+ 丢弃工作区的某文件修改，回退到上一个版本
  + 不加HEAD则只会从暂存区而不是版本库回退该文件版本

``` cmake
git checkout HEAD -- <文件名>
```

+ 删除暂存区的文件

```cmake
git rm <文件名>
```

### git 区域概念

+ 工作区：本地工作目录
  + 其中有暂存的文件，也有修改过的文件
+ 暂存区
  + 文件通过git add进入暂存区
+ 本地仓库/版本库
  + 暂存区作为一个新版本通过git commit进入本地仓库
+ 见图

![](Pic\615156-20160222173228895-1132617291.jpg)

![](Pic\20180919181719784.png)

### 远程仓库

+ 添加远程仓库
  + wufeng15226为我的用户名，newTest为远程仓库名，可以和工作区目录名不同
  + origin一般表示远程分支

``` cmake
git remote add origin git@github.com:wufeng15226/newTest.git
```

+ 把本地仓库分支推到远程分支
  + -u参数会关联本地的main分支和远程分支origin/main，方便以后简化命令

``` cmake
git push -u origin main
```

+ 删除远程仓库
  + 只是接触关联关系，远程库并没有改动

``` cmake
 git remote rm origin
```

+ 克隆远程库
  + 可以使用SSH或HTTPS来下载，但SSH较快

```cmake
git clone git@github.com:wufeng15226/GitTest
```

### 分支管理

+ 创建并跳转到新分支

``` cmake
git switch -c <分支名>
# 等同于下面两个命令
# git branch <分支名> # 新建分支
# git switch <分支名> # 切换分支
```

+ 查看当前分支

``` cmake
git branch
```


+ 合并分支

``` cmake
git merge <分支名>
```

+ 删除分支

``` cmake
git branch -d <分支名>
```

+ 冲突解决

``` cmake

```

