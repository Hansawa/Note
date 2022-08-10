打包时的各个包的版本位置package.json

现在前端是模块化开发

webpack 是一个现代 JavaScript 应用程序的静态模块打包器(module bundler)
，就像java程序会打成jar包给后续项目复用，js也可以被webpack打包给后续项目服用
[官网](https://www.webpackjs.com/)

安装webpack

```shell
--- 打包工具
npm install webpack -g
--- 客户端
npm install webpack-cli -g
```

测试安装成功

```shell
webpack -V
webpack-cli -V
```

编写代码
写模块与模块方法，文件名为hello.js

```js
/* webpack需要使用es6——js标准的语法 */
/* 本文件为一个js模块 */
/* 暴露一个方法 */
exports.sayHi = function () {
    document.write("<h1>ES6规范</h1>");
};
exports.sayHi1 = function () {
}
```

写打包入口，文件名设置为main.js

```js
/* 引入一个模块，不需要写.js */
var Hello = require("./hello");
/* 使用模块的方法 */
Hello.sayHi();
/* 前端在不断模仿后端，模块化 */
```

写打包配置文件，文件名设置为webpack.config.js

```js
module.exports = {
    /* 打包的入口 */
    entry: './modules/main.js',
    /* 输出路径 */
    output: {
        filename: './js/bundle.js'
    }
};
```

打包，使用控制台，输入后webpack程序会自动寻找webpack.config.js文件进行打包

```shell
webpack
```

打包后包文件在dist里

js包文件的使用
创建html文件

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<script src="./dist/js/bundle.js"></script>

</body>
</html>
```

前端用模块化开发
以后写完vue项目后，用webpack打包，最后用html的script引入就可以了

webpack 监听功能

```shell
webpack --watch
```

可以用来热部署，当你改变js时，它会自动打包