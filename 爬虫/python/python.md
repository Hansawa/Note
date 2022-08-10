pip：是python官方提供并维护的第三方库安装工具，在shell中使用

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

