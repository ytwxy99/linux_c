# MakeFile
## make
make 是个工程管理器，管理依赖和被依赖关系
makefile的优先级高于Makefile
## 编写一个makefile
```bash
# gcc *.c
shawnwang@ShawndeMac-mini makefile % ls
a.out	main.c	tool1.c	tool1.h	tool2.c	tool2.h
shawnwang@ShawndeMac-mini makefile % ./a.out 
tool1 print
tool2 print

# 解析
a.out 依赖  main.o tool1.o tool2.o
main.o 依赖 main.c
tool1.o 依赖 tool1.c
tool2.o 依赖 tool2.c

makefile就是维护上面的依赖关系
```
###makefile
```shell
mytool:main.o tool1.o tool2.o
	gcc main.o tool1.o tool2.o -o mytool

main.o:main.c
	gcc main.c -c -Wall -g -o main.o

tool1.o:tool1.c
	gcc tool1.c -c -Wall -g -o tool1.o

tool2.o:tool2.c
	gcc tool2.c -c -Wall -g -o tool2.o

clean:
	rm -rf *.o mytool
```
make
make clean --> clean:

## makefile 重构
```c
CC=gcc
CFLAGS+=-c -Wall -g

mytool:$(OBJS)
	$(CC) ${OBJS} -o mytool

main.o:main.c
	$(CC) main.c $(CFLAGS) -o main.o

tool1.o:tool1.c
	$(CC) tool1.c $(CFLAGS) -o tool1.o

tool2.o:tool2.c
	$(CC) tool2.c $(CFLAGS) -o tool2.o

clean:
	${RM} -r *.o mytool  # RM == rm -f
```
```c
OBJS=main.o tool1.o tool2.o
CC=gcc
CFLAGS+=-c -Wall -g

mytool:$(OBJS)
	$(CC) $^ -o $@

main.o:main.c
	$(CC) $^ $(CFLAGS) -o $@

tool1.o:tool1.c
	$(CC) $^ $(CFLAGS) -o $@

tool2.o:tool2.c
	$(CC) $^ $(CFLAGS) -o $@

clean:
	${RM} -r *.o mytool

main.o:main.c 对应  $@ $^
```
```c
OBJS=main.o tool1.o tool2.o
CC=gcc
CFLAGS+=-c -Wall -g

mytool:$(OBJS)
	$(CC) $^ -o $@

%.o:%.c
	$(CC) $^ $(CFLAGS) -o $@

clean:
	${RM} -r *.o mytool

# % 代表$(OBJS)的前缀名字
```
