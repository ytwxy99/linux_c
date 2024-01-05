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
typedef def int *IP 
IP a; --> int *a

typedef int ARR[6]; -->  int[6] -> ARR
ARR a; --> int a[6]

typedef struct node_st NODE;
NODE a; ---> struct node_st a;
等价：
typedef struct
{
  int i;
  float f;
}NODE;

typedef struct node_st *NODEP;
NODEP a; ---> struct node_st *a;

typedef int FUNC(int);
FUNC f; --> int f(int);


typedef int *FUNCP(int);
FUNCP pp ---> int *p(int);
```

