#### cmd

命令提示符

#### cmd shell

命令提示符 shell，shell 意为壳，包裹着计算机操作系统的内部，用户只能通过壳来与操作系统内部进行交互，与图形用户界面类似的作用

#### cmd 文件

windows 命令（提示符）脚本文件（.cmd），与批处理文件（.bat）一样，都是批处理文件（一批命令执行，或处理一批文件）

#### 如何执行 cmd 文件

##### 直接双击该文件

##### 在 CMD shell 或 PowerShell 中执行该文件

1. 设置环境变量，让系统知道在哪里找到该 cmd 文件，或直接在 shell 进入 cmd 文件所在目录

2. 在命令行界面输入该 cmd 文件名（可以加上后缀 .cmd）即可执行该 cmd 文件

#### cmd 常用语法

md <file>：创建文件

del <file>：删除某文件

findstr ：模式匹配（字符串匹配）

`%~dp0`：表示当前执行目录

#### 查看某命令的帮助文档

help <command> 或 <command> /?

#### 命令总表

[Windows 命令 | Microsoft Docs](https://docs.microsoft.com/zh-cn/windows-server/administration/windows-commands/windows-commands#command-line-reference-a-z)

#### 命令行参数

cmd shell 中执行程序（.exe, .o（c文件编译后的目标文件）, ...）时可在其后添加命令行参数，以数组（argv）形式传入程序中，其中：

1. argv[0]：运行该程序时的地址（绝对，相对）

2. argv[1~∞]：执行程序时在其后添加的各个命令行参数

#### cmd 文件与批处理文件不在 shell 显示执行的命令或产生的结果

1. @<command>...：不显示该行命令

2. echo off：显示该行，但不显示接下来的命令与结果

3. 合并1，2得 @echo off：不显示该文件所执行的命令与产生的结果
