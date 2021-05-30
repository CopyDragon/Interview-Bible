今天看了下这篇博客：[教你写Makefile（很全，含有工作经验的）](https://blog.csdn.net/qq_16234613/article/details/81413084?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160171328319724836704713%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160171328319724836704713&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-3-81413084.pc_first_rank_v2_rank_v28_p&utm_term=makefile&spm=1018.2118.3001.4187)

自己也试着实验了一下~

我分别编写了三个cpp文件：a.cpp、b.cpp、c.cpp，依赖关系为a依赖b，b依赖c


a.cpp:

```cpp
#include<iostream>
#include"b.cpp"
using namespace std;
int main(){
	cout<<"a";
	testb();
	return 0;
}
```

b.cpp:

```cpp
#include<iostream>
#include"c.cpp"
using namespace std;
void testb(){
	cout<<"b";
	testc();
}
```

c.cpp:

```cpp
#include<iostream>
using namespace std;
void testc(){
	cout<<"c";
}
```


根据三个cpp的依赖关系：依赖关系为a依赖b，b依赖c

编写以下makefile文件：

```cpp
test: a.o
	g++ -o test a.o
a.o: a.cpp b.o
	g++ -c a.cpp b.o
b.o: b.cpp c.o
	g++ -c b.cpp c.o
c.o: c.cpp
	g++ -c c.cpp
clean:
	rm *.o
	rm test
```

上述makefile文件可用“make”指令生成名为test可执行文件，也可以用"make clean"指令来删掉所有的.o文件和test执行文件。

运行结果如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003170009336.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDE2NDQ4OQ==,size_16,color_FFFFFF,t_70#pic_center)
为了更好测试这种依赖关系所带来的的编译效率，我要修改一下代码的依赖关系，改成：a依赖b、c

a.cpp:

```cpp
#include<iostream>
#include"b.cpp"
#include"c.cpp"
using namespace std;
int main(){
	cout<<"a";
	testb();
	testc();
	return 0;
}
```

b.cpp:

```cpp
#include<iostream>
using namespace std;
void testb(){
	cout<<"b";
}
```

c.cpp:

```cpp
#include<iostream>
using namespace std;
void testc(){
	cout<<"c";
}
```

makefile:

```cpp
test: a.o
	g++ -o test a.o
a.o: a.cpp b.o c.o
	g++ -c a.cpp b.o c.o
b.o: b.cpp 
	g++ -c b.cpp 
c.o: c.cpp
	g++ -c c.cpp
clean:
	rm *.o
	rm test
```

先执行一次make看看：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003171138345.jpg#pic_center)


然后将b.cpp进行修改，输出的b改为bb，然后再次执行make看看：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201003171143588.jpg#pic_center)

可以发现这次少了一行编译c.cpp的命令，这是因为c.cpp文件并没有修改，不需要重新编译，而b.cpp发生了修改，导致需要重新编译出b.o和重新链接得到a.o和test文件。


可见，使用makefile可以让编译更加高效，提高开发效率。


