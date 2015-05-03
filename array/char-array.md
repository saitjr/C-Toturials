# 字符串

在C语言中没有专门的字符串变量，通常用一个字符数组来存放一个字符串（字符数组即元素为字符的数组）。<font color=red>并且将`\0`作为结束标志。</font>

## 字符串定义

```c
char string[10];
```
因为最后一位`string[9]`要留给`\0`，所以对于`string`来说，有效位应该是9位。

```c
char string[] = {'a', 'b', 'c', 'd'};
char string[] = "abcd";
```
对于这种情况，系统会自动在末尾加上`\0`。

## 输入输出

输入输出的方法有很多，其中也可以像普通一维数组一样访问，这里不再举例。

其他访问方式如下：

```c
char string[10] = {};

// 注意：这里的string本身已经是地址了，所以不用再&string
// 弊端：scanf是以空格作为结束的，所以这里输入的字符串不能有空格
scanf("%s", string);
printf("%s", string);

// 注意：这种方式在xcode下有警告
gets(string);
puts(string);
```

## 字符串相关库函数

比起普通的一维数组，字符串的处理要方便得多。原因还是要归功于众多的系统库函数。下面将介绍几种常用的系统库函数。

使用之前，需要引入头：

```c
#include <string.h>
```
所有的字符串库函数均将`\0`作为结束标志，所以使用前，要确定最后一位是`\0`。

### `strlen`

功能：计算字符串长度

```c
char string[10] = "abc";
int length = strlen(string);
printf("length = %d", length); // 输出3
```

注意下面这种结束标志的位置：

```c
char string[10] = {'a', 'b', '\0', 'c', 'd'};
int length = strlen(string);
printf("length = %d", length); // 输出2，因为提前出现了\0
```

### strcat

功能：把string2中的字符串连接到string1 中字符串的后面，并删去string1后的串标志“\0”。本函数返回值是string1的首地址。

<font color = red>注意：因为字符串会直接拼接给string1，所以要确保string1的长度够长，至少能装下拼接过来的string2。</font>

```c
char string1[10] = "abc";
char string2[] = "def";
    
strcat(string1, string2);
puts(string1);
```

### strcpy

功能：字符串拷贝，将string2拷贝给string1（把后一个拷贝给前一个）。

```c
char string1[10] = {};
char string2[] = "def";
    
strcpy(string1, string2);
puts(string1);
```

### strcmp

功能：字符串比较。通过ASCII，比较两个字符串的大小。根据编译器不同，有的返回-1, 0, 1；有的返回相差多少（Clang返回相差多少）。

```c
char string1[10] = "abc";
char string2[] = "ard";
    
int a = strcmp(string1, string2);
printf("%d", a); // 输出-16
```

## 使用

练习：

> 统计单词个数，以空格区分