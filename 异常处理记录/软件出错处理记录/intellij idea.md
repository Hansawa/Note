## @tomcat日志信息乱码

解决方案

1. 修改tomcat根目录下conf文件夹下的logging.properties文件中`java.util.logging.ConsoleHandler.encoding`的值为`GBK`.
2. 打开idea的setting`(ctrl+alt+s)`，搜索`console`，更改`Default Encoding`为`UTF-8`

原理：tomcat的日志信息在cmd产生，而cmd所使用的字符集与idea在console输出信息所使用的字符集不一致，导致了console输出中文会乱码，此时只要将双方统一字符集即可解决。

## @创建了java web工程与添加了tomcat后运行工程，网页提示404

解决方案：在添加tomcat时部署网站即可

原理：没部署网站能打开什么？

## @无法打开后缀为.md的markdown文件

解决方案：`Settings->Editor->File Type->markdown`，添加检测后缀`*md`

原理：原先idea没有设置检测后缀为`*md`的文件为markdown文件

## @未解决

- .properties文件的属性显示为灰色