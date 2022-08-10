+ 查看IP配置信息：`ifconfig`
+ 查看内核版本（以及位数）：`uname -a`
+ 查看linux发行版的版本：`lsb_release -a`[codename:发行版本的别名]

## @netstat命令

netstat -lntp：查看被占用的端口

## @tar命令

tar -zxvf [tar压缩包]

## @apt命令

### #apt-cache

1. apt-cache search [软件名]：查找某一软件

## @find命令

find 搜索路径 [选项] 搜索内容

选项内容：http://c.biancheng.net/view/779.html

## @alias

给命令设置别称：alias 别称="命令"

## @locale

显示所有语言环境变量

- -a：查看可用的语言环境变量的值。格式：`language_territory`
- -av：查看可用的语言环境变量值的详述文本

## @可以查看文件类型的命令

- ls -l
- file
- stat

## @ls命令

- -p：给目录文件末尾添加/指示器

## @![image-20201215131759128](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20201215131759128.png)

往组里添加用户时，要重启才生效

## @dos2unix命令

- 将采用dos/windows格式的纯文本文件转成nuix格式（区别：dos/windows格式的换行符为`\r\n`，而nuix格式的换行符为`\n`）
- 有一个反向转换的命令`unix2dos`

## @grep命令

最好用`''`把者则表达式框起来，抑制某些shell扩展

- grep -P：实用报表提取语言正则表达式，即扩展的正则表达式，不扩展的话许多元字符与POSIX字符类无法使用
- grep -E：扩展正则表达式，但比-P扩展的少
- egrep：与`grep -E`一致

## @man命令

- man -f 命令：显示所有与命令名相同的文件
- man 数字 命令：显示某一命令的介绍，默认为1
- https://blog.csdn.net/gatieme/article/details/51656707
- man中文文档：manpages-zh

## @history命令

查询以前的命令

- !数字：使用history中数字行的命令

## @yum命令

+ 显示已安装与未安装的程序包：`yum list *`

## @cat命令（文件合并命令）

- cat [ 文件名 ] [ 文件名 ] ... [ 文件名 ] > [ 文件名 ]：把前面的文件内容合并到后面的文件
- cat > [ 文件名 ]：可从终端输入字符并按回车将那一行输出到[ 文件名 ]

## @Vim命令

- -b：二进制模式，可以看见一些平时看不见的脱字符

+ 向后查找：`:/*`
+ 向前查找：`:?*`
+ 连续查找：向后n，向前N
+ 取消查找：`:noh`
+ 复制n行：nyy
+ 粘贴：p
+ 剪切一行：dd
+ 打开多个文件：vs. https://www.cnblogs.com/chenmo-xpw/p/5954919.html
+ v可视模式下复制多行：y复制，p粘贴，c剪切，shift+>右移
+ 字符串替换：`:行号，行号s/string1/string2/` 替换两行号之间所有的 string1 为 string2
+ 字符串替换：`:s/string1/string2/` 替换当前行的 string1 为 string2
+ 字符串替换：`:%s/string1/string2/g` 替换所有的 string1 为 string2
+ ga：可以显示光标所在字符的ascii编码

## @read命令

```shell
read -p "  " #在输入时显示信息
read -s	   #安静模式，不显示输入字符
```

## @echo命令

```shell
echo -e "  " #可以识别字符串中的转义字符
echo $? #可以返回上一个退出码（退出码：exit x）
```

## @su与sudo命令

```shell
su userName #登录用户
su - userName #切换用户
```

## @jps命令

```shell
jps #是jdk提供的查看当前java进程的小工具
```

## @**命令扩展**

- 字符串扩展：“ ”或‘ ’【“  ”不抑制$，\，`的扩展，‘  ’抑制所有扩展】
- 算数扩展(只能算整数)：$((  ))。括号内写算数式，如$((1+2))，输出3【如果直接写1+2程序会当成字符串】
- 命令扩展：$(  )。先执行括号内命令（如果用“ string ”的话会被当成一个命令而可能会发生错误），再将执行后的返回值格式化(一般是把回车或多个空格转换为一个空格)显示

## @bc命令

规则：1. 先设置obase(2, 8, 10, 16)，再设置ibase. 2. 16进制字母要大写

## @用户操作

- 删除用户：userdel -r 用户名

