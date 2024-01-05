# 动态内存管理
## 原则
谁申请谁释放
## 申请内存位置
在堆空间上进行申请
## 一个内存泄露的例子
```c
include "stdio.h"
#include "stdlib.h"
#include "string.h"

#define M 3
#define N 4

int func(int *p, int n)
{
    p = malloc(n); // p局部变量内容，返回作用域则限制，本质值传递；   
    if (p == NULL)
    {
        exit(1);
    }

    return 0;
}

void main()
{
    int *p = NULL;
    func(p, N);
    if (p == NULL)
    {
        printf("oom !!");
    }

    free(p);

    exit(0);
}

# output
oom !!

#修改解决oom
#include "stdio.h"
#include "stdlib.h"
#include "string.h"

#define M 3
#define N 4

int func(int **p, int n)
{
    *p = malloc(n);
    if (*p == NULL)
    {
        exit(1);
    }

    return 0;
}

void main()
{
    int *p = NULL;
    func(&p, N);
    if (p == NULL)
    {
        printf("oom !!");
    }

    free(p);

    exit(0);
}

```

