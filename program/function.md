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
    返回值 * 函数名 (形参)；
    如：int * fun(int);
## 函数指针
指针指向的是函数
    类型 (*指针名) (形参);
    如：int (*p)(int);
```c
int add(int a, int b)
{
    return a + b;
}

int main()
{
    int a = 3, b = 5;
    int ret;
    //ret = add(a, b);
    int (*p) (int, int);
    p = add; // 函数名是一段代码所关联的入口地址
    ret = p(a, b);
    printf("%d \n", ret);
}
```
## 函数指针数组

    类型 (*数组名[下标]) (形参);
    如： int (*arr[N]) (int);

```c
int add(int a, int b)
{
    return a + b;
}

int sub(int a, int b)
{
    return a - b;
}

int main()
{
    int i;
    int a = 3, b = 5;
    int ret;

    int (*funcp[2])(int, int);
    funcp[0] = add;
    funcp[1] = sub;
    for(int i = 0; i < 2; i++)
    {
        ret = funcp[i](a, b);
        printf("%d \n", ret);
    }
}
```
