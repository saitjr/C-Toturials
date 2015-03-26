# 结构体的定义与使用

在学习语言的时候，做的最多的就是学生成绩管理系统。里面包含的数据类型丰富、拥有基本的CRUD操作，是一个比较经典的例子。那么，我们结构体的学习，也将使用这个例子。

##结构体的定义

由学生成绩管理系统的例子不难看出，学生的诸多属性（学号、姓名、年龄、成绩等）构成了学生这个结构体。结构体定义需要用到关键字`struct`，定义规则如下：

```
struct 结构体名称 {

    // 成员列表
}; // 注意：末尾有;

```
如，一个学生结构体：

```
struct Student {

    char *studentId;    // 学生学号
    char *name;         // 学生姓名
    int age;            // 学生年龄
    double score;       // 学生成绩
};
```
因此，如果我们对每一个Student结构体变量进行初始化，都会有学号、姓名、年龄、成绩这几个成员。

##结构体类型变量

定义结构体变量定义的方式有很多种：

###1. 定义结构体后，定义变量(最优)

```
struct Student {

    char *studentId;
    char *name;
    int age;
    double score;
};

struct Student stuA, stuB; // 定义结构体变量stuA、stuB

```

###2. 在定义结构体时，定义变量

```
struct Student {

    char *studentId;
    char *name;
    int age;
    double score;
} stuA, stuB; // 定义结构体变量stuA、stuB

```

###3. 直接定义变量

```
struct {

    char *studentId;
    char *name;
    int age;
    double score;
} stuA, stuB; // 定义结构体变量stuA、stuB

```
##结构体变量初始化

结构体只能在定义的时候，能为<font color=red>整个</font>结构体变量进行赋值。

```
struct Student {

    char *studentId;
    char *name;
    int age;
    double score;
};

struct Student stuA = {"11310110", "Karen", 15, 100};

// 下面这种写法是错误的，定义与整体初始化不能分开

struct Student stuB;
stuB = {"11310110", "Karen", 15, 100};

```

##结构体成员的访问

在实际操作中，不可能定义一个结构体变量就能整体初始化。这时，我们只能单个对结构体的成员进行访问，如：


```
struct Student {

    char *studentId;
    char *name;
    int age;
    double score;
};

struct Student stuA;

stuA.studentId = "11310110";
stuA.name = "Karen";
stuA.age = 15;
stuA.score = 100;

// 输出

printf("学号是:%s\n", stuA.studentId);
printf("姓名是:%s\n", stuA.name);
printf("年龄是:%d\n", stuA.age);
printf("成绩是:%lf\n", stuA.score);

// 整体赋值：将stuA的数据整体赋值给stuB

struct Student stuB = stuA;

```

##结构体变量所占内存大小

在结构体内存的计算上，有一个*自动对齐原则*，如，Student这个结构体中，所占内存最大的成员是`char *`或`double`类型，那么结构体所占的内存大小 = 成员个数 * 成员中占用最大的字节数。

如上面的学生结构体 = `4 * sizeof(char *) = 32`
