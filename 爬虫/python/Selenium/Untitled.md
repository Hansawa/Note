## 启动浏览器后如何退出程序（整个）

```python
from selenium import webdriver

browser = webdriver.Edge()
browser.get('http://www.tmdc.org.cn/query.aspx')
browser.quit()
```

