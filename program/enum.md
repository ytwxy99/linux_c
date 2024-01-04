# 枚举
## 声明
```c
enum 标识符
{
  成员1；
  成员2；
  ......
}
```
## 使用
```c
#include <stdio.h>
#include <stdlib.h>

enum day
{
  MON = 1, //不指定从0开始
  TUS,
  WES,
  THR,
  FRI,
  SAT,
SUN
};

int main()
{
  enum day a = WES;

  printf("%d\n", a)
}

# output
day is 3
```
