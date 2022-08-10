# 基于 vite 的 Vue 项目搭建流程

## 1. 使用npm构建vite项目

因为使用pnpm构建项目会导致代码提示，代码导航等等idea的功能失效，因此还是选用npm来构建项目

```shell
1. 创建vite项目
# 进入到要安装项目的目录
npm init vite
# 根据提示进行设置
cd vite项目名
# 下载nodejs相关的依赖
npm install
# 运行vite
npm run dev
# 打包
npm run build

2. 各种插件的安装
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

# v-md-editor 升级组件
npm i codemirror -S

# 前端样式归一化工具
npm i normalize.css -S

# 组件库 element-plus
npm i element-plus -S

#组件库 element-plus 的图标库
npm i @element-plus/icons-vue
```

构建完成后，将多余的文件及代码删除（比如 Hello.... .vue组件，App.vue 中的部分代码）

构建完成后的基本目录结构：

![image-20210517080314016](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210517080314016.png)

## 2. 配置与应用插件

#### 前端路由 vue-router

在此我使用的路由模式为历史模式 WebHistory 

1. 在 src 目录下创建 router 目录，接着在其中创建路由主文件 index.js

2. 在 index.js 文件中进行配置
   
   ```js
   /* /src/router/index.js */
   
   import {createRouter, createWebHistory} from "vue-router";
   
   /* 配置路由表。在之后的开发中，会在这里编写组件的路由 */
   const routes = [
       {
           path: ,
           alias: ,
           name: ,
           /* 路由懒加载 */
           component: () => import('')
           /* 不使用懒加载，要 import 组件进来 */
           component: ''
           children: [
               {
   
               }
           ]
       }
   ];
   
   /* 创建并配置 router 实例 */
   const router = createRouter({
       /* 路由模式使用历史模式 */
       history: createWebHistory(),
       routes
   });
   
   /* 暴露 router 实例 */
   export default router;
   ```

3. 在 main.js 中应用插件
   
   ```js
   /* /src/main.js */
   
   /* 导入 router 插件 */
   import router from './router/index'
   ...
   createApp(App)
       /* 应用 router 插件 */
       .use(router)
   ...
   ```

4. 在 App.vue 文件中放置<router-view/>来显示路由到的组件
   
   ```html
   <!-- /App.vue -->
   
   <template>
     <router-view/>
   </template>
   ...
   ```

#### 状态管理工具vuex

1. 在 src 目录下创建 store 目录，接着在其中创建主文件 index.js

2. 在 index.js 中进行配置
   
   ```js
   /* /src/store/index.js */
   
   import {createStore} from "vuex";
   
   const store = createStore({
       state: {},
       mutations: {},
       actions: {},
       modules: {}
   })
   
   export default store
   ```

3. 在 main.js 文件中应用插件
   
   ```js
   /* /src/main.js */
   
   /* 导入 vuex 插件 */
   import vuex from './store/index'
   ...
   createApp(App)
       /* 应用 vuex 插件 */
       .use(vuex)
   ...
   ```

#### axios

1. 在 src 目录下创建 request 目录，接着在其中创建主文件 index.js

2. 在index.js文件中进行配置
   
   ```js
   /* /src/request/index.js */
   
   import axios from 'axios'
   
   /* 创建 axios 实例并配置基础url与超时时间 */
   const instance = axios.create({
       /* 不使用反向代理解决跨域问题 */
       baseURL: 'http://localhost:8080',
       /* 使用反向代理解决跨域问题 */
       baseURL: '/api',
       timeout: 2000
   });
   
   /* 为 axios 实例配置请求拦截器（可以实现携带token给后端验证等操作） */
   instance.interceptors.request.use(req => {
       console.log(req);
       return req;
   }, err => {
       console.log(err);
   });
   
   /* 为 axios 实例配置响应拦截器（对相应的数据进行简单处理，比如只返回data对象） */
   instance.interceptors.response.use(resp => {
       console.log(resp);
       return resp.data;
   }, err => {
       console.log(err);
   });
   
   /* 对 axios 实例进行简单的封装，选择这种封装形式的原因是参数比较整齐 */
   function post(url, data) {
       return instance({
           method: 'POST',
           url,
           data
       });
   }
   
   /* 给parms赋予默认值 */
   function get(url, params={}) {
       return instance({
           method: 'GET',
           url,
           params
       });
   }
   
   function del(url, params={}) {
    return instance({
           method: 'DELETE',
           url,
           params
       });
   }
   
   function put(url, data) {
       return instance({
           method: 'PUT',
           url,
           data
       });
   }
   
   /* 单文件上传 */
   function uploadFile(url, file) {
       let data = new FormData();
       data.append('file', file);
   
       return instance({
           method: 'POST',
           url,
           data,
           headers: {
               'Content-Type': 'multipart/form-data'
           }
       });
   }
   
   /* 多文件上传 */
   function uploadFiles(url, files) {
       let data = new FormData();
       for (let file of files)
           data.append('files', file);
   
       return instance({
           method: 'POST',
           url,
           data,
           headers: {
               'Content-Type': 'multipart/form-data'
           }
       });
   }
   
   /* 暴露封装后的方法 */
   export {get, post, del, put, uploadFile, uploadFiles};
   ```

3. 在需要使用 axios 发送异步请求的组件中导入封装后的方法
   
   ```js
   /* 导入封装后的方法，并将方法放置在 request 对象中 */
   import request from '../request'
   
   request.[get|post](url, [params|data])
   ```

**最佳实践**：

​    在 main.js 文件中全局注册封装后的 axios，然后在组件中通过 this.axios.[get | post] (url, [data | params]) 调用异步请求的方法

```js
/* /src/main.js */
...
import axios from './request'
...

const app = createApp(App)
app.config.globalProperties.axios = axios
```

​    在需要使用 axios 发送异步请求的组件中使用：

```js
this.axios.[get | post](url, [data | params])
```

#### markdown编辑器 v-md-editor 及其升级组件 codemirror

1. 在 src 目录下创建 plugins 目录，接着在其中创建v-md-editor.js

2. 在 v-md-editor.js 文件中进行配置
   
   ```js
   /* /src/plugins/v-md-editor.js */
   
   /* markdown编辑 显示器 */
   import VMEditor from '@kangc/v-md-editor/lib/codemirror-editor'
   import '@kangc/v-md-editor/lib/style/codemirror-editor.css'
   // codemirror 编辑器的相关资源
   import Codemirror from 'codemirror';
   // mode
   import 'codemirror/mode/markdown/markdown';
   // placeholder
   import 'codemirror/addon/display/placeholder';
   // active-line
   import 'codemirror/addon/selection/active-line';
   // scrollbar
   import 'codemirror/addon/scroll/simplescrollbars';
   import 'codemirror/addon/scroll/simplescrollbars.css';
   // style
   import 'codemirror/lib/codemirror.css';
   
   /* markdown预览器 */
   import VMPreview from '@kangc/v-md-editor/lib/preview'
   import '@kangc/v-md-editor/lib/style/preview.css'
   
   /* 引入主题 */
   import VuepressTheme from '@kangc/v-md-editor/lib/theme/vuepress'
   import '@kangc/v-md-editor/lib/theme/style/vuepress.css'
   
   /* 应用升级组件 */
   VMEditor.Codemirror = Codemirror;
   /* 应用主题 */
   VMEditor.use(VuepressTheme);
   
   /* 应用主题 */
   VMPreview.use(VuepressTheme);
   
   export default (app) => {
       app.use(VMEditor);
       app.use(VMPreview);
   };
   ```

3. 在 main.js 文件中应用插件
   
   ```js
   /* /src/main.js */
   
   /* 导入 v-md-editor 插件 */
   import VMEditor from './plugins/v-md-editor'
   ...
   createApp(App)
       /* 应用 v-md-editor 插件 */
       .use(VMEditor)
   ...
   ```

4. 在需要用到 markdown 编辑器的组件中使用 v-md-editor 提供的组件标签，绑定一个 text data属性
   
   ```html
   <v-md-editor v-model="text" height="400px"></v-md-editor>
   ```

5. 在需要用到 markdown 预览器的组件中使用 v-md-editor 提供的组件标签，绑定一个 text data属性
   
   ```html
   <v-md-preview :text="text"></v-md-preview>
   ```

#### 前端样式归一化工具 normalize.css

1. 在 main.js 中引入
   
   ```js
   /* src/main.js */
   
   import 'normalize.css'
   ```

## 3. 创建全局 css 样式文件 global.scss

1. 在 /src/assets 目录下创建 global.scss 文件

2. 添加如下代码
   
   ```scss
   * {
       margin: 0;
       padding: 0;
   }
   ```

3. 在 main.js 文件引入该文件
   
   ```js
   /* /src/main.js */
   
   import './assets/global.scss'
   ```

## 4. 引入组件库 element-plus

1. ```js
   import ElementPlus from 'element-plus'
   import 'element-plus/lib/theme-chalk/index.css'
   
   export default function (app) {
       app.use(ElementPlus)
   }
   ```

2. ```
   app.use(elementPlus)
   ```

## 5. main.js 文件最终代码

```js
/* /src/main.js */

import {createApp} from 'vue'
import App from './App.vue'
import router from './router'
import vuex from './store'
import VMEditor from './plugins/v-md-editor'
import 'normalize.css'
import './assets/global.scss'

const app = createApp(App)
    .use(router)
    .use(vuex)
    .use(VMEditor)
app.config.globalProperties.axios = axios
app.mount('#app')
```

## 6. 补全目录结构

1. 在 src 目录下创建 views 目录存放视图组件

## 7. 配置 vite.config.js

```js
/* /vite.config.js */

import {defineConfig} from 'vite'
import vue from '@vitejs/plugin-vue'
import {resolve} from 'path'

export default defineConfig(({command, mode, ssrBuild}) => {
  // dev and serve
  if (command === 'serve') {
    // console.log(process.cwd())
    return {
      root: './',
      /*
        root: project root directory, where 'index.html' is located.
        default: process.cwd(), process from node.exe.
        absolute path (if you move your 'index.html' to 'src' directory).
        root: 'D:/graduation_project/background/src', both '/' and '\\'.
        relative path (relative to current working directory).
        root: './src'
       */

      base: '/',
      /*
        部署到网站后的公共基址，
        项目中所有文件的路径（不包括在 public 目录中的静态资源）将以它作为基址改写地址
      */

      mode: 'development',
      /* 设置开发模式（development）或发布、构建模式（production） */

      define: {
        __APP_VERSION__: JSON.stringify('v0.0.1'),
      },
      /*
        定义全局变量，值必须是 JSON 对象
        如果变量的值要为字符串，不能直接写字符串，因为会被当成表达式，
        需要用 JSON.stringify() 转成字符串
      */

      plugins: [vue()],
      /* 构建工具 vite 将会使用的插件 */

      publicDir: 'public',
      /*
        存放静态资源的路径，默认为 'public'
        可以为绝对地址，也可以为基于项目根目录的相对地址
        开发模式下，在该目录的静态资源将不会做任何的处理，直接复制到网站的根路径
        发布模式下，在该目录的静态资源将不会做任何的处理，直接复制到 'outDir' 路径的根路径
      */

      cacheDir: 'node_modules/.vite',
      /* 用来存放缓存文件的目录 */

      resolve: {
        alias: {
          '/@': path.resolve(__dirname, './src'),
          '/assets': path.resolve('/@', './assets')
        },
        /* 给路径取别名 */

        extensions: ['.mjs', '.js', '.ts', '.jsx', '.tsx', '.json']
        /* 导入时不需要写扩展名的文件 */
      },

      server: {
        host: 'localhost',
        /* 该项目启动时，服务器要监听的 ip 地址，一有对该地址发送请求便返回页面 */

        port: 8081,
        /* 服务器监听的 ip 地址的端口号 */

        strictPort: true,

        open: true,
        /* 每次启动时是否自动打开页面 */

        /*
        * 设置反向代理处理跨域问题
        * 当程序发现请求中含有'/api'时，会自动使用被代理的服务器，然后拼接上请求，如：
        * http://localhost:8080/api/adminlogin，
        * 但需要的完整请求为 http://localhost:8080/adminlogin，
        * 所以需要使用 rewrite 来将'/api'替换成空串
        * 此时在浏览器的开发者工具中显示的完整请求为 http://localhost:8081/api/adminlogin，
        * 但实际的完整请求为 http://localhost:8080/adminlogin */
        proxy: {
          '/api': {
            target: 'http://localhost:8080',
            changeOrigin: true,
            rewrite: path => path.replace(/^\/api/, '')
          }
        },
        /* 设置代理，可以用来解决跨域问题（如上） */

        cors: false
        /* 是否接受所有来源的请求，不接受就会产生跨域问题 */
      }
    }
  }
  else if (command === 'build') {
    return {

    }
  }
})
```

vite 配置文档[Configuring Vite | Vite (vitejs.dev)](https://vitejs.dev/config/)

1. ship with：过渡到
2. leverage：充分利用
3. intellisense：智能感知
4. tucked away：藏起来

## 8. 最终项目目录结构

![image-20210521140325293](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20210521140325293.png)

1. background-front-end：项目名，可以在 vite 构建项目时自定义
2. public：存放 `不会被源码引用 或 必须保持原有文件名`的文件，这些文件在开发时可以直接通过 / 根路径访问到，并且打包时会被完整复制到目标目录的根目录下。
3. assests：存放资源文件
4. components：存放全局公用组件
5. layouts：存放页面布局
6. plugins：存放插件
7. request：存放 axios 的封装文件
8. router：存放 vue-router 的配置文件
9. store：存放 vuex 状态管理的配置文件
10. views：存放路由级别视图组件
11. App.vue：根组件，会被 Vue 用来创建 Vue 实例
12. main.js：入口文件，Vue 在这里创建 Vue 实例，使用插件，引入全局样式，挂载到元素
13. index.html：首页文件，引导浏览器找到主文件
14. vite.config.js：存放 vite 项目的配置文件
