# 与数字有关的程序

##1. 四位反序数

设N是一个4位数，它的9被恰好是其反序数，求N。（反序数即数字倒过来的形式：1234的反序数为4321）

思路：使用穷举法，将所有的四位数一一列出，然后把该四位数的每一位取出，乘以逆向以后的倍率，如果等于该数的9倍，则满足条件。

知识点：循环，分支，取模运算与除法运算结合得到每一位的数字。

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    
	for (int i = 1000; i < 9999; i ++) {
	   
	   if (i % 10 * 1000 + i / 10 % 10 * 100 + i / 100 % 10 * 10 + i / 1000 == i * 9) {
	       
	       printf("%d ", i);
	   }
	}
    
	return 0;
}

```

##2. 完全数

如果一个数恰好等于它的因子之和，则该数成为“完全数”，求1000以内的完全数。（如：6 = 1 + 2 + 3）。

思路：首先需要一层循环来穷举1~1000所有的数字，然后还需要一层循环来求出每一个的因子，然后将因子相加，若等于该数，则满足条件。

知识点：循环。

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    
    for (int i = 1; i <= 1000; i ++) {
        
        int sum = 0;
        
        for (int j = 1; j < i; j ++) {
            
            if (i % j == 0) {
                
                sum += j;
            }
        }
        if (sum == i) {
            
            printf("%d ", i);
        }
    }
    
    return 0;
}

```

##3. 哥德巴赫猜想

任一大于2的偶数，都可表示成两个素数之和。请验证，该猜想在1000~1100成立。

思路：穷举法列出1000~1100之间的每一位数（注意循环步长为2，因为题目说明是偶数），然后使用一层循环从2开始，判断N = 2 + (N - 2)中2与(N-2)是否均为素数，然后判断N = 3 + (N - 3)，以此类推，直到满足条件为止。

知识点：循环，自定义函数，素数。

```c

#include <stdio.h>
#include <math.h>

/**
 *  判断是否是素数
 *
 *  @param number 需要进行判断的数字
 *
 *  @return 是否是素数  1:是  0:不是
 */
int isPrimeNumber(int number) {
    
    for (int i = 2; i <= sqrt(number); i ++) {
        
        if (number % i == 0) {
            
            return 0;
        }
    }
    return 1;
}

int main(int argc, const char * argv[]) {
    
    for (int i = 1000; i <= 1100; i += 2) {
        
        for (int j = 2; j <= i; j ++) {
            
            // 判断当前加数与被加数是否均为素数
            if (isPrimeNumber(j) && isPrimeNumber(i - j)) {
                
                // 输出其中一种情况
                printf("%d = %d + %d\n", i, j, i - j);
                break;
            }
        }
    }
    
    return 0;
}

```

##4. 阵列

输出一下结构，如N = 3：

```
1 2 3
8 9 4
7 6 5

```

