# 结构类型
## 生产及其意义
结构体是存储不同数据类型的数据存放在连续的内存空间中，而内存是相同类型数据存放在连续内存空间中；
## 类型描述
  struct 结构体名
  {
    数据类型 成员1;
    数据类型 成员2;
    ...... 
  };

```c
#include <stdio.h>
#include <stdlib.h>

#define NAMESIZE 32

struct student
{
  int i, j;
  float f;
  char ch;
};

struct birthday_st
{
  int year;
  int month;
  int day;
};

struct student_st
{
  int id;
  char name[NAMESIZE];
  struct birthday_st birth;
  //struct birthday_st   # 该方法定义同样有效
  //{  
  //  int year;
  //  int month;
  //  int day;
  //} birth;
  int math;
  int chinese;
};

int main()
{

  exit(0);
}
```

## 结构体嵌套定义
## 定义变量（变量，数组，指针），初始化及成员引用
## 占用内存空间大小
