## git 笔记

### 前言

+ 之前和同学合作项目时偷懒使用gitKraken这一git图形化界面，基本满足了使用需求
+ 但这次OS项目是私人项目，gitKraken免费版无法使用，想了想也该好好学习git了

### 命令

+ git 用户设置
  + 这里使用了ssh秘钥登入
+ 选取某一文件夹作为仓库，仓库初始化

``` cmake
git init
```

+ 为仓库添加预备文件或修改过的文件，在commit前可多次添加
  + 下方的warning表示文件中的回车会自动转化为CRLF(\r\n)，这里其实没有改变
  + 之所以会出现这样的warning，是因为Linux系统中回车是LF(\n)，相同的文件可能在不同的系统上有不同的形式，这就很恶心人，所以git在处理时根据系统自动转化了

``` cmake
git add 文件名
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory
```

+ 将添加的文件提交，默认需要备注

``` cmake
git commit -m "提交备注"
```

+ 查看仓库状态

```cmake
git status
```

+ 查看本地和commit文件的不同，注意只会查看已经add的文件