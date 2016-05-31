# wc.c Function - HW0 3.2
## About argc and argv for main function
<http://crasseux.com/books/ctutorial/argc-and-argv.html>
对比：
没有参数的C program
```C 
#include <stdio.h>
int main()
{
  return 0;
}
```
包含参数的C program
```C 
#include <stdio.h>
int main(int argc, char *argv[])
{
  return 0;
}
```
As you can see, main now has arguments. The name of the variable argc stands for "argument count"; argc contains the number of arguments passed to the program. The name of the variable argv stands for "argument vector". A vector is a one-dimensional array, and argv is a one-dimensional array of strings. Each string is one of the arguments that was passed to the program.
考虑gcc
``` shell
gcc -o myprog myprog.c
```
输出是
argc
4 
argv[0]
gcc 
argv[1]
-o 
argv[2]
myprog 
argv[3]
myprog.c
注意the first argument (argv[0]) is the name by which the program was called, in this case gcc. Thus, there will always be at least one argument to a program, and argc will always be at least 1.

## 关于EOF
http://www.ruanyifeng.com/blog/2011/11/eof.html
在Linux系统之中，EOF根本不是一个字符，而是当系统读取到文件结尾，所返回的一个信号值（也就是-1）。至于系统怎么知道文件的结尾，资料上说是通过比较文件的长度。
比如如果(c = getc (fp)) 到了文档末尾，则返回 －1，也就是(c = getc (fp)) ＝= EOF为 true

## isalpha()
http://www.tutorialspoint.com/c_standard_library/c_function_isalpha.htm
C中用于判断character is alphabetic, 也就是判断是不是字母。这个可以用来判断word的个数

## 关于GDB的使用
http://man.linuxde.net/gdb

## getChar() vs getc()
http://stackoverflow.com/questions/2507082/getc-vs-getchar-vs-scanf-for-reading-a-character-from-stdin

## 关于c和c++中的string和char数组
c中没有String type，全是char数组；c++中有 String
http://blog.csdn.net/hankai1024/article/details/7985813

## 关于word的定义
http://www.cnblogs.com/peida/archive/2012/12/18/2822758.html
一个字被定义为由空白、跳格或换行字符分隔的字符串。
但是mac中与linux中定义不同 

## The final wc.c file 
Word are defined as the Strings seperated by non-alphabets 
```c
 #include<stdio.h>
 #include<stdarg.h>
 #include<stdlib.h>
  
 typedef unsigned long count_t; /* Counter type */
  
 count_t ccount = 0;
 count_t wcount = 0;
 count_t lcount = 0;
 int flag = 0; // whether previous character is alphabet
  
 void count (char* filename) {
     FILE* f = fopen(filename, "r");
     if (!f) {
         printf("Can't open file `%s'!",filename);
     }
     int c;
     if (feof(f)) {
         return;
     }
     while ((c = getc(f)) != EOF) {
         ccount++;
         if (isalpha(c) && flag == 0) {
             wcount++;
             flag = 1;
         }
         if (!isalpha(c)) {
             flag = 0;
         }
         if (c == '\n') {
             lcount++;
         }
     }
     return;
 }
  
 int main(int argc, char *argv[]) {
     if (argc == 2) {
         count(argv[1]);
     }
     printf("%lu\t%lu\t%lu\t%s\n", lcount, wcount, ccount, argv[1]);
 //    printf("The counter works fine!");
     return 0;
}
```
### PS: sublime 去行号 
http://blog.csdn.net/u010983881/article/details/25898989

