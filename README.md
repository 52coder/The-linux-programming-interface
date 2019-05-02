# The-linux-programming-interface
Linux UNIX系统编程手册 勘误表

本项目是记录学习Linux/UNIX系统编程手册中文版过程中发现的问题，[英文版勘误表](http://man7.org/tlpi/errata/).

中文教材勘误会采用页码加原文加正确译文的形式，如果你刚好在看本书，发现了任何错误，均可以提交合并请求，欢迎各位与我交流讨论：persever2009#gmail.com

勘误1.(来自豆瓣网友@lifayi2008)

P384页 章节22.9. 第三行

原文“临时阻塞一个信号，以防止其信号处理器不会将某些关键代码片段的执行中断 ”

更改为“临时阻塞一个信号，以防止其信号处理器将某些关键代码片段的执行中断”  

勘误2.

p530页 章节30.2.1

原文“条件变量的数据类型是pthread_count_t” 
更改为“条件变量的数据类型是pthread_cond_t.

p558页 源代码thread_cleanup.c
main函数在全局变量赋值前应使用pthread_mutex_lock,添加后的代码如下：
```
        s = pthread_mutex_lock(&mtx);
        if (s != 0)
            errExitEN(s, "pthread_mutex_lock");
 

        glob = 1;
 
        s = pthread_mutex_unlock(&mtx);
        if (s != 0)
            errExitEN(s, "pthread_mutex_unlock");
```


p730页：
原文：
如read()可能hiu被一个向管道写入数据的信号处理器中断。
英文：
“For example, the read() might be interrupted by a signal handler that writes data to the pipe. ”
更正hiu--->会
看到这里我实在无力吐槽了，好好的一本书被翻译成天书了，翻译完就跑，也没人维护勘误表，你起码英文拼音拼对呀.


