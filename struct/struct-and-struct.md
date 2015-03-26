# 结构体的嵌套

比如，现在有这样一个需求：

> 定义一个人的结构体，有姓名、出生日期等成员，应该怎么定义？

或许可以这样定义：

```c
struct Person {

	char *name;
	int year;
	int month;
	int day;
};

```

这样也可以，但是我认为这个设计不好，年月日应该是日期的成员，怎么会是一个人的成员呢！所以，有了以下定义：

```c
struct Date {
	
	int year;
	int month;
	int day;
};

struct Person {

	char *name;
	struct Date birth;
};

```

##结构体嵌套的赋值与访问

```c
// 定义结构体变量

struct Person me;

me.name = "Karen";
me.birth.year = 2000;
me.birth.month = 1;
me.birth.day = 1;

```
