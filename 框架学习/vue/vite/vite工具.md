[TOC]

# Vite

## 是什么

下一代前端开发与构建工具

## 为什么用

调试运行时比 webpack 快，因为调试运行时不需要打包（因为现阶段浏览器支持 ES6 ，且 Vite 使用 ES6 的特性运行项目）

## 怎么用

### 1. vite 项目的安装

```shell
# 进入到要安装的项目所在的目录
npm init @vitejs/app # 根据提示进行选择
cd vite项目名
npm install
npm run dev
```

### 2. 插件与依赖的安装

```shell
 npm i [插件|依赖] [-S|-D]
```

### 3. 对配置文件 vite.config.js 进行配置

[官方的配置介绍](https://cn.vitejs.dev/config/) 

```js
import {defineConfig} from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
    /* 项目根目录，index.html文件所在的位置 */
    // root: process.cwd(),
    /* 开发或生产环境的公共基础路径（网站基础地址的协议域名端口号后面的部分）（所有静态资源都会以它为根路径） */
    base: '/',
    plugins: [vue()],
    /* 作为静态资源的根目录，会将里面的内容映射到base */
    publicDir: 'public',
    /* 服务器选项 */
    server: {
        host: 'localhost',
        port: 80,
        /* 端口被占用时禁止使用下一个可用端口 */
        strictPort: true,
        /* 开启https，需要ssl */
        // https: true,
        open: true
    },
    /* 打包选项 */
    build: {
        /* 指定输出路径 */
        outDir: 'dist',
        /* 指定生成静态资源的存放路径 */
        assetsDir: 'assets'
    }
})
```

## 注意事项

1. import .vue 组件时要写后缀
