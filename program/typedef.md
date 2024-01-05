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


