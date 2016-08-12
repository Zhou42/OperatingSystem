# Section 2 笔记
关于linux编程

1. GDB调试
启动GDB时 一定要 加上－g
```shell
gcc -g -o filename1 filename2.c
```

2. gdb -tui filename
进入视图调试

3. 关于linux下 wait()函数 -> parent process等待 children process
http://sodino.com/2015/04/14/c-wait/

我们看到在子进程非正常中断后,用wait(&status)回收子进程,将子进程的状态存到status中,status为整型变量.
从本质上讲,系统调用waitpid是wait的封装,waitpid只是多出了两个可由用户控制的参数pid和options,为编程提供了灵活性.
waitpid函数的原型为pid_t waitpid(pid_t pid,int *status,int options)



4. linux 下 open函数 
http://joe.is-programmer.com/posts/17463.html

5. execv函数
http://www.cnblogs.com/mickole/p/3187409.html

