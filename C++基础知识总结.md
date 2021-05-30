
@[TOC](目录)
## 面试宝典
 - [牛客网面试宝典](https://www.nowcoder.com/tutorial/93/a34ed23d58b84da3a707c70371f59c21)
 - [C++高频考点梳理](http://szufrank.top/#/./interview/c++.md)
 - [C++后台开发校招面试常见问题](https://blog.csdn.net/shanghairuoxiao/article/details/72876248)

## 基础知识点
 - 内存对齐： [内存对齐的作用](https://blog.csdn.net/CC_clear/article/details/77018250)、[博客2](https://blog.csdn.net/cyousui/article/details/17655051?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&dist_request_id=ee1ca678-b93b-4717-899d-9fdcf1a1e0a5&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)、[博客3](https://blog.csdn.net/hairetz/article/details/4084088?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.control&dist_request_id=283d845d-de22-44bf-bdf5-bf1d93a259a9&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.control)

		规则：
		1、每个变量所对应的偏移量都必须是该变量本身所占用字节数的整数倍。
		2、该结构体整体占用内存大小必须是结构体中占用最大内存变量的字节数的整数倍

		可以使用#pragma pack(x)来指定按 x 字节的整数倍来对齐。

	
 - 函数指针、回调函数：[博客1](https://blog.csdn.net/u010280075/article/details/88914424)、[博客2](https://blog.csdn.net/qican_7/article/details/100669020?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161389355516780299044300%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=161389355516780299044300&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-100669020.pc_search_result_no_baidu_js&utm_term=%E5%9B%9E%E8%B0%83%E5%87%BD%E6%95%B0)
 - 四种cast操作符：[C++四种cast操作符](https://blog.csdn.net/starryheavens/article/details/4617637)、[C++中static_cast和dynamic_cast强制类型转换](https://blog.csdn.net/qq_26849233/article/details/62218385?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160656458319724816638112%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160656458319724816638112&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-3-62218385.pc_search_result_cache&utm_term=dynamic_cast%E8%BD%AC%E6%8D%A2%E9%94%99%E8%AF%AF%E4%BC%9A%E8%BF%94%E5%9B%9E&spm=1018.2118.3001.4449)、[dynamic_cast转换类指针时，基类需要虚函数](https://blog.csdn.net/oyhb_1992/article/details/80023113?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160656716819726891130293%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160656716819726891130293&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-5-80023113.pc_search_result_cache&utm_term=dynamic_cast%E8%99%9A%E5%87%BD%E6%95%B0&spm=1018.2118.3001.4449)
 
 	关于dynamic_cast和虚函数的关系的例子见[此博客](https://blog.csdn.net/langb2014/article/details/50070619?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160656458319724816638112%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160656458319724816638112&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-1-50070619.pc_search_result_cache&utm_term=dynamic_cast%E8%BD%AC%E6%8D%A2%E9%94%99%E8%AF%AF%E4%BC%9A%E8%BF%94%E5%9B%9E&spm=1018.2118.3001.4449)。
		
		dynamic_cast转换错误会返回什么？ 答：NULL
		
	const_cast：[博客](https://blog.csdn.net/TanJiaLiang_/article/details/83992337?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161398131616780266232224%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=161398131616780266232224&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-3-83992337.pc_search_result_no_baidu_js&utm_term=c%2b%2b%20constcast)
			
		const_cast要通过指针使用。
		const_cast转换之后的数据依然是常量，不能通过赋值修改。
		之所以使用const_cast，是因为我们可能调用了一个参数不是const的函数，而我们要传进去的实际参数确实是const的，于是我们就需要使用const_cast去除const限定，以便函数能够接受这个实际参数。
	
 - 右值引用：[右值引用与移动构造函数](https://winsoft666.blog.csdn.net/article/details/78520237?utm_medium=distribute.pc_relevant_t0.none-task-blog-OPENSEARCH-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-OPENSEARCH-1.control)（重点看）、[博客1](https://blog.csdn.net/qq844352155/article/details/34412409)、[博客2](https://blog.csdn.net/tonglin12138/article/details/91479048)、[c++ 之 std::move ](https://blog.csdn.net/p942005405/article/details/84644069?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522160889165116780266271122%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=160889165116780266271122&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-84644069.nonecase&utm_term=move%E7%9A%84%E5%BA%95%E5%B1%82)
 - 引用：[引用和指针的区别](https://blog.csdn.net/Listening_music/article/details/6921608?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160629119919724844408180%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160629119919724844408180&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-1-6921608.pc_search_result_cache&utm_term=%E5%BC%95%E7%94%A8%E5%92%8C%E6%8C%87%E9%92%88%E5%8C%BA%E5%88%AB&spm=1018.2118.3001.4449)

		引用和指针做函数参数的区别？
		sizeof(指针)和sizeof(引用)的区别？
		指针能否为空，引用能否为空？

 - [“悬空指针”和“野指针”的区别](https://blog.csdn.net/ybhuangfugui/article/details/106435406?utm_medium=distribute.pc_relevant.none-task-blog-utm_term-3&spm=1001.2101.3001.4242)
 - [【C++】strlen 和sizeof 的区别（小结）](https://blog.csdn.net/ly_6699/article/details/89482591?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160629274919725255504223%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160629274919725255504223&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-1-89482591.pc_search_result_cache&utm_term=strlen%E5%92%8Csizeof&spm=1018.2118.3001.4449)

 - Lambda表达式：[博客](https://blog.csdn.net/weixin_44164489/article/details/106843981)
 - 智能指针：[博客1](https://blog.csdn.net/weixin_44164489/article/details/108125297)、[博客2](https://blog.csdn.net/zhuoya_/article/details/79926971)

 - 内存管理：堆、栈、自由存储区（抽象概念）、全局/静态存储区、常量存储区、代码区

 

 - new与delete的工作步骤：
				
		使用new操作符来分配对象内存时会经历三个步骤：
		
		第一步：调用operator new 函数（对于数组是operator new[]）分配一块足够大的，原始的，未命名的内存空间以便存储特定类型的对象。
		第二步：编译器运行相应的构造函数以构造对象，并为其传入初值。
		第三步：对象构造完成后，返回一个指向该对象的指针。
		
		使用delete操作符来释放对象内存时会经历两个步骤：
		
		第一步：调用对象的析构函数。
		第二步：编译器调用operator delete(或operator delete[])函数释放内存空间。
 - [C++中的delete和delete[ ]的区别](https://blog.csdn.net/u012936940/article/details/80919880?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161406316616780357265061%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=161406316616780357265061&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-80919880.pc_search_result_no_baidu_js&utm_term=delete%E5%92%8Cdelete%5B%5D)

 - new与malloc的区别：[博客](https://blog.csdn.net/weixin_44164489/article/details/108249123)
 - string底层：[博客](https://blog.csdn.net/weixin_44164489/article/details/108620217)

 - C++11：[十大必掌握C++11新特性](https://blog.csdn.net/FX677588/article/details/70157088?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160507826819195264704881%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160507826819195264704881&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-3-70157088.pc_first_rank_v2_rank_v28&utm_term=C%2b%2b11&spm=1018.2118.3001.4449)

 - tuple元组：[博客1](https://blog.csdn.net/sevenjoin/article/details/88420885?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160507955719725255515436%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160507955719725255515436&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-2-88420885.pc_first_rank_v2_rank_v28&utm_term=c%2b%2b%20%E5%85%83%E7%A5%96&spm=1018.2118.3001.4449)、[博客2](https://blog.csdn.net/netyeaxi/article/details/83539928?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.add_param_isCf&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.add_param_isCf#%E4%B8%89%E3%80%81%E5%A6%82%E4%BD%95%E8%8E%B7%E5%8F%96std::tuple%E4%B8%AD%E5%AD%98%E6%94%BE%E7%9A%84%E5%85%83%E7%B4%A0%E4%B8%AA%E6%95%B0)
 - [pair的基本用法](https://blog.csdn.net/weixin_44164489/article/details/108312730)
 - [bitset用法](https://blog.csdn.net/weixin_44164489/article/details/108010507)
 - [malloc的底层实现](https://blog.csdn.net/z_ryan/article/details/79950737?biz_id=102&utm_term=malloc%E5%8E%9F%E7%90%86&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-79950737&spm=1018.2118.3001.4449)
		
		brk（）的参数设置为新的heap上界地址，成功返回1，失败返回0； 
		sbrk（）的参数为申请内存的大小，返回heap新的上界的地址；
		mmap（）向映射区申请一块内存。
		
		malloc采用的是内存池的管理方式，使用空闲链表管理内存块。
		首先在空闲链表寻找内存块进行分配，不行就向heap申请，
		heap不够就判断需要分配的空间大小，若小于mmap分配阈值（128kb）就调用sbrk来扩大heap，若大于阈值则调用mmap向映射区申请内存。
		 
 - const和#define的区别：[博客1](https://blog.csdn.net/weibo1230123/article/details/81981384?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160509293319724838559181%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160509293319724838559181&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-2-81981384.pc_first_rank_v2_rank_v28&utm_term=const%E5%92%8Cdefine%E7%9A%84%E5%8C%BA%E5%88%AB&spm=1018.2118.3001.4449)、[博客2](https://blog.csdn.net/yi_ming_he/article/details/70405364?biz_id=102&utm_term=const%E5%92%8Cdefine%E7%9A%84%E5%8C%BA%E5%88%AB&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-70405364&spm=1018.2118.3001.4449)
 - 内联函数：[博客1](https://blog.csdn.net/cpongo3/article/details/93996094)、[博客2](https://blog.csdn.net/u011327981/article/details/50601800)
 - c++读写文本文件和二进制文件：[read()和write()](http://c.biancheng.net/view/7603.html)、[>>和<<](http://c.biancheng.net/view/7596.html)、[文本文件以及二进制文件的读写](https://blog.csdn.net/Lemon_CHA/article/details/108295844?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522160982579916780263070366%252522%25252C%252522scm%252522%25253A%25252220140713.130102334.pc%25255Fall.%252522%25257D&request_id=160982579916780263070366&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-4-108295844.pc_search_result_no_baidu_js&utm_term=c%20%20%20%E6%96%87%E6%9C%AC%E6%96%87%E4%BB%B6%E5%92%8C%E4%BA%8C%E8%BF%9B%E5%88%B6%E6%96%87%E4%BB%B6)

		read()和write()用于以二进制方式读写，运算符>>和<<以文本方式读写

 - volatile关键字：[作用](https://blog.csdn.net/qq_40843865/article/details/90729496)、[场景](https://blog.csdn.net/liuhhaiffeng/article/details/52494299)

 - [用程序判断大端、小端](https://blog.csdn.net/qq_36391130/article/details/81944217)（记住联合体的方法）
 - i++不是原子操作：[博客1](https://blog.csdn.net/YEYUANGEN/article/details/19612795?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522161224826516780271528623%252522%25252C%252522scm%252522%25253A%25252220140713.130102334.pc%25255Fall.%252522%25257D&request_id=161224826516780271528623&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-3-19612795.pc_search_result_no_baidu_js&utm_term=37.%2509%252B%252Bi%25E6%2598%25AF%25E5%2590%25A6%25E6%2598%25AF%25E5%258E%259F%25E5%25AD%2590%25E6%2593%258D%25E4%25BD%259C)、[博客2](https://blog.csdn.net/huaweitman/article/details/38352345?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522161224826516780271528623%252522%25252C%252522scm%252522%25253A%25252220140713.130102334.pc%25255Fall.%252522%25257D&request_id=161224826516780271528623&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-4-38352345.pc_search_result_no_baidu_js&utm_term=37.%2509%252B%252Bi%25E6%2598%25AF%25E5%2590%25A6%25E6%2598%25AF%25E5%258E%259F%25E5%25AD%2590%25E6%2593%258D%25E4%25BD%259C)
 - i++在两个线程里边分别执行100次，能得到的最大值和最小值？[博客1](https://blog.csdn.net/zhangrui_fslib_org/article/details/50311195?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522161224872516780266228131%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=161224872516780266228131&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-50311195.pc_search_result_no_baidu_js&utm_term=i%252B%252B%25E5%259C%25A8%25E4%25B8%25A4%25E4%25B8%25AA%25E7%25BA%25BF%25E7%25A8%258B%25E9%2587%258C%25E8%25BE%25B9%25E5%2588%2586%25E5%2588%25AB%25E6%2589%25A7%25E8%25A1%258C100%25E6%25AC%25A1)、[博客2](https://blog.csdn.net/will130/article/details/48714343?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)

		i=0,i++在两个线程分别执行100次 -> [2,200]
		j=100，两个线程j–-，均执行50次 -> [0,98]

 - 模板类中可以使用虚函数吗？模板成员函数可以是虚函数吗？[博客1](https://blog.csdn.net/zzuchengming/article/details/51763563?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161616682416780271564518%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=161616682416780271564518&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-2-51763563.first_rank_v2_pc_rank_v29&utm_term=%E6%A8%A1%E6%9D%BF%E5%8F%AF%E4%BB%A5%E8%99%9A%E5%87%BD%E6%95%B0)、[博客2](https://blog.csdn.net/jcwKyl/article/details/3771059?utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromMachineLearnPai2~default-1.control&dist_request_id=&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromMachineLearnPai2~default-1.control)
 - [const修饰的对象能调用所有函数吗？](https://blog.csdn.net/qq_33726635/article/details/105200480?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161616694616780264022938%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=161616694616780264022938&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-1-105200480.first_rank_v2_pc_rank_v29&utm_term=const%E4%BF%AE%E9%A5%B0%E5%AF%B9%E8%B1%A1%E8%83%BD%E8%B0%83%E7%94%A8%E6%89%80%E6%9C%89%E5%87%BD%E6%95%B0)
 - [怎么限制一个类的对象实例,只能在"堆"上分配,或者只能在"栈"上分配](https://blog.csdn.net/u010536615/article/details/45337841?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161685010616780264067705%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=161685010616780264067705&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-1-45337841.pc_search_result_cache&utm_term=%E5%AF%B9%E8%B1%A1%E5%8F%AA%E8%83%BD%E5%9C%A8%E6%A0%88%E4%B8%8A)

## 封装、继承、多态
 - 多重继承：[博客1](https://blog.csdn.net/qq_28584889/article/details/88753181)、[博客2](https://blog.csdn.net/weixin_44164489/article/details/106792535)
 - 多重（菱形）继承的内存布局：[博客1](https://blog.csdn.net/lizhidefengzi/article/details/57124230)、[博客2](https://blog.csdn.net/Code_beeps/article/details/94162612)、[博客3](https://blog.csdn.net/M_jianjianjiao/article/details/85260429)

		虚基表指针记录虚基表的地址，虚基表记录公共基类成员相对于虚基表指针地址的偏移量，
		通过偏移量可以找到公共基类成员的位置
 
 - [C++ 公有继承、保护继承和私有继承的对比详解](https://blog.csdn.net/weixin_28712713/article/details/80967650)
 - [C++静态多态与动态多态](https://blog.csdn.net/qq_37934101/article/details/81365449?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161431669716780274125195%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=161431669716780274125195&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-81365449.first_rank_v2_pc_rank_v29_10&utm_term=%E9%9D%99%E6%80%81%E5%A4%9A%E6%80%81) **（重要！！）**
 - [C++多态（虚函数、静态链接、动态链接、虚函数表、虚表指针）](https://blog.csdn.net/weixin_45146520/article/details/109537291)
 
 			虚函数的调用关系：this->vptr->虚函数表->虚函数
 

 - 虚函数表指针以及虚函数表创建时机：[博客1](https://blog.csdn.net/qq_38158479/article/details/106970213)、[博客2](https://blog.csdn.net/Linux_ever/article/details/51056251)

		子类对象的vptr指针指向子类虚函数表，但是在调用父类的构造函数的时候创建，可以认为Vptr指针是属于父类的成员，但在调用子类的构造函数时Vptr又被赋值指向子类的虚函数表。

 - [this指针和虚函数理解](https://blog.csdn.net/anribras/article/details/76445455?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522160913620816780257436320%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=160913620816780257436320&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-76445455.nonecase&utm_term=this%E6%8C%87%E9%92%88%20vptr)

 - 虚函数表位于只读数据段（.rodata），也就是C++内存模型中的常量区；而虚函数则位于代码段（.text），也就是C++内存模型中的代码区：[C++中的虚函数表和虚函数在内存中的位置](https://blog.csdn.net/qq_28114615/article/details/98041319?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160656816319724818015839%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160656816319724818015839&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-1-98041319.pc_search_result_cache&utm_term=%E8%99%9A%E5%87%BD%E6%95%B0%E5%9C%A8%E5%86%85%E5%AD%98)
 
 -  重写、重载、重定义：[博客1](https://blog.csdn.net/xu1105775448/article/details/80118159?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160507878619725266920768%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160507878619725266920768&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-2-80118159.pc_first_rank_v2_rank_v28&utm_term=C%2b%2b%E9%87%8D%E5%86%99%E5%92%8C%E9%87%8D%E8%BD%BD&spm=1018.2118.3001.4449)、[博客2](https://blog.csdn.net/zhejfl/article/details/90199200?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160507878619725266920768%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160507878619725266920768&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-90199200.pc_first_rank_v2_rank_v28&utm_term=C%2b%2b%E9%87%8D%E5%86%99%E5%92%8C%E9%87%8D%E8%BD%BD&spm=1018.2118.3001.4449) 
 - 虚函数返回值协变： [c++返回类型协变](https://blog.csdn.net/gjggj/article/details/72626794?locationNum=2&fps=1&ops_request_misc=&request_id=&biz_id=102&utm_term=c%20%20%E5%8D%8F%E5%8F%98&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-72626794.first_rank_v2_pc_rank_v29)
 - [C++面试题之浅拷贝和深拷贝的区别](https://blog.csdn.net/caoshangpa/article/details/79226270?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-%20%20-%20BlogCommendFromMachineLearnPai2-1.control)
 - 重载运算符：[代码](https://paste.ubuntu.com/p/9kyphvWvFP/)
 - [C++中构造函数，拷贝构造函数和重载赋值运算符的区别和实现](https://blog.csdn.net/zcyzsy/article/details/52132936?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160629460019724843337164%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160629460019724843337164&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-1-52132936.pc_search_result_cache&utm_term=%E6%8B%B7%E8%B4%9D%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E5%92%8C%E8%B5%8B%E5%80%BC%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E7%9A%84%E5%8C%BA%E5%88%AB&spm=1018.2118.3001.4449)

	重载赋值运算符时有指针变量：先释放原本指向的堆内存空间，再进行深拷贝。
		
	```cpp
	/*
		对象不存在，且没用别的对象来初始化，就是调用了构造函数；

        对象不存在，且用别的对象来初始化，就是拷贝构造函数;

   	 	对象存在，用别的对象来给它赋值，就是赋值函数。
	*/
	
	class  A;
	A a;
	A b=a;   //调用拷贝构造函数（b不存在）
	A c(a) ;   //调用拷贝构造函数
	 
	/****/
	 
	class  A;
	A a;
	A b;   
	b = a ;   //调用赋值函数(b存在)</span>
	```
	

 - 能不能同时用static和const修饰类的成员函数？ [博客1](https://blog.csdn.net/bxyill/article/details/8444391?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160672705519725211996370%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160672705519725211996370&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-5-8444391.pc_search_result_cache&utm_term=const,%20static%E8%83%BD%E5%A4%9F%E4%BF%AE%E9%A5%B0%E5%90%8C%E4%B8%80%E4%B8%AA%E7%B1%BB%E6%88%90%E5%91%98%E5%87%BD%E6%95%B0&spm=1018.2118.3001.4449)、[博客2](https://blog.csdn.net/chan0311/article/details/61425051?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160672744619724827698972%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=160672744619724827698972&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-2-61425051.pc_search_result_cache&utm_term=%E5%9C%A8%E5%87%BD%E6%95%B0%E4%B8%AD%E6%B7%BB%E5%8A%A0%E4%B8%80%E4%B8%AA%E9%9A%90%E5%BC%8F%E7%9A%84%E5%8F%82%E6%95%B0const%20this&spm=1018.2118.3001.4449)
 - 哪些函数不能设置为虚函数：[博客1](https://blog.csdn.net/qq_39750086/article/details/81462568)、 [C++中构造函数不能声明为虚函数](https://blog.csdn.net/wk_bjut_edu_cn/article/details/80187658)

		构造函数不能为虚函数的原因：
		假设构造函数为虚函数，虚函数执行依赖于虚函数表，找到虚函数表要通过对象中的vptr指针，
		然而此时该对象构造函数还未执行，vptr指针还没能完成初始化，找不到虚函数表，因此二者矛盾。
		
		静态成员函数不能为虚函数的原因：
		静态成员函数没有this指针，虚函数的实现是为每一个对象分配一个vptr指针指向虚函数表，而vptr是通过this指针调用的，所以不能为virtual。
	

 - 阻止一个类在外部被实例化的方法：[博客1](https://blog.csdn.net/Feng_8071/article/details/52704253?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522161182624416780271574128%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=161182624416780271574128&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-52704253.pc_search_result_no_baidu_js&utm_term=%25E5%25B0%2586%25E6%259E%2584%25E9%2580%25A0%25E5%2587%25BD%25E6%2595%25B0%25E5%25A3%25B0%25E6%2598%258E%25E4%25B8%25BAprivate)、[博客2](https://blog.csdn.net/liucheng_34/article/details/78409097?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522161182624416780271531693%252522%25252C%252522scm%252522%25253A%25252220140713.130102334.pc%25255Fall.%252522%25257D&request_id=161182624416780271531693&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-3-78409097.pc_search_result_no_baidu_js&utm_term=%25E5%25B0%2586%25E6%259E%2584%25E9%2580%25A0%25E5%2587%25BD%25E6%2595%25B0%25E5%25A3%25B0%25E6%2598%258E%25E4%25B8%25BAprivate)
		
		将类定义为抽象基类或者将构造函数声明为private。

		那构造函数为private时要怎么在类内构造对象？
		答：在静态成员函数中创建对象，或者利用友元函数实现。

## STL

 - STL基本概念： [概述](https://blog.csdn.net/weixin_39640298/article/details/86583252)、[STL基本组成](https://blog.csdn.net/smallerxuan/article/details/80783108?biz_id=102&utm_term=stl%E5%9F%BA%E6%9C%AC%E7%BB%84%E6%88%90&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-80783108&spm=1018.2118.3001.4449)、 [仿函数](https://blog.csdn.net/weixin_39640298/article/details/88750451)、[空间配置器](https://blog.csdn.net/weixin_44164489/article/details/108218967)、[适配器](https://blog.csdn.net/weixin_39640298/article/details/88767303?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160507752119725225033013%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160507752119725225033013&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-88767303.pc_first_rank_v2_rank_v28&utm_term=stl%E9%80%82%E9%85%8D%E5%99%A8&spm=1018.2118.3001.4449)
 - [STL容器的底层数据结构](https://blog.csdn.net/weixin_44164489/article/details/108309467)
 - [关于STL中list、deque、vector的插入删除的时间复杂度的比较](https://blog.csdn.net/like_that/article/details/98446479)
 - [C++ STL deque介绍与使用方法](https://blog.csdn.net/Cypress1010/article/details/53669396)

 - STL的List::sort()采用归并排序：[博客1](https://blog.csdn.net/lijun5635/article/details/23963707)、[博客2](https://blog.csdn.net/qq_31720329/article/details/85535787)
 -  优先队列priority_queue：[博客](https://blog.csdn.net/weixin_36888577/article/details/79937886?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.add_param_isCf&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.add_param_isCf)
 - 仿函数：[greater()、less()](https://blog.csdn.net/weixin_41921520/article/details/105006699)
 - [C++头文件algorithm的find 函数](https://blog.csdn.net/sinat_34328764/article/details/79946650?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522160947985416780310141226%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=160947985416780310141226&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-3-79946650.pc_search_result_no_baidu_js&utm_term=c%20%20%20find)
 - vector调用push_back如果发生扩容：
	
	[关于c++中vector的push_back、拷贝构造和移动构造](https://blog.csdn.net/Nie_Quanxin/article/details/81187468)
	
		当vector容量不足扩容时对旧元素调用的是移动构造函数，对于新加入的元素调用的是拷贝构造函数或者移动构造函数；
		那么对于有n个元素的vector调用push_back，若不涉及扩容，则调用一次拷贝构造函数或者移动构造函数；若涉及扩容，则调用n次移动构造函数和一次拷贝构造函数或者移动构造函数。

		因此当vector存储自定义对象的时候，如果有指针，记得要在自定义类中补充拷贝构造函数（保证深拷贝）和移动构造函数（扩容时直接转移所有权，不需要拷贝，高效）。

 - [ emplace_back() 与 push_back() 的区别](https://blog.csdn.net/lemonxiaoxiao/article/details/108595548)
 - push_back的时间复杂度：[博客1](https://blog.csdn.net/u011417820/article/details/79959825)、[博客2](https://blog.csdn.net/q_l_s/article/details/52640365)
	
		倍增因子为m，直接记住时间复杂度为O(m/(m-1))即可！！！
		2倍扩容为O(2)，1.5倍扩容为O(3) 。
	
		假设N个数，则有：2^0,  2^1, 2^2, ..., 2^log(N-1)
		总时间复杂度=2(1-2^logN)/(1-2)= 2^(logN+1)-2=2N-2
		平均时间复杂度=(2N-2)/N=2*(N-1)/N=2
		因此两倍扩容时，时间复杂度为O(2)。


	

 - accumulate函数：[博客1](https://blog.csdn.net/qq_40803710/article/details/80273811?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522161258189416780261927063%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=161258189416780261927063&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-80273811.pc_search_result_no_baidu_js&utm_term=accumulate)、[博客2](https://blog.csdn.net/qq_21567767/article/details/82023752?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522161258189416780261927063%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=161258189416780261927063&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-82023752.pc_search_result_no_baidu_js&utm_term=accumulate)
 - [rbegin反向迭代器获得红黑树结构的最后一个元素](https://blog.csdn.net/weixin_42513339/article/details/102690854?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522161387846116780266231142%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=161387846116780266231142&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-102690854.pc_search_result_no_baidu_js&utm_term=map.rbegin)
 
