## valgrind简介
Valgrind是一套Linux下，开放源代码（GPL V2）的仿真调试工具的集合。

它用来构建动态分析工具, 主要具有以下功能：

 - Memcheck，重量级内存检测工具，使用广泛 
 - Helgrind，检测多线程中的数据竞争问题
 - Callgrind，检查程序中函数调用过程中出现的问题 
 - Cachegrind，检查程序中缓存使用出现的问题
 - Massif，检查程序中堆栈使用中出现的问题 
 - Extension，利用core提供的功能，自己编写特定的内存调试工具

虽然内存检测工具使用比较广泛，但Valgrind功能要比单纯内存检测强大得多。

无需改变 Valgrind 的调用方式，就能得到比想象的要多得多的极具价值的信息。

Valgrind 会在你的程序奔溃之前找出潜在的错误；它不仅告诉你错误在哪里，还会告诉你原因。

Valgrind 首先是一个未知行为 检测工具，其次他是一个函数和内存分析工具, 然后是一个数据竞争条件侦测工具， 它最后才是一个内存泄露检查工具。

## 安装

1、使用如下命令下载压缩包：

（比较慢，耐心等待，这个版本bug少）
```cpp
wget https://sourceware.org/pub/valgrind/valgrind-3.16.1.tar.bz2
```

2、解压安装包：

```cpp
tar -jxvf valgrind-3.16.1.tar.bz2
```
3、进入目录

```cpp
cd valgrind-3.16.1
```
4、配置Valgrind，生成MakeFile文件

```cpp
./configure
```

5、编译Valgrind

```cpp
make
```

6、安装Valgrind

```cpp
make install	//如果报错前面要加sudo
```
## 使用

默认是使用memcheck，可以通过-tool参数指定使用的功能。

比如下面语句就是指定使用memcheck

```bash
valgrind --tool=memcheck ./test_valgrind
```

**1、内存泄漏**

写个没有释放内存的demo：

```cpp
#include <iostream>
using namespace std;
int main()
{
    int *p=new int[5];
    return 0;
}
```
编译：`g++ -o test_valgrind test_valgrind.cpp`
运行：`valgrind ./test_valgrind`

结果如下：

```cpp
==18694== Memcheck, a memory error detector
==18694== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==18694== Using Valgrind-3.16.1 and LibVEX; rerun with -h for copyright info
==18694== Command: ./test_valgrind
==18694==
==18694== error calling PR_SET_PTRACER, vgdb might block
==18694==
==18694== HEAP SUMMARY:
==18694==     in use at exit: 20 bytes in 1 blocks
==18694==   total heap usage: 2 allocs, 1 frees, 72,724 bytes allocated
==18694==
==18694== LEAK SUMMARY:
==18694==    definitely lost: 20 bytes in 1 blocks
==18694==    indirectly lost: 0 bytes in 0 blocks
==18694==      possibly lost: 0 bytes in 0 blocks
==18694==    still reachable: 0 bytes in 0 blocks
==18694==         suppressed: 0 bytes in 0 blocks
==18694== Rerun with --leak-check=full to see details of leaked memory
==18694==
==18694== For lists of detected and suppressed errors, rerun with: -s
==18694== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
```
可以看到提示了有20个字节直接内存泄漏（definitely lost），但没有给出行号。

接下来为了得到更详细的信息，我们
编译加上-g：`g++ -g -o test_valgrind test_valgrind.cpp`
运行加上--leak-check=full：`valgrind --leak-check=full ./test_valgrind`

结果如下：

```cpp
==18740== Memcheck, a memory error detector
==18740== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==18740== Using Valgrind-3.16.1 and LibVEX; rerun with -h for copyright info
==18740== Command: ./test_valgrind
==18740==
==18740== error calling PR_SET_PTRACER, vgdb might block
==18740==
==18740== HEAP SUMMARY:
==18740==     in use at exit: 20 bytes in 1 blocks
==18740==   total heap usage: 2 allocs, 1 frees, 72,724 bytes allocated
==18740==
==18740== 20 bytes in 1 blocks are definitely lost in loss record 1 of 1
==18740==    at 0x483C583: operator new[](unsigned long) (vg_replace_malloc.c:431)
==18740==    by 0x10919E: main (test_valgrind.cpp:5)
==18740==
==18740== LEAK SUMMARY:
==18740==    definitely lost: 20 bytes in 1 blocks
==18740==    indirectly lost: 0 bytes in 0 blocks
==18740==      possibly lost: 0 bytes in 0 blocks
==18740==    still reachable: 0 bytes in 0 blocks
==18740==         suppressed: 0 bytes in 0 blocks
==18740==
==18740== For lists of detected and suppressed errors, rerun with: -s
==18740== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
```

可以看出这次明确指出了内存泄漏是由于第五行的new产生的。


**2、内存越界**

写个demo：

```cpp
#include <iostream>
using namespace std;
int main()
{
    int *p=new int[5];
    p[5]=1;
    delete [] p;
    return 0;
}
```
编译：`g++ -g -o test_valgrind test_valgrind.cpp`
运行：`valgrind --leak-check=full ./test_valgrind`

结果如下：

```cpp
==18786== Memcheck, a memory error detector
==18786== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==18786== Using Valgrind-3.16.1 and LibVEX; rerun with -h for copyright info
==18786== Command: ./test_valgrind
==18786==
==18786== error calling PR_SET_PTRACER, vgdb might block
==18786== Invalid write of size 4
==18786==    at 0x1091CB: main (test_valgrind.cpp:6)
==18786==  Address 0x4da5c94 is 0 bytes after a block of size 20 alloc'd
==18786==    at 0x483C583: operator new[](unsigned long) (vg_replace_malloc.c:431)
==18786==    by 0x1091BE: main (test_valgrind.cpp:5)
==18786==
==18786==
==18786== HEAP SUMMARY:
==18786==     in use at exit: 0 bytes in 0 blocks
==18786==   total heap usage: 2 allocs, 2 frees, 72,724 bytes allocated
==18786==
==18786== All heap blocks were freed -- no leaks are possible
==18786==
==18786== For lists of detected and suppressed errors, rerun with: -s
==18786== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
```
可以看到提示了Invalid write of size 4 at 0x1091CB: main (test_valgrind.cpp:6) ，告诉我们第六行有非法写入产生，即发生了内存越界的情况。

还可以加上-s参数让错误总结更明显：`valgrind -s --leak-check=full ./test_valgrind`


结果如下：

```cpp
==18788== Memcheck, a memory error detector
==18788== Copyright (C) 2002-2017, and GNU GPL'd, by Julian Seward et al.
==18788== Using Valgrind-3.16.1 and LibVEX; rerun with -h for copyright info
==18788== Command: ./test_valgrind
==18788==
==18788== error calling PR_SET_PTRACER, vgdb might block
==18788== Invalid write of size 4
==18788==    at 0x1091CB: main (test_valgrind.cpp:6)
==18788==  Address 0x4da5c94 is 0 bytes after a block of size 20 alloc'd
==18788==    at 0x483C583: operator new[](unsigned long) (vg_replace_malloc.c:431)
==18788==    by 0x1091BE: main (test_valgrind.cpp:5)
==18788==
==18788==
==18788== HEAP SUMMARY:
==18788==     in use at exit: 0 bytes in 0 blocks
==18788==   total heap usage: 2 allocs, 2 frees, 72,724 bytes allocated
==18788==
==18788== All heap blocks were freed -- no leaks are possible
==18788==
==18788== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
==18788==
==18788== 1 errors in context 1 of 1:
==18788== Invalid write of size 4
==18788==    at 0x1091CB: main (test_valgrind.cpp:6)
==18788==  Address 0x4da5c94 is 0 bytes after a block of size 20 alloc'd
==18788==    at 0x483C583: operator new[](unsigned long) (vg_replace_malloc.c:431)
==18788==    by 0x1091BE: main (test_valgrind.cpp:5)
==18788==
==18788== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
```
**3、多线程竞争问题**

使用如下命令即可：

```bash
valgrind --tool=helgrind ./test_valgrind
```
**4、分析程序性能**

使用如下命令即可：

```bash
valgrind --tool=callgrind ./test_valgrind
```


------
更多详细的使用可见[Linux动态分析工具valgrind使用入门](https://blog.csdn.net/guotianqing/article/details/104023641)