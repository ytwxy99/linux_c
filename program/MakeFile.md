# MakeFile
## make
make 是个工程管理器，管理依赖和被依赖关系
makefile的优先级高于Makefile
## 编写一个makefile
```bash
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
