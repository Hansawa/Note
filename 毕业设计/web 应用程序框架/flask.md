## 最小应用

```python
from flask import Flask
app = Flask(__name__)
@app.route('/')
def index():
	return '<h2>Welcome to my website</h2>'
if __name__ == '__main__':
    app.run()
```

## 热部署

```python
from flask import Flask
app = Flask(__name__)
if __name__ == '__main__':
    # 允许程序进行热部署
    app.run(debug=True)
```

## 对象

1. [g](http://www.coolpython.net/flask_tutorial/basic/flask-g.html): 它是global的缩写，g是全局变量，在整个request生命周期内生效，当一次请求深度调用了许多方法，那么这些方法可以用 g 来共享一些变量。

   ```python
   from flask import Flask, g
   app = Flask(__name__)
   @app.route('/')
   def index():
       g.a = 1
       process()
   	return '<h2>Welcome to my website</h2>'
   def process():
       print(g.a) # >>> 1
   if __name__ == '__main__':
       app.run()
   ```

   

