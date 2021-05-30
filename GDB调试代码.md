转自[https://blog.csdn.net/weixin_43628270/article/details/108179941](https://blog.csdn.net/weixin_43628270/article/details/108179941)

----

@[TOC](目录)
## 一、编译时加上 -g调试信息并且去掉优化信息
在Makefile中增加-g调试信息并且去掉优化信息

## 二、设置启动参数
gdb --args ./Client 127.0.0.1 6000 “hello this is a client”

说明：
–args：设置127.0.0.1 6000 "hello this is a client"为启动参数

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201210220040964.png)
## 三、设置断点
1、命令：l
说明：查看代码

2、命令：b 16
说明：在程序的第16行添加断点

3、命令：info break
说明：查看断点

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201210220055750.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70)

## 四、开始调试

1、命令：r
说明：开始运行
2、命令：s
说明：进入函数内部
3、命令：n
说明：下一步
4、命令：finish
说明：跳出函数内部
5、命令：c
说明：直接运行到下一个断点

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201210220123107.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70)
## 五、打印变量
1、命令：p m_cliSocket
说明：打印m_cliSocket，十进制格式
2、命令：p/x m_cliSocket
说明：打印m_cliSocket，十六进制格式
3、命令：p/t m_cliSocket
说明：打印m_cliSocket，二进制格式
4、命令：p/o m_cliSocket
说明：打印m_cliSocket，八进制格式

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201210220158233.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70)
## 六、退出
1、命令：q
说明：退出GDB调试，根据提示选y则退出

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201210220839972.png)
## 七、其他常用命令
1、在文件中某一函数处设置断点：b TcpClient.cpp:TcpClient::SenMsg
2、直接运行到下一个断点：c
3、查看调用堆栈：bt

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201210220911680.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70)
4、删除断点：d 5
说明：5为断点序号，如果不加5则提示是否删除所有断点

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201210220928358.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70)
## 八、多线程调试

 

 1、命令：info threads
 说明：显示当前可调试的所有线程，ID前有“ * ”号的线程是当前被调试的线程。


2、命令： thread ID
说明：调试目标ID指定的线程

3、命令：set scheduler-locking off/on/step
说明：调试多线程程序时，默认除了被调试的线程在执行外，其它线程也在继续执行，但有时我们希望只让被调试的线程运行，因此可以使用这个命令。off表示不锁定任何线程，所有线程可以继续运行，即默认值；on表示只有当前被调试的线程会继续执行；step表示在单步执行的时候，只有当前线程会执行。



