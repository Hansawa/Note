node package manager：在下载nodejs时被一同下载

[nodejs官网对npm的介绍](http://nodejs.cn/learn/an-introduction-to-the-npm-package-manager)

## npm 安装的包的路径

[npm 将软件包安装到哪里 (nodejs.cn)](http://nodejs.cn/learn/where-does-npm-install-the-packages)

## 使用npm构建vite

```shell
1. 工具安装
# 到项目根目录
npm init @vitejs/app
cd vite项目名
npm install
# 运行vite
npm run dev

2. 各种插件与依赖安装
# vue提供的前端路由
npm i vue-router@next -S

# vue提供的状态管理工具vuex
npm i vuex@next -S

# 基于 promise 的网络请求库axios
npm i axios@next -S

# css预处理器scss的库
npm i sass -D

# 不需要安装scss--loader，因为vite集成了它

# markdown编辑器
npm i @kangc/v-md-editor@next -S

# v-md-editor进阶版（两个都要安装）
npm i codemirror -S
```

```shell
i：install
un: uninstall
-S：即--save（保存），包名会被注册在package.json的dependencies里面，在生产环境下这个包的依赖依然存在
-D：即--dev（生产），包名会被注册在package.json的devDependencies里面，仅在开发环境下存在的包用-D，如babel，sass-loader这些解析器

`npm i 插件名 -S or -D`
```

## 注意

1. 安装 nvm 时 环境变量 symlink 是正在使用的 nodejs 的快捷方式的地址

2. npm init 与 npm create 作用相同：[npm init - What is npm create command? - Stack Overflow

## npm 源码解读

npm.cmd -> node.exe npm-cli.js prefix -g，此时 node.js 程序会给 npm-cli.js 里的被 require 的函数提供一个 NodeJs.Process 类型的 process 实例，该 process 实例的 argv 属性即为执行 node.exe 时在其后添加的各个命令行参数 ->