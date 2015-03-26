# 结构体指针

##指向结构体变量的指针

与指向基本类型的指针类似，结构体指针指向的是一个结构体变量的地址。定义方式为：

```c
struct 结构体名称 *指针变量名;

```
如，定义一个指向学生结构体的指针：

```c
struct Student {
    
    char *studentId;
    char *name;
    int age;
    double score;
};

struct Student *pStu; // 定义结构体指针

```

##结构体指针的赋值与访问

###赋值

```c
struct Student {
    
    char *studentId;
    char *name;
    int age;
    double score;
};

struct Student *pStu; // 定义结构体指针

// 赋值

struct Student stu = {"11310110", "Karen", 15, 100}; // 定义结构体变量
pStu = &stu; // 将结构体变量stu的首地址给指针pStu

```

###访问

结构体指针访问成员的方式有两种：

####1. 先取`*`然后访问

```c
printf("学生%s的年龄为%d\n", (*pStu).name, (*pStu).age);
// 输出：学生Karen的年龄为15

```

####2. 使用`->`访问

```c
printf("学生%s的年龄为%d\n", pStu->name, pStu->age);
// 输出：学生Karen的年龄为15

```