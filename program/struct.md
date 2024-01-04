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
  int i;
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
  // TYPE NAME = VALUE;
  struct student st = {1, 2.0, 'a'};
  st.id = 2;

  struct student_st sst = {1, "Alan", {2011, 11, 11}, 99, 99};

  struct student_st sst1 = {.math = 98, .chinese = 97}; //初始化部分成员变量内容

  struct student_st *p = {1, "Alan", {2011, 11, 11}, 99, 99};

  struct student_st arry[2] = {{1, "Alan", {2011, 11, 11}, 99, 99}, {2, "Jack", {2011, 11, 11}, 99, 99}};

  p->id = 100;
  p->birth.year = 2022;

  st.birth.year = 2023;

  p = &arry[0];

  for(int i = 0; i < 2; i++, p++)
  {
    arry[i].birth.year = 2022;
    p->birth.year = 2022;
  }
  exit(0);
}
```

## 结构体嵌套定义
```c
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
```
## 定义变量（变量，数组，指针），初始化及成员引用
TYPE NAME = VALUE
变量名.成员名
指针->成员名
(*指针).成员名
## 占用内存空间大小
