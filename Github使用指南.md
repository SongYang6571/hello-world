# Github使用指南

## Github网页端

- 创建新的repository

- 创建分支

  - 在最开始的repository中分支默认为master，可以创建其他的分支，在分支上的操作不会影响到master分支，改动后可以merge到master分支。

  - 在分支上进行改动
  - 将分支改动commit
  - pull request
  - merge branch
  - delete branch

- Github网页端官方教程：<https://guides.github.com/activities/hello-world/>

## 本地连接代码仓库

- 安装git
- git配置和远程连接Github代码仓库
  - 配置ssh
    - 打开Git Bash，输入`ssh-keygen –t rsa –C “邮箱地址”`
    - 接下来会提示修改存放rsa密钥文件的文件夹，这里我们不进行修改，使用默认的，一路Enter，直到密钥生成成功（会有一个类似图片的提示）。
    - 访问Github网站，选择网页右上角的下拉菜单（一个向下的小箭头），选择settings。
    - 选择Add SSH Key，进入到添加SSH界面，title一栏随便填，key一栏将刚才生成的rsa文件的内容粘贴到对话框中，点击Add Key按钮完成操作。
    - 验证是否成功：git bash下输入：`ssh –T git@github.com`，第一次会提示输入yes和no，输入yes完成验证。
    - 用`git config –global user.name “用户名”` 和 `git config –global user.email “邮箱”`配置用户名和邮箱，完成配置。
  - 连接github上已经创建的repository
    - 选中想作为本地仓库的文件夹，右键选择git bash here
    - 输入 `git init`，来完成初始化工作。这时候目录里面就多了一个.git的目录了（隐藏）。
    - 连接远程代码仓库：`git remote add origin git@github.com:用户名/仓库名`。
    - 同步本地仓库和github仓库：`git pull git@github.com:用户名/仓库名`，成功后会发现在github上创建的README.md已经成功载入到本地。
- git的使用与命令
  - **git中的文件状态更改**：git中的文件有三种状态：modify，stage，commited。所有的文件在被clone下来之后都是commited状态，当对文件进行修改之后变为modify状态，add一个文件则变成stage状态，此时文件存放在临时存储区，若确认修改，则需要用：`git commit -m “注释”`提交修改。
  - 添加和删除文件：
    - 在本地添加单一文件：`git add 文件名` 
    -  在本地添加多个文件：`git add .`
    - git add支持通配符，例如：`git add *.cpp`
    - 删除文件：`git rm 文件名`（其他操作同上），或者直接在本地删除文件。
    - **注**：添加和删除文件之后需要`git commit -m "注释"`才正式完成。
  - **查看区别：**`git status`，提交之前应该仔细查看区别之后再提交。
  - **本地同步到远程**：`git push git@github.com:用户名/仓库名 [分支名]`
  - 远程同步到本地：`git pull git@github.com:用户名/仓库名 [分支名]`
  - **分支**：分支是指从主分支master上开辟新的开发路径，在branch上的操作不会影响到主分支master，当更改完成后，可以将分支merge到主分支上，完成版本的更新。
    - 创建分支：`git branch 分支名`
    - 切换分支：`git checkout 分支名`
    - merge：`git checkout master  git merge 分支名`
    - 删除分支：`git branch -d 分支名`