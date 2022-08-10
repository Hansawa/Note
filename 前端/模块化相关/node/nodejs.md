Node.js 是一个开源与跨平台的 JavaScript 运行时环境

[官网](http://nodejs.cn/)

NPM是随同NodeJS一起安装的包管理工具，能解决NodeJS代码部署上的很多问题，常见的使用场景有以下几种：
    1. 允许用户从NPM服务器下载别人编写的第三方包到本地使用。
    2. 允许用户从NPM服务器下载并安装别人编写的命令行程序到本地使用。
    3. 允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用。

yarn：yarn的简介：Yarn是facebook发布的一款取代npm的包管理工具。

修改npm的下载路径
```shell
npm config set cache "F:\nodejs\npm-cache"
npm config set prefix "F:\nodejs\npm_global"
```

查看npm的各个路径
```shell
npm config list
```

npm下载vue-cli
```shell
npm install vue-cli -g
```
npm查找全局包路径
```shell
npm root -g
```

## npm命令
```shell
npm install moduleName --安装模块到项目的node_modules下

npm install -g moduleName -- -g的意思是将模块安装到全局 具体安装到磁盘哪个位置 由npm config prefix设定的位置决定

npm install --save moduleName -- --save 的意思是将模块安装到项目的node_modules下 并在package文件的dependencies节点写入依赖 -S为该命令的缩写

npm install --save-dev moduleName -- --save-dev 的意思是将模块安装到项目的node_modules下 并在package文件的devdependencies节点写入依赖 -D为该命令的缩写
```

## 出现的问题
1. 安装了vue后出现提示：vue不是内不命令
    解决方案：
        1. 将当前路径切换至npm的全局包路径，vue程序在那里
        2. 将npm的全局包路径设置到环境变量里
2. 安装的时候不要强修复！！