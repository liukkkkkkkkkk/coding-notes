# Git 学习
## 学习网址在[廖雪峰的官方网站]（https://liaoxuefeng.com/index.html）
## 定义： Git是目前世界上最先进的***分布式*** 版本控制系统（没有之一）。
#### 如果有一个软件，不但能自动帮我记录每次文件的改动，还可以让同事协作编辑，这样就不用自己管理一堆类似的文件了，也不需要把文件传来传去。如果想查看某次改动，只需要在软件里瞄一眼就可以，岂不是很方便？
***他是linux的发明人用了两周用c语言进行编写的***
## 1.安装
***在windws上安装Git***

1.首先有两种方法
第一种是直接从Git官网直接下载安装程序，然后按默认选项安装即可。安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功。

 <img width="447" height="259" alt="image" src="https://github.com/user-attachments/assets/f5fdbe80-d8ce-421e-b7e7-d4105c5a95c8" />
 
第二种是先安装一个包管理器，推荐Scoop，然后在PowerShell中通过以下命令安装Git：
```powershell
C:\> scoop install git
```
安装成功后，在powershell下运行命令 ***git -v*** 显示Git版本，可看到已下输出

<img width="635" height="262" alt="image" src="https://github.com/user-attachments/assets/8f0457ab-88d4-440b-934f-1a8940afcc54" />

### 使用包管理器安装git只需一条命令，且升级非常方便： 升级命令为 ***scoop update git***

## 配置Git
安装好Git后，还需要最后一步设置，在命令行输入：
```cmd
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
#### 因为Git是分布式控制系统，所以，每个机器都必须自报家门即你的名字和Email地址

***注意 git configd的命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址***

## 2.创建版本库

1.首先介绍什么是版本库，版本库又名仓库（Repository）,可以简单理解为一个目录，在这个目录里所有文件都可以被Git管理起来，文件的修改、删除、Git都能跟踪，在任何时刻可以追踪历史，或者可以在某个时刻可以还原。

2.首先创建一个版本库,在合适的地方，创建一个空目录
```cmd
$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit
```

3.通过 git init 命令把创建的目录变成Git可以管理的仓库
```cmd
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/
```

***Git仓库就创建完成了，他会告诉你是一个空的仓库（empty Git repository）里面目录里多了一个.git的目录，这个目录是git来跟踪管理版本库的，所以没事千万别手动修改这个目录里的文件，不然改乱了，就把git仓库给改坏了***

***如果没有看到.git目录，因为他是隐藏的，用ls -ah命令就可以看见***

