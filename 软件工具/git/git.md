$ git config --global user.name ""

$ git config --global user.email ""

删除 ssh，在 C:\Users\Hans\\.ssh

$ ssh-keygen -t ecdsa -b 521 -C "your_email@example.com"

登录 github

将pub公钥复制到github的ssh设置里

初始化本地仓库

$ git init

创建分支（各个分支内的文件内容都不同，切换后会改变文件的内容）

$ git checkout -b newbranch

删除分支

$ git checkout -D branchname

改变分支

$ git checkout branchname

将某个文件添加到暂存区（staging area）

$ git add .

将暂存区的文件添加到本地仓库中（local repository）

$ git commit -m ""

设置远程仓库源（remote repository）

$ git remote add origin 仓库地址

删除远程仓库源

$ git remote remove origin

将本地仓库内容上传到远程仓库

$ git push origin [branchname | master]

从远程仓库拉取内容到本地仓库

$ git pull origin master