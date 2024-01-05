#typedef
##定义
为已有的数据类型改名
## 声明
已有的数据类型  新名字；
## 事例
```c
#include <stdio.h>
#include <stdlib.h>

typedef int INT;

int main()
{
  INT i = 100;
  printf("%d\n", i);

  exit(0);
}
```
## 指针
技巧  用a 替换 IP/ARR/NODE/NODEP
```c
type def int *IP 
IP a; --> int *a

typedef int ARR[6]; -->  int[6] -> ARR
ARR a; --> int a[6]

type struct node_st NODE;
NODE a; ---> struct node_st a;

type struct node_st *NODEP;
NODEP a; ---> struct node_st *a;
```

