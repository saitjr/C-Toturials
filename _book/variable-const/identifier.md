# 字符集

C语言的字符集分为六类：标识符，关键字，运算符，分隔符，常量，注释符。本讲讲关键字与标识符，其余几个平时用的过程中就能理解。

##关键字

在C语言中，系统已经占用了一些字符，这些字符有特殊含义，我们不能进行重复命名，这就是关键词。

C语言一共有32个关键字（都是小写），不用特别记忆。在之后的编码中，天天都要和这些关键字打交道，并且他们能编辑器里面（如Sublime Text，Notepad++等）都会高亮进行显示（当然，IDE也会高亮显示）。

```c
auto double int struct break else long switch
 
case enum register typedef char extern return union

const float short unsigned continue for signed void
 
default goto sizeof volatile do if while static

```

##标识符

在程序中使用的变量名、函数名、标号等统称为标识符。除库函数的函数名由系统定义外,其余都由用户自定义。

标识符由数字`0~9`、字母`a~z A~Z`、下划线组成`_`。

命名规则：

1. <font color=red>不能以数字开头</font>，错误示例：`0abc`；
2. <font color=red>不能与关键字重复</font>，错误示例：`int`；
3. <font color=red>区分大小写</font>，`abc`与`ABC`不同；
4. <font color=red>不能出现除数字、字母、下划线以外的字符</font>，错误示例：`a!bc`。