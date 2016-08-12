# Notes on HW1
- 一些如何写shell的文章
http://brennan.io/2015/01/16/write-a-shell-in-c/


- Q2 如何实现cd, pwd
cd使用系统函数chdir() pwd使用getcwd
http://stackoverflow.com/questions/18686114/cd-command-not-working-with-execvp
http://blog.csdn.net/dlutbrucezhang/article/details/17054091

一个问题是chdir() 不能识别 ~ 目录
http://www.cnblogs.com/wuyuegb2312/p/3399566.html
但是对于cd ~以及cd ~/PATHNAME就不行了。对于这种情况，可以发现这个路径的特点是以“~”开始，那么利用type_prompt()中的获取工作目录的方式，重新拼接出完整路径再作为参数进行传递即可。为了提高效率，把type_prompt()中获取的信息做成是全局的，这样实现cd时可以直接调用。

- linux中exit()的作用
http://www.oschina.net/question/234345_42434
exit：（#include <stdlib.h>） 
    在C语言的main函数中我们通常使用return (0);这样的方式返回一个值。但这是限定在非void情况下的，也就是非void main()这样的形式。     exit()通常是用在子程序中用来终结程序用的，使用后程序自动结束，跳出操作系统。 
    exit(0) 表示程序正常退出, 
    exit(1)/exit(-1)表示程序异常退出。 
exit() 结束当前进程/当前程序/，在整个程序中，只要调用 exit ，就结束。 
但在如果把exit用在main内的时候无论main是否定义成void返回的值都是有效的，并且exit不需要考虑类型，exit(1)等价于return (1) 。 
例如： 
#include<stdlib.h> 
int main() 
{ 
  exit (1);//等价于return (1); 
} 
exit()是一个函数 ,结束一个进程，它将删除进程使用的内存空间，同时把错误信息返回父进程，在父进程中wait系统调用将接受到此返回信息。

- 关于execv函数
execv(func, argv);
其实第一个参数是函数名，第二个参数是该函数func的参数，而argv[0]就是func本身，之后是其输入的parameters

函数后p的作用
带 p 的exec函数：execlp,execvp，表示_第一个参数path不用输入完整路径_，只有给出命令名即可，它会在环境变量PATH当中查找命令

- 如何获得系统变量PATH
http://www.powerxing.com/unix-simple-shell-with-argv/
