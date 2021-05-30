@[TOC](目录)

## 1、cd

```c
cd xxx	//进入xxx目录
cd ..	//返回上一级目录
cd ~	//进入当前用户的home目录
cd /	//进入根目录
```

关于linux目录结构可见[链接](https://blog.csdn.net/weixin_44164489/article/details/108553933)。
## 2、ls
显示指定工作目录下之内容

```cpp
ls		//显示所有文件及目录（不含隐藏文件）
ls -a	//显示所有文件及目录（含隐藏文件）
ls -l	//除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出
```

## 3、wc

```cpp
wc [-clw][filename]
-c # 字节
-l # 行数
-w # 字数
# 默认的情况下，wc将计算指定文件的行数、字数，以及字节数。
$ wc README.md
    29      56     366 README.md

```
## 4、cat
cat命令用以将文件、标准输入内容打印至标准输出。常用于显示文件内容、创建文件、向文件中追加内容

```cpp
cat a.cpp	//显示a.cpp的所有内容
cat a.cpp | grep  abc	//显示a.cpp中包含关键字“abc”的行
cat > b.cpp <<end	//创建b.cpp并写入内容，直到输入end为止
cat > c.cpp <<end	//对已存在的c.cpp文件写入文件内容（覆盖），直到输入end
cat >> c.cpp <<end	//对已存在的c.cpp文件末尾追加文件内容（不覆盖），直到输入end
```

更多关于cat命令可见[链接](https://blog.csdn.net/XD_hebuters/article/details/79204812?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160223303919195246602586%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160223303919195246602586&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28_p-1-79204812.pc_first_rank_v2_rank_v28_p&utm_term=cat%E5%91%BD%E4%BB%A4&spm=1018.2118.3001.4187)。

## 5、more
 more 命令用于分页显示文件内容。

```cpp
more a.cpp	//显示a.cpp的内容，按空格显示下一页，按b回到上一页，按回车显示下一行，按q离开
```

更多关于more命令可见[链接](https://blog.csdn.net/yychuyu/article/details/89926703?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160223807619724848365299%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160223807619724848365299&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28_p-4-89926703.pc_first_rank_v2_rank_v28_p&utm_term=more%E5%91%BD%E4%BB%A4&spm=1018.2118.3001.4187)。

## 6、less
less命令与more命令 非常类似，但less命令可以更加随意地浏览文件，而且 less 在查看之前不会加载整个文件。

```cpp
less a.cpp	//查看a.cpp的内容，用上下方向键进行上下翻滚
```

更多关于less命令可见[链接](https://blog.csdn.net/djaksj8721/article/details/101439524?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param)



## 7、cp
主要用于复制文件或目录

```cpp
cp [filename] [filepath]	//默认复制文件
//复制文件夹要带上 -r
$ cp –r test/ newtest 	//将当前目录 test/ 下的所有文件复制到新目录 newtest 下

```

## 8、mv
用来为文件或目录改名、或将文件或目录移入其它位置

```cpp
mv [filename] [filepath]

//目标目录与原目录一致，指定了新文件名，效果就是仅仅重命名
$ mv  /home/a.txt   /home/b.txt
//目标目录与原目录不一致，没有指定新文件名，效果就是仅仅移动
$ mv  /home/a.txt   /home/test/
//目标目录与原目录不一致, 指定了新文件名，效果就是：移动 + 重命名
$ mv  /home/a.txt   /home/test/c.txt
```

## 9、top

用于实时显示进程的动态

```cpp
top	//显示进程信息
top -d xxx	//每隔xxx秒更新一次进程信息

//top视图下按 b可以高亮正在运行的进程
```

更多关于top命令可见[链接](https://blog.csdn.net/weixin_44164489/article/details/108814967)。

## 10、ps
用于显示当前进程的状态，得到的是个快照，不会像top一样实时更新

```cpp
ps -e	//显示所有进程
ps -A	//与ps -e一样
ps -aux	//显示所有进程及详细信息（包含其它用户的进程）
ps -ef	//系统中所有用户的所有进程的完整列表
ps -T -p  id	//查看进程号为id的进程中的线程
```
[ps aux、ps -aux、ps -ef之间的区别](https://blog.csdn.net/wynter_/article/details/73825978?biz_id=102&utm_term=ps-%20aux&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-73825978&spm=1018.2118.3001.4187)

关于ps命令详细可见[链接](https://blog.csdn.net/qq_36838191/article/details/83022705?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160229867819195264747832%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160229867819195264747832&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-83022705.pc_first_rank_v2_rank_v28_p&utm_term=ps%E5%91%BD%E4%BB%A4&spm=1018.2118.3001.4187)

## 11、rm
用于删除一个文件或者目录

```cpp
rm [filename/path]
-f 	//即使原档案属性设为唯读，亦直接删除，无需逐一确认
-r 	//将目录及以下之档案亦逐一删除
//传说中的删库跑路
rm -rf [filepath]
```

## 12、pwd
用于显示当前工作目录

```cpp
pwd		//显示当前所处目录
```

## 13、mkdir

```cpp
mkdir [-p] [dirpath]
-p 	// 确保目录名称存在，不存在的就建一个
//本例若不加 -p 参数，且原本 temp 目录不存在，则产生错误
$ mkdir -p /home/temp/test
```

## 14、grep
用于查找文件里符合条件的字符串

```cpp
grep [pattern] [filename]
//查找后缀有 file 字样的文件中包含 test 字符串的文件并打印出该字符串的行
grep test *file 
grep -r include /home //在home目录下递归查找所有包含include字符串的文件
```

ps 搭配 grep，有一个很常用的命令

根据进程名/进程id搜索进程状态：

```cpp
ps -ef | grep [进程名/进程id]
如：ps -aux | grep R		//可以查找出包含字符“R”的进程信息，因此可以快速找到状态R的进程
```

## 15、kill
关闭执行中的程序或工作

```cpp
kill -9 [pid] 	//强制杀死进程
kill -15[pid]	//-15是默认的kill方式
```

更多关于kill可见[链接](https://blog.csdn.net/bocai8058/article/details/82932403)。

## 16、chmod
chmod是Linux/Unix中修改文件或者目录权限的命令，通过修改权限可以让指定的人对文件可读、可写、可运行，极大地保证了数据的安全性。

```cpp
chmod -R 777  file		//将file这个文件夹及文件夹内所有内容的权限改为对所有用户可读，可写，可执行，-R表示递归修改
```

更多关于chmod可见[链接](https://blog.csdn.net/jerrytomcat/article/details/81744860?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160229220419725271735829%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160229220419725271735829&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-6-81744860.pc_first_rank_v2_rank_v28_p&utm_term=chmod&spm=1018.2118.3001.4187)。

## 17、netstat
Netstat是控制台命令,是一个监控TCP/IP网络的非常有用的工具，它可以显示路由表、实际的网络连接以及每一个网络接口设备的状态信息。Netstat用于显示与IP、TCP、UDP和ICMP协议相关的统计数据，一般用于检验本机各端口的网络连接情况。

```csharp
netstat -a	//列出所有端口
netstat -at	//列出所有tcp端口
netstat -au	//列出所有udp端口
netstat -l	//只显示监听端口
netstat -s	//显示所有端口的统计信息
```
更多关于netstat可见[链接](https://blog.csdn.net/dongl890426/article/details/86981901?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160230743919724848322591%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160230743919724848322591&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-3-86981901.pc_first_rank_v2_rank_v28_p&utm_term=netstat&spm=1018.2118.3001.4187)。

## 18、rename
见[链接](https://blog.csdn.net/weixin_44164489/article/details/108832971)。
## 19、file、stat

```cpp
file filename	//查看filename的文件类型
stat filename	//查看filename的具体信息
```

更多可见[链接](https://blog.csdn.net/weixin_44164489/article/details/108815583)。

## 20、zip、unzip

用于进行压缩和解压缩，对应的压缩包为zip格式

```cpp
zip file.zip file	//将file文件夹压缩成zip形式
unzip file.zip	//解压缩，解压后文件放在当前目录下
```
## 21、which、whereis、locate、find

```cpp
whichis ls	//显示ls可执行程序所处路径
whereis ls	//返回与ls匹配的二进制文件、源文件和帮助手册文件所在的路径

//注意：locate是找绝对路径，因此采用locate file*无法找到其绝对路径名
locate *file	//找出名为file的文件所处路径，高效，注意前面一定要加上*
locate *file*	//找出名字中含file的文件所处路径
sudo updatedb //locate的数据库默认一天更新一次，可以用该命令立即更新

find file	//与locate类似，较慢，比locate低效
find /home  -name *.cpp	//常用！在home目录下查找含有cpp后缀的所有文件
```


更多关于which、whereis、locate、find详见[链接](https://blog.csdn.net/u010625000/article/details/44455023)


## 22、ulimit
查看linux各项资源的限制

```cpp
ulimit -a	//查看所有资源的限制
ulimit -n	//查看最大文件描述符数量，一般为1024
ulimit -u	//查看最大进程数目
ulimit -n 2048	//将最大文件描述符数量改为2048
```

更多可见[链接](https://blog.csdn.net/tustzhoujian/article/details/81666062?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160241173219725271722107%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160241173219725271722107&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-81666062.pc_first_rank_v2_rank_v28_p&utm_term=ulimit&spm=1018.2118.3001.4187)。


## 23、pkill
可以直接杀掉指定名字的进程，而kill需要指定进程ID

```cpp
pkill redis	//把redis进程杀掉
```
## 24、df
df用来检查linux服务器的文件系统的磁盘空间占用情况。

```cpp
df -a	//查看全部文件系统，单位默认KB
df -h	//以人类可阅读的方式显示磁盘空间占用情况，单位GB
```

详细可见[链接](https://blog.csdn.net/hgelin/article/details/82113441?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160242486119725271742037%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160242486119725271742037&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28_p-2-82113441.pc_first_rank_v2_rank_v28_p&utm_term=df%E5%91%BD%E4%BB%A4&spm=1018.2118.3001.4187)。

## 25、du
显示每个文件和目录的磁盘使用空间。

```cpp
du -h	//以K,M,G为单位显示所有目录或文件的大小，提高信息可读性
//以下命令都可在最后一个字符后加个h，增加可读性
du -a	//显示所有目录或文件的大小
du -c	//显示目录或文件的大小总和
du -s	//仅显示目录或文件的总计大小数值
```

更多可见[链接](https://blog.csdn.net/linuxnews/article/details/51207738?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160242512319725271712580%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160242512319725271712580&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28_p-2-51207738.pc_first_rank_v2_rank_v28_p&utm_term=du%E5%91%BD%E4%BB%A4&spm=1018.2118.3001.4187)。
## 26、pstree
pstree命令是用于查看进程树，可以看出进程之间的关系，即哪个进程是父进程，哪个是子进程，可以清楚的看出来是谁创建了谁

```cpp
pstree
pstree -a
```
## 27、free
free 命令显示系统内存的使用情况

```cpp
free -h		//显示系统内存使用情况（含单位）
free -s 5	//每隔五秒输出一次内存使用情况
```

更多可见[链接](https://blog.csdn.net/liuwkk/article/details/108820845?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160249366419724836749701%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160249366419724836749701&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-108820845.pc_first_rank_v2_rank_v28_p&utm_term=free%E5%91%BD%E4%BB%A4&spm=1018.2118.3001.4187)。

## 28、size
size 命令基本上就是输出指定输入文件的各段及其总和的大小。

```cpp
size test	//得到可执行程序test的text、data、bss段大小和总大小
//输出中的dec、hex是10进制、16进制表示的总大小
```

更多可见[链接](https://blog.csdn.net/F8qG7f9YD02Pe/article/details/79787555?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param)。
## 29、ip
linux的ip命令和ifconfig类似，但前者功能更强大，并旨在取代后者。 

```cpp
ip addr	//查看ip地址
```

详见[此博客](https://blog.csdn.net/cool_summer_moon/article/details/78752291?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522160362755319724835863270%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=160362755319724835863270&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v28-1-78752291.pc_first_rank_v2_rank_v28&utm_term=linux%20ip&spm=1018.2118.3001.4187)。
## 30、watch
watch命令可以实时全屏监控当前命令执行的动态变化结果。watch命令的常用参数有“-n”、“-d”、“-t”分别表示“时隔多少秒刷新”、“高亮显示动态变化”、“关闭命令顶部的时间间隔,命令显示”

```cpp
watch -n 5 ps -ef	//每隔5秒钟刷新一次ps -ef
```

详见[链接](https://blog.csdn.net/weixin_47763101/article/details/106297834)
## 31、sort

```cpp
sort a.txt	//对a.txt的每一行文本内容进行排序，升序
sort -r a.txt //降序
```

## 其它

### 1、sed

把所有文件中的hello替换为world（**重要**）：
```cpp
sed -i "s/hello/world/g"  *
```

输出hello.txt的第3行到最后一行：

```cpp
sed -n '3,$'p hello.txt
```

匹配以10开头的行，并替换为yes，并输出

```cpp
sed -n 's/^10/yes/p' hello.txt
```

删除匹配100的行：

```cpp
sed '/100/'d hello.txt
```

更多关于sed可见[链接](https://mp.weixin.qq.com/s/29iMrw1CFpmLiW36p40szw)。

### 2、awk
逐行处理文件中的数据

输出hello.txt文件中第3到5行：

```cpp
awk 'NR == 3, NR == 5{print;}' hello.txt
```

输出hello.txt第3列：

```cpp
awk '{print $3}' hello.txt
```

输出hello.txt第2行、第3列：

```cpp
sed -n "2p" hello.txt | awk '{print $3}'
```

输出hello.txt中，正则匹配hello的行

```cpp
awk '/hello/' hello.txt
```

更多关于awk可见 [链接](https://mp.weixin.qq.com/s/ofvB31w5rRywIdUUtOjskw)。



## 参考资料

 - [http://szufrank.top/#/./docs/linux?id=_3-%e5%8f%82%e8%80%83](http://szufrank.top/#/./docs/linux?id=_3-%E5%8F%82%E8%80%83)



