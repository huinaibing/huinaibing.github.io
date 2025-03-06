---
layout: post
title: 闭着眼睛学Linux
permalink: /cs/linuxlearning
usemathjax: true
---

> 本笔记基于尹航老师与张清国老师的课件，主要是shell编程，基本命令懒得写

# 简单的shell

一个shell通常开头要

```
#! /bin/sh
```

这个用`#! /bin/bash`貌似也可以，但是我经常不写这个

写完后需要`chmod`一下，这样可以使用`./`去执行，但是我直接`sh shell.sh`这样省事

# 反引号

![image-20250305173239652](/img/linuxlearning/image-20250305173239652.png)

![image-20250305173345921](/img/linuxlearning/image-20250305173345921.png)

# 变量

## 自定义（用户变量）和环境变量

显然分为自定义变量和环境变量，通常字母全部大写，这个是编程习惯不遵守也行

```
$VARIABLE=value
```

上面的定义不能加空格，要加的话也要用`“”`引号

![image-20250304132035479](/img/2025-03-04-Linux-Learning/image20250304132035479.png)

显然，shell把它当成命令了

![image-20250304132118538](/img/2025-03-04-Linux-Learning/image20250304132118538.png)

同理，shell把1当成命令了

输出变量在前面加$

```
echo $MYVAL
echo ${MYVAL}
```

![image-20250304132349015](/img/2025-03-04-Linux-Learning/image20250304132349015.png)

注意的这里的command not found，这说明shell直接把$MYVAL当成指令了，显然这个可以用于简化一些编程操作

`unset`可以删除一个变量，`set`不带参数可以显示所有变量（包括用户的），`env` `printenv`也可以，但是只**显示系统的**

![image-20250304132842429](/img/2025-03-04-Linux-Learning/image20250304132842429.png)

变量可以设置默认值

```
${color:-grey}
${color:=grey} # 和上面的不同是，这个会直接把value给变量
```

![image-20250305145944432](/img/linuxlearning/image-20250305145944432.png)

---

环境变量大多是在`/etc/profile`中的，也可以在命令行定义

## 位置变量

![image-20250305150536060](/img/linuxlearning/image-20250305150536060.png)

一目了然，但是缺点是只能访问9个，访问后面的要用shift命令

## 预定义变量

![image-20250305151015368](/img/linuxlearning/image-20250305151015368.png)

# 条件判断

```
[ condition ]
# condition两边要有空格，里面的操作数操作符号都要空格
```

逻辑操作符：

- -a 与
- -o 或
- ！非

数值比较符

- -eq # equal
- -ne # not equal
- -gt # greater than
- -lt # less than
- -le # less equal
- -ge # greater equal

字符串比较 / 判断

- =
- !=
- -z # 字符串为空
- -n # 字符串非空

文件判断（下面条件对上了就返回真）

- -r # 文件存在且可读
- -w # 存在且可写
- -x # 存在且可执行
- -s # 存在且文件里面至少有一个字符
- -d # 存在且这是个目录
- -e # 文件存在就行
- -f # 存在且为普通文件
- -c # 存在且为字符型特殊文件
- -b # 块特殊文件

# 数据处理

变量都是字符串存储的，所以不好计算数值，掌握下面几个就好

- `let`
- `$((expression))`

![image-20250305154200700](/img/linuxlearning/image-20250305154200700.png)

用let，表达式中不能有空格，因为空格表示它是多个表达式，非要用空格就加双引号

![image-20250305154354238](/img/linuxlearning/image-20250305154354238.png)

$(())这个有没有空格无所谓

# 控制流

## if

```sh
if expression
	then
	dosth
fi

if expression; then
	dosth
	elif expression; then
		dosth
	else
		dosth
fi
	
```

## case

```sh
case test-string in
	mode1) dosth
	;;
	mode2) dosth
	;;
esac
```

可以使用通配符（*）

## for

```sh
for i in iterable
do
	dosth
done
```

有几种生成iterable的方法

- seq 
- {1..5}

## while 

```sh
while expression
do
	dosth
done
```

expression 中可以放read， 这样可以让用户输入东西

# 函数

```sh
function fuctionname
{
	dosth
}

functionname()
{

}
```

调用的时候可以传参数，然后在函数中调用参数的方法就是用`$1 $2`

函数返回值有三种方式

- 函数中最后一条命令的运行状态`$?`

- 使用return，拿到这个return的方法`$?`
- 使用函数输出

# shell内部命令

![image-20250305173700848](/img/linuxlearning/image-20250305173700848.png)

![image-20250305173711254](/img/linuxlearning/image-20250305173711254.png)

![image-20250305173718713](/img/linuxlearning/image-20250305173718713.png)

# grep

在文本中搜索字符串

```sh
grep match_pattern file_name
```

# 管道

将一个命令的输出给另一个输入

```sh
command1 | command2 | command3
```

# tee

```sh
tee [-a] [-i] [文件]
```

-a表示在后面追加，没有这个就会覆盖文件

# 文件重定向

![image-20250305174429255](/img/linuxlearning/image-20250305174429255.png)

```
> <
# 这个重定向符号，尖口对应着数据流向，表示把数据从一个给定东西给另外一个东西
```

```
commad 2> error-file
# 上面代表把command的错误输出放入error-file
command 1> output 2>&1
# 把标准输出放入output同时把标准错误放入和1一样的地方
command <input >output
# command从input拿数据，输出放到output
```

以上默认覆盖文件，若是要追加就使用`<< >>`

若是懒得慌，就使用永久的重定向

```
exec 1> testout
```

也可以使用3-9创建一个永久输出/输入端口，为什么不能用123？因为被占用了

```sh
exec 3>testoutput
echo "114514" >&3
```

永久的重定向怎么恢复？搞一个备份！

```
exec 3>&1
exec 1>test
...
...
exec 1>&3
```

你甚至可以使用这个玩点花的

```
bash <first.sh
```

# printf

```
printf "%d%c%s..." $the_value_you_want_use
```

![image-20250306160916923](/img/linuxlearning/image-20250306160916923.png)
