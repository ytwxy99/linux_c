# 变量和地址

变量是采用补码方式，放到指定内存空间里；而指针则是指向这个变量空间的；

```c
#include "stdio.h"
#include "stdlib.h"
#include "string.h"


int main(void)
{
    int a[3][2] = {1,2,3,4,5,6};;
    int (*p)[2] = a;  //p 为数组指针

    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 2; ++j) {
            printf("r: %p, p: %p, v: %d \n", &p[i][j], *(p+i)+j, *(*(p+i)+j));
        }
    }

    exit(0);
}

/* output

r: 0x16b0ff870, p: 0x16b0ff870, v: 1 
r: 0x16b0ff874, p: 0x16b0ff874, v: 2 
r: 0x16b0ff878, p: 0x16b0ff878, v: 3 
r: 0x16b0ff87c, p: 0x16b0ff87c, v: 4 
r: 0x16b0ff880, p: 0x16b0ff880, v: 5 
r: 0x16b0ff884, p: 0x16b0ff884, v: 6

```

# 数组指针和指针数组

```c
#include "stdio.h"
#include "stdlib.h"
#include "string.h"


int main(void)
{
    int a[3][2] = {1,2,3,4,5,6};;
    int (*p)[2] = a;

    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 2; ++j) {
            printf("r: %p, p: %p, v: %d \n", &p[i][j], (*p+i)+j, *(*p+i)+j);
        }
    }
}

// output
r: 0x16f517870, p: 0x16f517870, v: 1 
r: 0x16f517874, p: 0x16f517874, v: 2 
r: 0x16f517878, p: 0x16f517874, v: 2 
r: 0x16f51787c, p: 0x16f517878, v: 3 
r: 0x16f517880, p: 0x16f517878, v: 3 
r: 0x16f517884, p: 0x16f51787c, v: 4 

```

# 数组/指向数组的指针

```c
#include "stdio.h"
#include "stdlib.h"
#include "string.h"


int main(void)
{
    char * str;
    char tmp[] = "hello";

    // str 指向已分配6个字符空间的头地址
    str = tmp;
    strcpy(str, "wolrd");
    printf("case: 1, %s\n", str);

    // arry 已分配6个字符空间的头地址
    char arry[] = "hello";
    strcpy(arry, "wolrd");
    printf("case: 2, %s\n", arry);

    // str 指向hello 常量的头地址（常量不能被改变）
    str = "hello";
    strcpy(str, "wolrd");
    printf("case: 3, %s\n", str);


    exit(0);
}

// output
case: 1, wolrd
case: 2, wolrd

进程已结束，退出代码为 138 (interrupted by signal 10: SIGBUS)
```
# const 和 指针
```c
#include <stdio.h>

/*
 *  const int *p 常量指针，指针的指向可以发生变化，但是指向所指向目标变量值不能变化；
 *  int *const p 指针常量，指针的指向不可以发生变化，但是指向所指向目标变量值可以变化；
 *  const int *const p 即是常量指针也是指针常量；
 *
 */

int main(void)
{
    const float pi = 3.14;
    printf("pi = %f\n", pi);

    float *p = &pi;
    *p = 3.1415926;
    printf("p = %f\n", *p); // 间接指向，改变const常量内容；一种猜想是p的指向开启新的内存空间存储3.1415926
    printf("pi = %f\n", pi); // 还是保持原来3.14，*p没有改变指向pi地址的内容 ？ 这个和老的gcc表现不一致，老的是pi也被改变；

    int i = 1;
    int j = 100;
    int const *a;
    a = &i;
    // T i = 10;  是可以改的
    // F *a = 10;    这个是改不了的
    a = &j;
    printf("i -> %p, j -> %p, p -> %p \n", &i, &j, a);

    int *const b = &i;
    // F b = &j; 指向是不能改变的
    *b = 1000;
    printf("p -> %d, a -> %d \n", i, *b, i);

    int const *const c = &i;
    // F c = &j; 不可以改变指向
    // F *c = 1000; 不可以改变目标变量内容；

    return 0;
}

// output 
pi = 3.140000
p = 3.141593
pi = 3.140000
i -> 0x16fd4363c, j -> 0x16fd43638, p -> 0x16fd43638 
p -> 1000, a -> 1000 
```