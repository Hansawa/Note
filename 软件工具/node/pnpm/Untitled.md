[TOC]

nodejs软件包管理器npm的进阶版

[官网]([pnpm - 速度快、节省磁盘空间的软件包管理器 | pnpm 中文文档 | pnpm 中文网 (pnpmjs.cn)](https://www.pnpmjs.cn/))

## @安装

```shell
npm i pnpm -g
```

## @Usage

```shell
# 查看源
pnpm config get registry
# 切换淘宝源
pnpm config set registry http://registry.npm.taobao.org
# 安装的包在 dependencies 生产环境与开发环境中使用
pnpm add 包名
pnpm add 包名 -S
# 安装的包只在 devDependencies 开发环境中使用
pnpm add 包名 -D
# 全局安装
pnpm add 包名 -g
# 移除某个包
pnpm remove 包名
```

## @使用pnpm搭建vite项目（该项目是一个vue项目）

```shell
# 进入到存放项目的目录

# 初始化vite项目
pnpm init @vitejs/app

# 根据提示进行设置

# 安装初始软件包（依赖）
pnpm install

# 运行vite项目
pnpm dev

# 安装vue提供的前端路由
pnpm add vue-router

# 安装vue提供的状态管理工具
pnpm add vuex

# 安装css预处理器scss的库，并只在开发环境中使用
pnpm add sass -D

# 不需要安装scss--loader，因为vite集成了它

# markdown编辑器
pnpm add @kangc/v-md-editor

# v-md-editor进阶版（两个都要安装）
pnpm add codemirror
```
