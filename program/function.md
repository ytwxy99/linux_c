# 函数与二维数组
```c
#include "stdio.h"
#include "stdlib.h"
#include "string.h"

#define M 3
#define N 4

void print_arry(int *p, int n)
{
    for (int i = 0; i < n; ++i) {
        printf("%d\n", p[i]);
    }
}

int main(void)
{
    int arr[M][N] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
    print_arry(&arr[0][0], M*N);
    
    exit(0);
}
```

# 函数与指针
## 指针函数
函数返回的是指针
如：int * fun(int);
## 函数指针


```c

```
