脚本文件被执行时是一条一条执行的，像在终端中输入命令回车执行一样，每执行一个命令都会创建一个进程

输入文件不能是输出文件

ctrl+d：文件结束符，二进制值，EOF，会让输入文本结束，与cat结合使用

系统升级操作：https://www.itcoder.tech/posts/how-to-upgrade-to-ubuntu-20-04/

Ubuntu的版本号为`\d\d.\d\d`，前两个为年份后两位，后两位为该年的迭代版本

Ubuntu最早版本4.10的发布时间2004.10.20

Ubuntu18.04版本在更改地区与语言后会询问是否更改家目录下的文件名称为相应的语言，但目前为止只询问了一次，再更改地区与语言后不在询问了。

man中文文档：manpages-zh

图形界面创建文本文件：https://blog.csdn.net/weixin_42697074/article/details/88827874

## @shell

Shell俗称壳（用来区别于核），为用户提供命令操作界面（命令解析器）

## @文件类型

https://blog.csdn.net/rong09_13/article/details/79233956

- -：普通文件
- d：目录文件
- l：链接文件
- b：块设备文件（硬盘，软盘等）
- c：字符设备文件（串行端口设备：键盘、鼠标等）
- p：管道文件
- s：套接字文件

## @命令行参数

- $0：运行某个shell脚本时所使用的文件名，如果用./file.sh，则显示./file.sh。如果用bash file.sh，则显示file.sh
- $[1-∞]：命令函参数
- $#：除$0外的参数个数
- $@：显示除$0外的所有的参数

## @标准输入输出文件

- ## @各种重要路径

- ~：家目录

- /：根目录

- /usr/local：存放用户自己安装的程序

## @各种重要文件

- Terminal程序所在地址：`/usr/bin/gnome-terminal`
- 当前系统的版本信息：`/etc/redhat-release`（只适用于Redhat系列的系统）
- 当前主机名：`/etc/hostname`
- “零”输入设备：`/dev/zero`，可以无限提供空字符0x00，用来初始化文件
- 记录可以以管理员身份执行命令的用户或组：`/etc/sudoers`https://www.cnblogs.com/betterquan/p/12189796.html
- 创建用户时修改的文件：用户账户信息`/etc/passwd`，密码`/etc/shadow`，用户组`/etc/group`，用户组密码`/etc/gshadow`
- 主机名文件：`/etc/hostname`
- 硬盘分区：/etc/sda1
- 硬盘：/etc/sda
- /proc/version：
- /etc/profile：开机登录进linux时会被执行，配置开机启动项或环境变量

## @权限相关

- 新建的文件的初始权限为rw-rw-rw-，新建的目录的初始权限为rwxrwxrwx，之后与umask异或运算得出最终权限

## @变量

- ${  }：可以取得一个变量的值。如echo ${y}dd意思为取变量y的值连上dd，而echo $yddd的意思是取变量yddd的值

### #系统变量

- RANDOM：产生一个占两字节的正整数。由于产生的数是正整数且系统以补码形式存储数字，因此该数的二进制最高位为0，导致了RAMDOM能产生的最大十进制数为32767
- PATH：export PATH=。。。设置临时环境变量。把他写在~/.bashrc中然后执行`source ~/.bashrc`才能设置成长期环境变量，设置成命令的程序不需要./*来执行了

#### $locale（语言环境）变量

https://www.cnblogs.com/idlo/p/10427409.html

- LANG：指定所有与locale有关的变量的默认值
- LANGUAGE：设置应用程序的界面语言
- LC_CTYPE：语言符号及其分类
- LC_NUMERIC：数字
- LC_COLLATE：比较和排序习惯
- LC_TIME：时间显示格式
- LC_MONETARY：货币单位
- LC_MESSAGES：信息主要是提示信息,错误信息,状态信息,标题,标签,按钮和菜单等
- LC_NAME：姓名书写方式
- LC_ADDRESS：地址书写方式
- LC_TELEPHONE：电话号码书写方式
- LC_MEASUREMENT：度量衡表达方式
- C_PAPER：默认纸张尺寸大小
- LC_IDENTIFICATION：对locale自身包含信息的概述

### #shell变量

- REPLY：

## @退出码（exit x）

- https://blog.csdn.net/nicai_xiaoqinxi/article/details/85055086

## @shell脚本解析器

- sh：最原始的解析器，无法识别双等号
- bash：常用解析器
- dash：
- 三个解析器的区别：https://blog.csdn.net/weixin_39212776/article/details/81079727

## @ctrl+r，ctrl+j

- `ctrl+r`：历史命令查询
- `ctrl+k`：取消查询

## @网络配置

### #连接方式

#### $桥接网卡

- 使用该方式时，只需将IPv4的获取方式设置成DHCP即可连接网络

#### $网络地址转换（NAT）

#### $仅主机（Host-Only）网络

- 使用该方式时，根据虚拟机软件Host-Only network（网关）的IP地址与子网掩码，手动填写虚拟机的IP地址与子网掩码，注意虚拟机软件Host-Only network与虚拟机的网络号要一致，通过以上设置即可使宿主机连接上虚拟机
- 虚拟机软件Host-Only network在`网络连接`窗口