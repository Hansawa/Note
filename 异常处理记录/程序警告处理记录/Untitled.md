# !console

## @Warning: the ECDSA host key for 'hansarchive.top' differs from the key for the IP address '112.74.47.41', Offending key for IP in C:\Users\Hans/.ssh/known_hosts:1, Matching host key in C:\Users\Hans/.ssh/known_hosts:2

### ＃解决方案：

windows：将`家目录\.ssh\known_hosts`文件中属于相同的主机IP或域名的密码的那一行删除

### #原因：

相同IP或域名的密钥不一致所产生的冲突