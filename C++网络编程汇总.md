
@[TOC](目录)
## 基础知识
 - [C++网络编程（一）：TCP套接字编程](https://blog.csdn.net/weixin_44164489/article/details/108606391)
 - [C++网络编程（二）：UDP套接字编程](https://blog.csdn.net/weixin_44164489/article/details/108663819)
 - [C++网络编程（三）：基于TCP的半关闭](https://blog.csdn.net/weixin_44164489/article/details/108673426)
 - [C++网络编程（四）：多进程并发服务器](https://blog.csdn.net/weixin_44164489/article/details/108910059)
 - [C++网络编程（五）：IO多路复用实现并发服务器](https://blog.csdn.net/weixin_44164489/article/details/108930663)
 - [C++网络编程（六）：多线程并发服务器](https://blog.csdn.net/weixin_44164489/article/details/108954110)
 - [recv( )函数返回值说明](https://blog.csdn.net/mercy_ps/article/details/82224128?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522161278520216780271556500%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=161278520216780271556500&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-82224128.pc_search_result_no_baidu_js&utm_term=recv%25E8%25BF%2594%25E5%259B%259E%25E5%2580%25BC)
	
		成功执行时，返回接收到的字节数（即大于0）。
		另一端已关闭则返回0。
		失败返回-1，errno被设为某个值。
		（注意：非阻塞IO下errno为EAGAIN或者EWOULDBLOCK说明数据读取完毕！）
 - 各个函数与TCP各个状态的对应如下图：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210208200617321.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70)
			
	特别要记住：主动断开连接的一方调用close进入FIN_WAIT_1状态，被动的一方调用close后进入LAST_ACK状态

## IO多路复用相关问题
 - [网络socket编程实现并发服务器——IO多路复用](https://blog.csdn.net/qq_43296898/article/details/88770413?utm_medium=distribute.pc_relevant.none-task-blog-OPENSEARCH-2.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-OPENSEARCH-2.channel_param)（理解其中的代码实现）
 	
	 	FD_ZERO(fd_set* fds) //清空集合
		FD_SET(int fd, fd_set* fds) //将给定的描述符加入集合
		FD_ISSET(int fd, fd_set* fds) //判断指定描述符是否在集合中
		FD_CLR(int fd, fd_set* fds) //将给定的描述符从文件中删除
 - [select()函数以及FD_ZERO、FD_SET、FD_CLR、FD_ISSET
](https://blog.csdn.net/cstarbl/article/details/7645298)
		
		（1）执行fd_set set; FD_ZERO(&set);则set用位表示是0000,0000。
		（2）若fd＝5,执行FD_SET(fd,&set);后set变为0001,0000(第5位置为1)
		（3）若再加入fd＝2，fd=1,则set变为0001,0011
		（4）执行select(6,&set,0,0,0)阻塞等待（ 第一个参数代表需要检查的文件描述字个数（即检查到fd_set的第几位），值是所监听的文件描述符中最大的一个加1（如在readset,writeset,exceptset中所含最大的fd为5，则nfds=6，因为fd是从0开始的）。设这个值是为提高效率，使函数不必检查fd_set的所有1024位。）
		（5）若fd=1,fd=2上都发生可读事件，则select返回，此时set变为0000,0011。注意：没有事件发生的fd=5被清空。

 - epoll的EPOLLONESHOT：[博客1](https://blog.csdn.net/le119126/article/details/46364399)、[博客2](https://blog.csdn.net/mijichui2153/article/details/81004874)、[博客3](https://blog.csdn.net/liuhengxiao/article/details/46911129)

## 多线程相关问题

 - [C++11学习笔记-----线程库std::thread](https://blog.csdn.net/sinat_35261315/article/details/79275839)
 - [boost::thread 多线程全解析](https://blog.csdn.net/Fourier_Legend/article/details/82020686?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.control#boostthread%E7%9A%84%E5%87%A0%E4%B8%AA%E5%87%BD%E6%95%B0)
 - Boost线程池： [博客1](https://blog.csdn.net/tissar/article/details/88359860)、[博客2](https://blog.csdn.net/qingzai_/article/details/44488223)、[官方文档（1.69.0版）](https://www.boost.org/doc/libs/1_69_0/doc/html/boost_asio/reference/thread_pool.html#boost_asio.reference.thread_pool.protected_member_functions)、[官方文档（1.74.0版）](https://www.boost.org/doc/libs/1_74_0/doc/html/boost_asio/reference/thread_pool.html)
## 模式
 - [网络模型的一些基本概念](https://mp.weixin.qq.com/s?__biz=MzAxNzU2MzcwMw==&mid=2649274278&idx=4&sn=caa323faf0c51d882453c0e0c6a62282&chksm=83ffbefeb48837e841a6dbff292217475d9075e91cbe14042ad6e55b87437dcd01e6d9219e7d&scene=0&xtrack=1#rd)
 - [Reactor（反应器）模式](https://blog.csdn.net/suchahaerkang/article/details/80576220?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522160916804916780271154047%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=160916804916780271154047&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-3-80576220.nonecase&utm_term=Reactor%20%E6%A8%A1%E5%BC%8F)
 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210113150417205.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70#pic_center)
 - Proactor模式：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210113150433806.jpg#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210113150433888.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70#pic_center)


 - [生产者/消费者模式的理解及实现](https://blog.csdn.net/u011109589/article/details/80519863?ops_request_misc=&request_id=&biz_id=102&utm_term=%25E7%2594%259F%25E4%25BA%25A7%25E8%2580%2585%25E6%25B6%2588%25E8%25B4%25B9%25E8%2580%2585%25E6%25A8%25A1%25E5%25BC%258F&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-80519863.pc_search_result_no_baidu_js)

## 其它问题

 - close-wait问题：[博客](https://blog.csdn.net/lishenglong666/article/details/45335589)

		问题：有大量的socket处于close-wait状态
		
		原因：某种情况下对方关闭了socket连接，但是我方忙于其它事情，没有调用close关闭连接。
		换句话说，就是在对方连接关闭之后，程序里没有检测到，或者程序压根就忘记了这个时候需要关闭连接，于是这个资源就一直被程序占着。

		解决方法：通过recv的返回值来检测出对方已经关闭的socket，然后关闭它。


 - 缓冲区：[一文搞懂用户缓冲区与内核缓冲区](https://blog.csdn.net/Jiangtagong/article/details/108703123)
 - 半连接队列和全连接队列：[链接](https://blog.csdn.net/qq_34827674/article/details/106448326)
 - listen()的backlog参数：[博客1](https://blog.csdn.net/yangbodong22011/article/details/60399728)、[博客2](https://blog.csdn.net/ordeder/article/details/21551567)

		linux内核2.2之前，backlog参数=半连接队列长度+已连接队列长度
		linux内核2.2之后，backlog参数=已连接队列（Accept队列）长度

 - [socket套接字及缓冲区详解](https://blog.csdn.net/daaikuaichuan/article/details/83061726?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)


 ## 资源

尹圣雨版的TCP IP网络编程pdf和源码下载链接：

链接：[https://pan.baidu.com/s/1PAc3IapVmcZyPfmlY3r27g](https://pan.baidu.com/s/1PAc3IapVmcZyPfmlY3r27g) 

提取码：5dr3 
