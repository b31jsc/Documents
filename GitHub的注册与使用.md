### GitHub 的注册与使用
#### 0. 准备工作
* 操作系统: Ubuntu 18.04

#### 1. 什么是 GitHub ？
**GitHub** 是一个基于 git 的代码托管平台。从开源到商业，可以托管代码、查看代码、管理项目、与其他开发人员一起构建软件。  
官方网站：[https://github.com/](https://github.com/)   

#### 2. 注册
* 登录官网首页，输入用户名Username、邮箱Email、密码Password，点击注册 "**Sign up for GitHub**"
![signup](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A801-%E6%B3%A8%E5%86%8C.png)

* 选择使用方案，此处有两个方案，"**Unlimited public repositories for free**" 和 "**Unlimited private repositories for $7/mouth**"。第一项是免费的，第二项是收费的，默认就是第一项，无需修改，直接点击下一步 "**Continue**"
![plan](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A802-plan.png)

* 该页面是一些用户调查，可按自己实际情况填写，也可以直接点击提交 "**Submit**"
![experience](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A803-experience.png)

* 进入欢迎页面，有两个选项，"**Read the guide**" 和 "**Start a project**"。第一项是使用教程，可以借鉴学习，第二项是建立一个新的工程，点击第二项 "**Start a project**"
![Learn](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A804-Learn.png)

* 进入邮箱验证界面，提示需要验证邮箱地址
![verify](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A805-verify.png)

* 登录自己的邮箱，看到一封来自 **GitHub** 邮件，点击下方的链接地址，验证邮箱
![email](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A806-email.png)

* 再次回到了欢迎页面，可以看到左上方提示 “**Your email was verified**”，邮箱验证成功。
![verified](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A807-verified.png)

#### 3. 建立仓库
* 再次点击 "**Start a project**"
![verified](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A807-verified.png)

* 进入新建仓库页面，输入仓库名称，此处以"**test**"为例。点击 "**Create repository**"
![create](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A809-create.png)

* 仓库建立成功，进入快速设置页面，下方提示三种操作：  
"**...or create a new repository on the command" line** 创建一个新仓库  
"**...or push an existing repository from the command line**" 上传一个已经建立的仓库  
"**...or import code from another repository**" 从其他的仓库导入代码  
我们按第一种操作
![quicksetup](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A810-quicksetup.png)

* 在终端命令行新建一个目录，在新目录下依次输入如下命令  
输入 `echo "# test" >> README.md` 创建文件README.md  
输入 `git init` 初始化仓库  
输入 `git add README.md` 添加文件README.md  
输入 `git commit -m "first commit"` 本地保存  
输入 `git remote add origin https://github.com/b31jsc/test.git` 关联GitHub仓库
输入 `git push -u origin master` 上传，此处会提示输入用户名和密码，输入即可
  ```
  $ mkdir test
  $ cd test/
  $ echo "# test" >> README.md
  $ git init 
  已初始化空的 Git 仓库于 /home/jiang/git/test/.git/
  $ git add README.md
  $ git commit -m "first commit"
  [master （根提交） b6e0463] first commit
   1 file changed, 1 insertion(+)
   create mode 100644 README.md
  $ git remote add origin https://github.com/b31jsc/test.git 
  $ git push -u origin master
  Username for 'https://github.com': b31jsc
  Password for 'https://b31jsc@github.com': 
  对象计数中: 3, 完成.
  写入对象中: 100% (3/3), 216 bytes | 216.00 KiB/s, 完成.
  Total 3 (delta 0), reused 0 (delta 0)
  To https://github.com/b31jsc/test.git
   * [new branch]      master -> master
  分支 'master' 设置为跟踪来自 'origin' 的远程分支 'master'。
  $ 
  ```
* 上传成功后刷新仓库页面，可以看到test已经上传
![test](https://raw.githubusercontent.com/b31jsc/img/master/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A8/GitHub%E7%9A%84%E6%B3%A8%E5%86%8C%E4%B8%8E%E4%BD%BF%E7%94%A811-test.png)






