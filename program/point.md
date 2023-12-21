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

# const/数组/指向数组的指针
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