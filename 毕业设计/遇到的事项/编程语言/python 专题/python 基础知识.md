[toc]

1. 表示进制数：0b 0o 0x

## 语法

1. python 中对象拥有三个要素：id（身份标识，使用 id(<object>) 查看 id），type（类型，使用 type(<object>) 查看 type），value（值）
2. ==: 只对对象的 value 进行判断
3. is: 对对象的 id 进行判断
4. with...as...: 创建上下文管理器（类似于一个函数），帮助我们自动分配（如文件的打开）与释放（如文件的关闭）资源，并进行异常处理（try/except），在分配与释放资源时如果程序是异步的，会自动添加 await，[例子](https://docs.python.org/zh-cn/3/reference/compound_stmts.html#the-with-statement)
5. [async/await 协程与任务](https://docs.python.org/zh-cn/3/library/asyncio-task.html)
   1. 协程: 运行在用户态的轻量级线程，在线程之上，有自己的寄存器上下文与栈，阻塞时能够被挂起，能够恢复被切换前的状态
   2. async 定义一个方法 <method> 为协程函数，通过 asyncio.run(<method>) 来执行协程函数
   3. await 使被阻塞的方法能够被挂起，进而执行其他协程，只能用在 协程，任务和 Furture
   4. [异步爬虫例子——与 aiohttp 结合使用](D:\vscode-workspace\python_crawler\3. 使用 aiohttp 与 asyncio.py\example.py)
6. yield: 在方法中使用时，该方法变成生成器，是一个可迭代对象，需要 next() 或 for in 来进行执行，每次执行生成一个 yield 后的表达式，并记录当前位置，等待下一次执行
6. assert: 断言，后面为 True，正常运行，后面为 False，抛出异常
6. method(*args, **kwargs): 方法参数中参数前有 * 代表可以接收无数个变量，除字典，出现 \** 代表可以接收字典


## 无导包方法

1. id(): 使用 id(<object>) 查看 id

2. type(): 使用 type(<object>) 查看 type

3. getattr(<class>, '<attrName>', <defultValue>): 获取类 <class> 的名为 <attrName> 的值，如果没有，则返回 <defultValue>

4. issubclass(<subclass>, <superclass>): 判断一个类是否为某个类的子类

4. enumerate(<iterasble>): 传入可迭代对象（生成器，列表，字典），返回一个有两个元素的元组的枚举类实例（也是一个可迭代对象），第一个元素为枚举序号，第二个元素为可迭代对象的各个元素（如果可迭代对象为字典，则第二个元素为各个键）

5. <string>.encode('<charset>'): 将 <string> 按照 <charset> 编码成两个十六进制数组成一个字节的字节类型（bytes）

   ```python
   >>> '稗田阿求'.encode('utf-8')
   b'\xe7\xa8\x97\xe7\x94\xb0\xe9\x98\xbf\xe6\xb1\x82'
   ```

   

6. b<string>.decode('<charset>'): 将两个十六进制数组成一个字节的 <string> 按照 <charset> 解码成字符串类型（str）

   ```python
   >>> b'\xe7\xa8\x97\xe7\x94\xb0\xe9\x98\xbf\xe6\xb1\x82'.decode('utf-8')
   稗田阿求
   ```
   
8. len(): 获取列表，字典的元素个数

## 内置属性

### 共有

1. \_\_name\_\_: 除了它属于的模块是启动模块时的值是 '\_\_main\_\_' 外，其他时候都等于该模块的绝对模块路径（proxypool.crawler）
1. _\_file__: 当前模块的绝对文件路径（windows D:\filename linux D:/filename）
1. \_\_all\_\_: 是一个列表，可以用来存储该模块中的类，变量，方法等，当其他模块以 from <该模块名> import * 时，只能使用 \_\_all\_\_ 中的元素。可以直接 from <该模块名> import \_\_all\_\_ as <otherName>

### 包拥有

1. \_\_path\_\_: 只有包才拥有的内置属性，在 \_\_init\_\_.py 中使用，表示该包的文件路径

## 类型

### list

1. 转换为字符串，两个元素之间用 <string> 分隔: <string>.join(list)

### str

1. 通过 encode('<charset>') 可以转换成 bytes
2. [字符串（可转义）u<string>, 原始字符串（不可转义） r<string>, 字节串 b<string>](https://www.jb51.net/article/176601.htm)
2. 格式化字符串 f<string>: [最新的字符串格式化方法](https://geek-docs.com/python/python-tutorial/python-fstring.html)

### bytes

通过 decode('<charset>') 可以转换成 str

### dict

1. [字典的增删查改](https://www.runoob.com/python3/python-remove-a-key-from-dictionary.html)

### Iter 迭代器

1. 可迭代对象: 实现了 \_\_iter\_\_() 方法的对象为可迭代对象
2. 迭代器对象: 可迭代对象执行 \_\_iter\_\_() 后返回的对象为迭代器对象，for in 表达式可以隐式执行可迭代对象的 \_\_iter\_\_()，并进行迭代

### Generator 生成器

1. 生成器也是可迭代对象

## python 面向对象

1. \__init__.py
2. [metaclass](https://zhuanlan.zhihu.com/p/98440398)
2. 不加下划线的方法是公共方法
3. 用 double leading underscores 加方法名可以使该方法成为 private 方法
3. 用 single leading underscore 加方法名可以使该方法成为 protected 方法
4. 类继承 ABC 类与 @abstractmethod 装饰类方法实现抽象类
5. python 是面向过程的，一个 python 文件代表模块，不能代表类

## 库管理

1. pip list 可以查看已安装的第三方库

## 包管理

1. 导入自定义包时，该包所在的目录文件路径需要放入包搜索路径，使用 sys.path 查看包搜索路径，使用 sys.path.append() 添加路径
1. \_\_path\_\_: 只有包才拥有的内置属性，在 \_\_init\_\_.py 中使用，表示该包的文件路径
1. 当导入包时，该包的 \_\_init\_\_.py 将被执行

## python 编码规范参考 java