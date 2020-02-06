# Git操作指南



## 2020-02-06

### 配置Git

首先在本地创建`ssh key；`

```
$ ssh-keygen -t rsa -C "your_email@youremail.com"
```

后面的`your_email@youremail.com`改为你在github上注册的邮箱，之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。成功的话会在`~/`下生成`.ssh`文件夹，进去，打开`id_rsa.pub`，复制里面的`key`。

回到github上，进入 Account Settings（账户配置），左边选择SSH Keys，Add SSH Key,title随便填，粘贴在你电脑上生成的key。

![github-account](https://www.runoob.com/wp-content/uploads/2014/05/github-account.jpg)

为了验证是否成功，在git bash下输入：

```
$ ssh -T git@github.com
```

如果是第一次的会提示是否continue，输入yes就会看到：You've successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。

接下来我们要做的就是把本地仓库传到github上去，在此之前还需要设置username和email，因为github每次commit都会记录他们。

```
$ git config --global user.name "your name"
$ git config --global user.email "your_email@youremail.com"
```

### 检出仓库

执行如下命令以创建一个本地仓库的克隆版本：

```
$ git clone /path/to/repository 
```

如果是远端服务器上的仓库，你的命令会是这个样子：

```
$ git clone username@host:/path/to/repository
```

### 工作流

你的本地仓库由 git 维护的三棵"树"组成。第一个是你的 `工作目录`，它持有实际文件；第二个是 `暂存区（Index）`，它像个缓存区域，临时保存你的改动；最后是 `HEAD`，它指向你最后一次提交的结果。   

你可以查看工作目录的更改，使用如下命令：

```
$ git add status
```

你可以提出更改（把它们添加到暂存区），使用如下命令：

```
$ git add <filename>
```

```
$ git add *
```

这是 git 基本工作流程的第一步；使用如下命令以实际提交改动：

```
$ git commit -m "代码提交信息"
```

现在，你的改动已经提交到了 **HEAD**，但是还没到你的远端仓库。        

![trees](https://www.runoob.com/wp-content/uploads/2014/05/trees.png)

### 推送改动

你的改动现在已经在本地仓库的 **HEAD** 中了。执行如下命令以将这些改动提交到远端仓库：

```
$ git push origin master
```

可以把 *master* 换成你想要推送的任何分支。            

如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加：

```
$ git remote add origin <server>
```

如此你就能够将你的改动推送到所添加的服务器上去了。