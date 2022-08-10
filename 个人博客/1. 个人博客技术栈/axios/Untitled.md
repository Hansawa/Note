[toc]

# axios

## 是什么

基于 promise 的网络请求库

## 为什么



## 怎么用

总共有4中常见的请求方法（method）：get，post，delete，put

返回值是一个 promise 对象，需要使用 then 方法或使用 asnyc-await来取得响应数据

### get 方法

get 方法使用 urlenconded 形式传值（数据存放在url后，表单数据传输有时会用到这种办法，此时content-type为'application/x-www-form-urlencoded'）

```js
/* 第一种写法，参数为 config */
axios({
    url: '/user',
    method: 'get',
    params: {
        id: 999
    }
})

/* 第二种写法，参数为 url */
axios.get('/user?id=999')

/* 第三种写法 参数为 url + config */
axios.get('/user', {params: {id: 999}})
```

1. 后端 controller 的方法的参数名或对象参数的属性名要与 params 对象的属性名一致才能接收，或者在参数名前使用 @RquestParam(value = "") 指定接收 params 对象的属性

方法的参数的类型不能是 Map 类型

### post 方法

```js
/* 第一种写法，参数为 config */
axios({
    url: '/user',
    method: 'post',
    data: {
        name: 'hans',
        pwd: '123456'
    }
})
/* 第二种写法，参数为 url + data */
axios.post('/user', {
    name: 'hans',
    pwd: '123456'
})

/* 第二种形式 */
axios.post('/user', 'name=hans&pwd=123456')
```

使用 post 方法传值时，有两种形式：

1. 传对象，Content-Type 自动使用 ‘application/json;charset=utf-8’，此时使用 json 数据格式传值，数据存放在请求体里
2. 传字符串，而且该字符串的形式为 urlencoded 形式，Content-Type 自动使用 'application/x-www-form-urlencoded'，此时使用 urlencoded 形式传值，数据存放在url后

当axios使用第一种形式传值时，此时请求的headers的 'Content-Type' 的值为 'application/json;charset=utf-8' ，后端有三种方式接收：

1. 后端用字符串类型的参数来接收 json 格式字符串
2. 后端使用 Map 类型参数来接收 json 格式的数据
3. 后端用属性名与 data 对象的属性的名字一致的 java 对象来接收，此时程序会自动将 data 对象的属性的值赋给名字一致的 java 对象的属性。

无论哪一种方法，都必须在controller的方法的参数前加上@RequestBody 表明接收的是请求体的数据，因为此时 post 方法的数据是放在请求体里的

当axios 使用第二种方式传值时，此时请求的headers的 'Content-Type' 的值为 'application/x-www-form-urlencoded' ，后端可以像前端用了 get 方法一样接收数据，因为使用了 urlencoded

### delete 方法（与 get 方法类似）

### put 方法 （与 post 方法类似）



