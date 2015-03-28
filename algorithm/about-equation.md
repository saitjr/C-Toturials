# 不定方程求整数解问题

##爱因斯坦的数学题

爱因斯坦出了一道这样的数学题：有一条长阶梯，若每步跨2阶，则剩最后1阶；若每步跨3阶，则剩最后2阶；若每步跨5阶，则剩最后4阶；若每步跨6阶，则剩最后5阶；只有每步跨7阶，才一阶不剩。请问，这条阶梯一共有多少阶？

思路：首先，这里肯定需要一个循环进行穷举，如果满足题目所有条件则跳出。因为不确定具体循环次数，所以选择使用while。

知识点：循环与各个循环的特点。

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    
    int number = 7;
    
    while (1) {
        
        if (number % 2 == 1 && number % 3 == 2 && number % 5 == 4 && number % 6 == 5 && number % 7 == 0) {
            
            printf("阶梯有%d阶", number);
            break;
        }
        number ++;
    }
    
    return 0;
}

```

##百钱百鸡问题

中国古代数学家张邱建在他的《算经》中提出了著名的“百钱百鸡问题”：鸡翁一，值钱五；鸡母一，值钱三；鸡雏三，值钱一，百钱买百鸡，问翁，母，雏各几何？

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    
    for (int male = 0; male <= 20; male ++) {
        
        for (int female = 0; female <= 33; female ++) {
            
            int child = 100 - male - female;
            
            if (child % 3 != 0) {
                
                continue;
            }
            if (child / 3 + male * 5 + female * 3 == 100) {
                
                printf("公鸡 = %-6d母鸡 = %-6d小鸡 = %-6d\n", male, female, child);
            }
        }
    }
    
    return 0;
}

```
