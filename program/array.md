# 二维数组

```c
#include "stdio.h"
#include "stdlib.h"

#define M 2
#define N 2

int main(void)
{
    printf("M: %d\n", M);
    printf("N: %d\n", N);

    int a[M][N]={
            {1,2},
            {3, 4},
    };

    printf("address: %p, adress + 1 : %p \n", a, a+1);

    printf("address: %p, adress + 1 : %p \n", a, a+1);

    printf("address: %d, adress + 1 : %d \n", (*a)[1], (*(a+1))[1]);

    for(int i = 0; i < M; i ++)
    {
        for(int j = 0; j < N; j ++)
        {
            printf("address: %p, value : %d \n", &a[i][j], a[i][j]);
        }
    }


    return 0;
}

/* output

M: 2
N: 2
address: 0x16f5af870, adress + 1 : 0x16f5af878 
address: 0x16f5af870, adress + 1 : 0x16f5af878 
address: 2, adress + 1 : 4 
address: 0x16f5af870, value : 1 
address: 0x16f5af874, value : 2 
address: 0x16f5af878, value : 3 
address: 0x16f5af87c, value : 4

```
