```js
/* src/plugins/element-plus.js */

/* 引入elementplus组件 */
import ElementPlus from 'element-plus'
import 'element-plus/lib/theme-chalk/index.css'

/* 按需引入 */
// import {ElButton} from 'element-plus'
// import 'element-plus/lib/theme-chalk/el-button.css'
export default (app) => {
    app.use(ElementPlus)

    // app.use(ElButton)
};
```
