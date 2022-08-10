# Vue Router

## 是什么

## 怎么用

1. 一个路由相当于一个地址

```js
/* src/App.vue，作为一级路由出口 */
<template>
  <router-view/>
</template>

/* src/router/index.js */

import {createRouter, createWebHistory} from "vue-router";

const routes = [
    // 一级路由
    {
        path: '/',
        // 重定位
        redirect: 'welcome'
    },
    {
        path: '/welcome',
        name: 'welcome',
        component: () => import('../views/WelcomePage.vue')
        // 二级路由
        children: [
            {

            }
        ]
    }
]

const router = createRouter({
    history: createWebHistory(),
    routes
})

export default router
```
