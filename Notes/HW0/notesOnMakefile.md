# Notes on Makefile
## A test Makefile - single file
```shell
# 可执行文件
TARGET = main
# c文件
SRCS = main.c
# 目标文件
OBJS = $(SRCS:.c=.o)

# 指令编译器和选项 
CC=gcc
CFLAGS=-Wall -std=gnu99

$(TARGET):$(OBJS) # 声明依赖关系
        $(CC) -o $(TARGET) $(OBJS) # 具体的规则：当倚赖的对象在目标修改后修改的话，就要去执行规则这一行所指定的命令

$(OBJS):$(SRCS)
        $(CC) -c $(SRCS)

clean:
        rm -rf $(OBJS) # -r: --recursive, remove the contents of directories recursively; -f: --force, ignore nonexistent files, never prompt
```

## For CS162 HW0 3.1 
只需要 compile c文件即可
```shell
TARGET = main
SRCS = main.c test.c wc.c
OBJS = $(SRCS:.c=.o)

CC=gcc
CFLAGS=-Wall -std=gnu99

$(OBJS):$(SRCS)
        $(CC) -c $(SRCS)

clean:
        rm -rf $(OBJS)
```


## Notes
1. Makefile有三个非常有用的变量。分别是$@，$^，$<代表的意义分别是：$@--目标文件，$^--所有的依赖文件，$<--第一个依赖文件。
2. %.o:%.c 表示把所有.c文件都编译成 .o

