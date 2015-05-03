# 二维数组

二维数组可以看成多个一维数组，即用数组作为元素的数组。

## 二维数组的定义

`类型说明符 数组名[常量表达式1][常量表达式2];`

即：

```c
int sz[3][4];
```
这里声明一个三行四列的数组，一共能表示12个整型。具体访问下标如下：

![](./images/two-dimensional-array-1.png)

## 二维数组的初始化

### 初始化全部元素

```c
int sz[2][3] = {{0, 1, 2}, {3, 4, 5}};

// 0 1 2
// 3 4 5
```

### 初始化部分元素

```c
int sz[2][3] = {{1}, {2}};

// 1 0 0
// 2 0 0

// 或

int sz[2][3] = {0};
```

### 缺省第一个长度

如果数组的长度已经确定，初始化时，可以缺省第一个长度。

```c
int sz[][3] = {{0, 1, 2}, {3, 4, 5}};

// 或

int sz[][3] = {0, 1, 2, 3, 4, 5};
```

上面这个例子中可以看出，二维数组可以像一维数组一样进行初始化。<font color=red>因为在C语言中，二维数组是按行排列的。</font>即，先存放sz[0]行，再存放sz[1]行，每行中有三个元素也是依次存放。

## 二维数组的应用

按照下表，求出各科总分与每个学生的总分。

![](./images/two-dimensional-array-2.png)

```c
int main(int argc, const char * argv[]) {
    // insert code here...
    
    int scores[3][3] = {{23, 45, 67}, {12, 56, 89}, {45, 89 ,19}};
    
    for (int i = 0; i < 3; i ++) {
        
        int sumOfStudent = 0;
        int sumOfCourse = 0;
        
        int j = 0; // j 需要在循环外进行输出，所以定义到外面
        
        for (; j < 3; j ++) {
            
            // 注意i和j分别表示什么
            sumOfStudent += scores[i][j];
            sumOfCourse += scores[j][i];
        }
        printf("第%d个学生的总分 = %d\n", i, sumOfStudent);
        printf("第%d门课程的总分 = %d\n\n", i, sumOfCourse);
    }
    
    return 0;
}
```

练习：

> 有一个3 * 4的矩阵，求出最大的那个元素的值，并输出行号和列号

