## @解决闲置超时中断连接的问题

### #客户端解决方法：

1. 可以修改配置文件config（windows：家目录->.ssh目录->config文件，没有的话创建一个），添加

```
host *(域名或IP)
	ServerAliveInterval (秒数)
	ServerAliveCountMax (次数) #非必须
```

​		保存即可。

2. 也可以连接时添加选项：

```
ssh -o serveraliveinterval=(秒数) 服务器端用户名@域名或IP
```

### #原因：

https://www.jianshu.com/p/92d60c6c92ef