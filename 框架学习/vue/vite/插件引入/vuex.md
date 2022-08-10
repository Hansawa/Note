# Vuex

## 是什么

## 怎么用

```js
/* src/store/index.js */

import {createStore} from "vuex";

const store = createStore({
    /* 全局状态 */
    state: {},
    mutations: {
        /* 写方法，通过$store.commit('方法名')调用 */
    },
    actions: {},
    modules: {}
})

export default store
```
