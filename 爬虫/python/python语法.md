with...as...：能够自动处理异常

yield：拥有 yield 的函数在调用时不会执行，而是返回一个生成器，只有 for in遇到生成器时，每迭代一次生成器就在 yield 处返回一次值给迭代变量，因此是不占内存的，不像列表，而 next(生成器)时也可以使生成器执行到 yield 处并返回值，下次 next 时再从 yield 处开始执行

[Python进阶——如何正确使用yield？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/321302488)

[3. (译)Python关键字yield的解释(stackoverflow) — 一起写Python文章，一起看Python文章 (pyzh.readthedocs.io)](https://pyzh.readthedocs.io/en/latest/the-python-yield-keyword-explained.html)

```python
# coding: utf8
# 生成器
def gen(n):
    for i in range(n):
        yield i

g = gen(5)      # 创建一个生成器
print(g)        # <generator object gen at 0x10bb46f50>
print(type(g))  # <type 'generator'>

# 迭代生成器中的数据
for i in g:
    print(i)

# Output:
# 0 1 2 3 4
```

类：

```python
# 在一个类中，self 代表的是实例本身，而在 @classmethod 里的 cls 代表的是该类本身
class class_name(parent_class):
    # 实例属性的优先级比类属性高，因此当实例属性与类属性重名后，调用（如 class_name.a）时用的是实例属性。如果没有实例属性，则用类属性
    a = 1;
    # 定义实例属性与初始化时每一个实例属性会被赋予什么名称的参数值
    def __init__(self, args...):
        # 实例属性的赋值
        self.arg = args[i]
        self.a = args[j]
    # 必须要这样定义实例方法，self 代表实例本身
    def foo(self, args...):
    # 静态方法则不需要
    @staticmethod
    def foo(args...):
    # 必须要这样定义类方法，cls 代表类本身，此时创建实例时更加灵活
    @classmethod
    def foo(cls, args...):

# 有两种方法给 class 的实例赋值
1. class_name['class_attr'] = value
2. class_name.class_attr = value
```

