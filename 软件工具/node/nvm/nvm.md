是一款nodejs版本管理器，可以下载、使用各个版本的nodejs

[官网]([coreybutler/nvm-windows: A node.js version management utility for Windows. Ironically written in Go. (github.com)](https://github.com/coreybutler/nvm-windows))

安装时选择nodejs路径可能是选择已安装nodejs的路径，安装nvm时对它们进行迁移

## Usage

```shell
# 查看nvm版本
nvm version
# 查看系统位数
nvm arch
# 查看已安装或可安装nodejs版本
nvm list [available]
# 查看或修改nodejs下载路径（可修改）
nvm root [ |nodejs根路径]
# 下载某版本某位数的nodejs
nvm install 版本号 位数[32|64]
# 使用某个版本的nodejs（要输入此命令才能使用 npm 等）
nvm 版本号
# 卸载
nvm uninstall 版本号 位数
```

## 使用 nvm 安装nodejs

```shell
# 1. 先从官网下载安装 nvm
# 2. 设置环境变量 NVM_HOME 指向 nvm 根目录
# 3. 在 nvm 根目录创建 settings.txt 文件，此文件包括安装 node 的目录及快捷方式地址，填入
root: F:\nvm
path: F:\nodejs
# 2. 从控制台安装某个 node 版本
nvm install 版本号 位数[32|64]
# 3. 使用某个 node 版本
nvm use 版本号
# 此时程序会创建一个指向 nvm 里的某一版本的 node 程序目录的快捷方式，设置环境变量 NVM_SYMLINK 指向该快捷方式
```
