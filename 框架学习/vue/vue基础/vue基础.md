一个 vue 应用的创建

```js
// 创建跟组件
const RootComponent = { 
  /* 选项 */ 
}
// 创建 Vue 应用实例， 并配置根组件
const app = Vue.createApp(RootComponent)
// 将 Vue 应用实例挂载到 id 为 app 的元素（一般为 div）中
const vm = app.mount('#app')
// 此时可以创建许多组件，他们的作用范围在被挂载的元素内
```

```js
// Vue 应用实例是用来在应用中注册“全局”组件的
const app = Vue.createApp({})
app.component('SearchInput', SearchInputComponent)
app.directive('focus', FocusDirective)
app.use(LocalePlugin)
// 应用实例暴露的大多数方法都会返回该同一实例，允许链式
Vue.createApp({})
  .component('SearchInput', SearchInputComponent)
  .directive('focus', FocusDirective)
  .use(LocalePlugin)
```

@attrs 访问的是组件的所有非 props 或 emits 属性（属于 html 概念的属性）

data() 内返回的对象中的键值对名为 property

vue 会自动添加 css 的前缀（如果该 css 在不同的浏览器中需要的话）

methods 选项中的方法中无其他实参时可以接受一个原始 DOM 事件 event，要写出来，形参可以不写 \$event，当有其他参数时，需要实参 event 时形参 \$event 要写出来

组件可以用 vm.property 或 vm.\$data.property 访问某一个父 property

组件可以用 vm.some_method() 来使用在 method 定义的某一方法

组件声明中的 this 指向的是当前的组件
