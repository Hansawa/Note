[toc]

## 正则表达式库 re

## 日志 logging

## pkgutil 包工具

### method

1. walk_packages(<filePath>, <pkgPath.>): 获取 <filePath> 路径下所有的模块的 ModuleInfo，返回元素为 ModuleInfo 的生成器

### class

1. ModuleInfo(module_finder(FileFinder), name, ispkg)

## importlib

### method

1. import_module(<modPath>): 动态加载包路径为 <modPath> 的模块
1. reload(<module>): 重新加载一个模块

## inspect

### method

1. getmembers(<module>): 获取模块中所有的成员，包括变量，类，方法等。返回列表，列表元素为键值元组
1. isclass(<object>): 判断一个对象是否为类

## time

1. sleep(<second>): 暂停 <second> 秒
1. time(): 获取当前时间戳
1. strftime('timeformat', time): 时间格式化，返回以格式 timeformat（如：%Y/%m/%d/%H/%M/%s）显示的时间 time
1. localtime(): 返回当地当前时间

## asyncio 异步输入输出库

1. 定义协程
1. 创建协程任务，定义任务列表，新建事件循环，设置事件循环，用时间循环运行任务或任务列表

## random

## os

1. getcwd(): 获取当前程序的工作目录（根包）
2. getpid(): 获取当前线程 id

### path

join(*paths): 接收无数个目录字符串或文件字符串，将根据系统决定路径分隔符使用反斜杠（windows）或正斜杠（linux）

## sys

1. gettrefcount(<object>): 获取引用计数，当引用计数为 0 时，解释器会对它进行垃圾回收

## multiprocessing