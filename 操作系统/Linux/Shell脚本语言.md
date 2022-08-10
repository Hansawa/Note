true命令返回0，false命令返回1

## @case

### #一般格式

```shell
case $var in
	pattern1 | pattern2 | ...) statements;;
	pattern3 | pattern4 | ...) statements;;
	...
	*) statements;;
esac
```

## @if

### 	#一般格式

```shell
if [ 条件测试式 ]; then
elif [ 条件测试式 ]; then
else
fi
```

## @for

### #一般格式

#### $第一种

```shell
for i in string1 string2 string3 ...
do
statements
done
```

#### $第二种

```shell
#char1与char2是一个数字或字母序列的头尾值
for i in {char1..char2}
do
statements
done
```

#### $第三种

```shell
#seq num1 num2: 输出一个从num1到num2的正整数序列，如果只有num1，则该序列从1开始排列
for i in $(seq num1 num2)
do
statements
done
```

#### $第四种

```shell
#类高级语言for循环
for (( ; ; ))
do
statements
done
```



## @until

判断为假，继续循环

## @while

判断为真，继续循环

## 		@测试框样式

- test：与[  ]一致
- [  ]：1.不能用>< 2.最古老的
- [[  ]]（只有bash能用）：1.可以使用正则表达式 2.可以用逻辑运算（与或非）
- (())：1.只能整数比较 2.可以不用空格 3.可以使用逻辑运算 4.可以使用><= 5.像c语言一样 6.可以不写美元符

## @条件测试式

- -z $string: 字符串长度为零
- -n $string：字符串长度大于零
- $string：string不为空
- 其中-n $string与$string相同
- ![image-20201209192503005](C:\Users\Hans\AppData\Roaming\Typora\typora-user-images\image-20201209192503005.png)

## @注释写法

- https://jingyan.baidu.com/article/08b6a591fa1dc655a80922d5.html

如果file存在，则删除：[ -e $file ] && rm $file