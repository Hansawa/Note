## 获取文件路径

```python
os.path.join(os.getcwd(), "utils", "crawlers_util.py")
```



```cmd
# 以绝对路径运行
# C:\Python364\python.exe C:/PyCharm/PycharmProject/get_path/path_demo.py
sys.path[0] =  C:\PyCharm\PycharmProject\get_path
sys.argv[0] =  C:/PyCharm/PycharmProject/get_path/path_demo.py
__file__ =  C:/PyCharm/PycharmProject/get_path/path_demo.py
os.path.abspath(__file__) =  C:\PyCharm\PycharmProject\get_path\path_demo.py
os.path.realpath(__file__) =  C:\PyCharm\PycharmProject\get_path\path_demo.py
os.path.dirname(os.path.realpath(__file__)) =  C:\PyCharm\PycharmProject\get_path
os.path.split(os.path.realpath(__file__)) =  ('C:\\PyCharm\\PycharmProject\\get_path', 'path_demo.py')
os.path.split(os.path.realpath(__file__))[0] =  C:\PyCharm\PycharmProject\get_path
os.getcwd() =  C:\PyCharm\PycharmProject\get_path
```



```cmd
# 以相对路径运行
# C:\PyCharm\PycharmProject\get_path>python path_demo.py
sys.path[0] = C:\\PyCharm\\PycharmProject\\get_path
sys.argv[0] = path_demo.py
__file__ = path_demo.py
os.path.abspath(__file__) = C:\\PyCharm\\PycharmProject\\get_path\\path_demo.py
os.path.realpath(__file__) = C:\\PyCharm\\PycharmProject\\get_path\\path_demo.py
os.path.dirname(os.path.realpath(__file__)) = C:\\PyCharm\\PycharmProject\\get_path
os.path.split(os.path.realpath(__file__)) = ('C:\\PyCharm\\PycharmProject\\get_path', 'path_demo.py')
os.path.split(os.path.realpath(__file__))[0] = C:\\PyCharm\\PycharmProject\\get_path
os.getcwd() = C:\\PyCharm\\PycharmProject\\get_path
```

python 使用引用计数策略来进行垃圾回收
