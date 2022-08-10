

[toc]

## 1. 使用 vue-cli4 创建 vue 项目，启动时显示如下错误

![image-20210702210515746](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210702210515746.png)

解决方案：

1. 在 vue.config.js 中配置 Babel 的 loader

   ```js
   /* vue.config.js */
   
   module.exports = {
     configureWebpack: {
       module: {
         rules: [
           {test: /\.js$/, use: 'babel-loader'}
         ]
       }
     }
   }
   ```

   

