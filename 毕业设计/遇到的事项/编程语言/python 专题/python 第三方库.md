

[toc]

## 数据库相关库

### [pymongo](https://cloud.tencent.com/developer/article/1612289)

### [redis-py](https://www.runoob.com/w3cnote/python-redis-intro.html)

1. 有序集合添加: zadd('<key>', <dict(value, score)>) -> 1 or 0

## 爬虫相关库

### requests

1. 同步请求库

1. resp.content: 值为字节形式的网页 html

   ```python
   >>> resp = requests.get('http://www.baidu.com')
   >>> resp.content
   ...
   /bdorz/baidu.min.css><title>\xe7\x99\xbe\xe5\xba\xa6\xe4\xb8\x80\xe4\xb8\x8b\xef\
   ...
   ```

   

2. resp.text: 值为对 content 进行解码后的字符形式的网页 html ，使用的 charset 为 resp.encoding 的值

   ```python
   >>> resp = requests.get('http://www.baidu.com')
   >>> resp.encoding = 'utf-8'
   >>> resp.text
   ...
   /bdorz/baidu.min.css><title>百度一下，你就知道</title></head> <body link=
   ...
   >>> resp.content.decode('utf-8')
   ...
   /bdorz/baidu.min.css><title>百度一下，你就知道</title></head> <body link=
   ...
   ```

   

### [scrapy](https://docs.scrapy.org/en/latest/intro/overview.html)

1. [from_crawler()](https://www.jianshu.com/p/e9ec5d7b6204)
2. [如何在中间件修改请求 url](https://blog.csdn.net/wang785994599/article/details/97887294)

### aiohttp

1. 异步请求库，必须运行在协程里

2. [Client Quickstart — aiohttp 3.8.1 documentation](https://docs.aiohttp.org/en/stable/client_quickstart.html#make-a-request)

3. 基本使用

   ```python
   async def main():
       async with aiohttp.ClientSession() as session:
           async with session.get('http://httpbin.org/get') as resp:
               print(resp.status)
               print(await resp.text())
   asyncio.run(main)
   ```
   
4. [异步爬虫例子——与 asyncio 结合使用](D:\vscode-workspace\python_crawler\3. 使用 aiohttp 与 asyncio.py\example.py)

## 数据解析库

### parsel

## 类相关库

### [attrs](https://www.jb51.net/article/162909.htm)	[官方地址](https://www.attrs.org/en/stable/)

类装饰库，能够帮助我们在 python 中更好地实现 OOP，更方便快捷地定义一个类，并实现类的内置方法如 \__eq__ 等。类似 java 的第三方库 lombok

## 日志相关库

### loguru

## web 应用程序框架库

[flask](D:\typora-workspace\毕业设计\web 程序框架\flask.md)

## psutil
