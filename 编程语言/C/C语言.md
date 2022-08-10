接收字符串(可以含空格)：gets( string );

void main(int argc, char *argv[])：参数计数器argc，等于参数个数加一，参数向量argv

引入头文件用<>时，编译器会在默认的头文件目录中查找该头文件。用""时，会先在当前目录中查找该头文件，之后才到默认头文件目录查找。

i++: 后加

++i: 先加

## @语法

- extern：声明变量或函数是在其它文件或本文件的其他位置定义

## @linux下

### #头文件errno.h

- 变量errno

### #头文件stdio.h

- perror()

### #头文件string.h

- strerror()

### #头文件wait.h

- wait()
- waitpid()

### #头文件unistd.h

#### $进程相关

- fork()

- ##### %exec()函数族

#### $系统调用级函数

- write()
- read()