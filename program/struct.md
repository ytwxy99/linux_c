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
```c
struct student a;  // 12个字节   如果存储大小小于int型，需要地址偏移来存储，如char占用一个字节，但是在struct中算4个字节来做对齐；
struct student *p; //指针在64位中占8个字节
```
## 函数传参
总共有两种：
  值传递和地址传递

```c
// 值传递
void func(struct student st)
{
  printf("%d\n", sileof(b));
}

// 地址传递
void func(struct student *p)
{
   printf("%d\n", sileof(p));
}
```
# 共用体
## 产生及意义
多个成员变量一个时刻只能一个成员在内存存在，一个共用体的大小是最大成员变量类型占用的大小。历史产生原因是当时硬件资源匮乏，节省内存资源；
## 类型描述
  union 共用体名
  {
    数据类型 成员名1；
    数据类型 成员名2；
    ......
  }
## 嵌套定义
共用体和结构体可以相互嵌套
```c
#include <stdio.h>
#include <stdlib.h>

#define NAMESIZE 32

struct tmp_st
{
  int i;
  union
  {
    int a;
    char c;
  }un;

  float f;
}

union
{
  int a;
  double d;
  struct
  {
    int arr[10];
  }st;
}

union test_un
{
  int i;
  float f;
  double d;
  char ch;
}

int main()
{
  // TYPE NAME = VALUE;
  union test_un a;
  a.f = 3.12;
  printf("%d", a.i); //这里调用是无意义的，是个随机值。
  exit(0);
}

```
## 定义变量（变量，数组，指针），初始化及成员引用
```c
  成员引用: 
    变量名.成员名
    指针名->成员名
```
## 内存空间占用大小
按照成员类型最大占用空间位union内存大小
## 函数传参（值，地址）
## 位域
```c
union
{
  struct
  {
    char a:1; //指定占用1位（bit）
    char b:2; //指定占用2位
    char c:1;
  }x;
  int y;
}u;
```
