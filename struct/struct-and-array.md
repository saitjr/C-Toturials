# 结构体数组

和之前学习数组的目的一样，在学生管理系统中，不可能一个一个学生去定义并初始化，所以引入了数组的概念。

##结构体数组的定义

与结构体变量定义一样，结构体数组的定义也有三种方式：

###1. 定义结构体后，定义数组(最优)

```c
struct Student {
    
    char *studentId;
    char *name;
    int age;
    double score;
};

struct Student stu[10]; // 定义一个长度为10的结构体数组

```

###2. 在定义结构体时，定义数组

```c
struct Student {
    
    char *studentId;
    char *name;
    int age;
    double score;
} stu[10];  // 定义一个长度为10的结构体数组

```

###3. 直接定义数组

```c
struct {
    
    char *studentId;
    char *name;
    int age;
    double score;
} stu[10];  // 定义一个长度为10的结构体数组

```

##结构体数组的赋值与访问

```c

struct Student students[10];
    
for (int i = 0; i < 10; i ++) {
    
    students[i].age = i;
}

for (int i = 0; i < 10; i ++) {
    
    printf("第%d个学生的年龄 = %d\n", i + 1, students[i].age);
}

```


