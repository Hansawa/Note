$ git config --global user.name ""

$ git config --global user.email ""

删除 ssh，在 C:\Users\Hans\\.ssh

$ ssh-keygen -t ecdsa -b 521 -C "your_email@example.com"

登录 github

将pub公钥复制到github的ssh设置里

$ git init

创建分支

$ git checkout -b newbranch

$ git add .

$ git commit -m ""

$ git remote add origin 仓库地址

|

$ git remote remove origin

$ git push origin [branchname | master]