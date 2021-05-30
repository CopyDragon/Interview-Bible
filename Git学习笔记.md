看的是廖雪峰的[教程](https://www.liaoxuefeng.com/wiki/896043488029600)，这个教程确实很通俗易懂，适合初学者。
@[TOC](目录)

## Git安装与设置
**windows安装git：**

在Windows上使用Git，可以从Git官网直接下载[安装程序](https://git-scm.com/downloads)，然后按默认选项安装即可。

安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

安装完成后，还需要最后一步设置，在命令行输入：

```cpp
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。你也许会担心，如果有人故意冒充别人怎么办？这个不必担心，首先我们相信大家都是善良无知的群众，其次，真的有冒充的也是有办法可查的。

注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

**ubuntu安装git：**

	sudo add-apt-repository ppa:git-core/ppa       //添加源
	sudo apt-get update                                          //更新
	sudo apt-get install git                //自动安装git
	git --version                                                       //确认git版本
	
	//第一次使用前
	git config --global user.name "your name"        //设置用户名，注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。
	git config --global user.email "your email"        //设置电子邮箱
	git config user.name                                           //查看用户名
	git config user.email                                           //查看电子邮箱
	git config --list                                                    //查看所有用户信息
## 创建本地版本库

**1、在git bash进入项目文件所在的目录中。**

**2、通过git init命令把这个目录变成Git可以管理的仓库**

如下：

```cpp
$ git init
```

瞬间Git就把仓库建好了，而且告诉你是一个空的仓库（empty Git repository），细心的读者可以发现当前目录下多了一个.git的目录，这个目录是Git来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件，不然改乱了，就把Git仓库给破坏了。

如果你没有看到.git目录，那是因为这个目录默认是隐藏的，用ls -a命令就可以看见。

## 把文件添加到版本库

用命令git add告诉Git，把文件添加到仓库：

```cpp
$ git add readme.txt
```
用命令git commit告诉Git，把文件提交到仓库：

```cpp
$ git commit -m "wrote a readme file"
```

简单解释一下git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

为什么Git添加文件需要add，commit一共两步呢？因为commit可以一次提交很多文件，所以你可以多次add不同的文件，比如：

```cpp
$ git add file1.txt
$ git add file2.txt file3.txt
$ git commit -m "add 3 files."
```

**小结**

初始化一个Git仓库，使用git init命令。

添加文件到Git仓库，分两步：

使用命令git add <file>，注意，可反复多次使用，添加多个文件；

使用命令git commit -m <message>，完成提交。

## 查看工作区状态和修改

要随时掌握工作区的状态，使用git status命令。

如果要查看每一个文件的精简状态，可使用：

```cpp
git status -s
```
git status -s得到每一个文件的状态码如[此博客](https://blog.csdn.net/weixin_42239374/article/details/80368448?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param)所述。

如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

## 版本回退

每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为commit。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个commit恢复，然后继续工作，而不是把几个月的工作成果全部丢失。

版本控制系统有某个命令可以告诉我们历史记录，在Git中，我们用git log命令查看：

```cpp
$ git log
```

执行上述命令后看到的一大串类似1094adb...的是commit id（版本号）。

Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交，上一个版本就是HEAD^ ,上上一个版本就是HEAD^^。

当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。

现在，我们要把当前版本回退到上一个版本，就可以使用git reset命令：

```cpp
$ git reset --hard HEAD^
```

当回退版本之后再使用git log查看会发现最新的版本已经不见了，怎么办？

Git提供了一个命令git reflog用来记录你的每一次命令：

```cpp
$ git reflog
```

然后找到新版本的commit ID，再使用git reset --hard xxxxxx(即commit ID）回到最新版本。

```cpp
git reset --hard xxxxxx(即commit ID）
```

## 工作区和暂存区

前面讲了我们把文件往Git版本库里添加的时候，是分两步执行的：

第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；

第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。

你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

## 撤销修改

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

## 删除文件

现在有两个选择，一是确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit：

```cpp
$ git rm test.txt
$ git commit -m "remove test.txt"
```

另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：

```cpp
$ git checkout -- test.txt
```

git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

## 添加远程库

**1、上github新建仓库并且复制URL**

**2、为了建立与远程仓库的关联，在本地仓库下运行以下命令：**

```cpp
$ git remote add 自定义的远程库名字 仓库的URL
```

如下例：

```cpp
$ git remote add origin https://github.com/xxx/yyy.git
```

git默认远程库叫origin，也可以改成别的。

如果要**删除**已建立的远程库origin，可使用如下命令：

```cpp
$ git remote rm origin
```

**3、第一次把本地库内容推送到远程库**

使用如下命令把本地内容推送到origin远程库
```cpp
$ git push -u origin master
```

把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样。

**4、推送最新修改到远程库**

从现在起，只要本地作了提交，就可以通过命令：

```cpp
$ git push origin master
```

把本地master分支的最新修改推送至GitHub。

完整格式为：

```cpp
git push <远程主机名> <远程分支名>:<本地分支名>
```



**小结：**

要关联一个远程库，使用命令git remote add origin https://github.com/xxx/yyy.git；

关联后，使用命令git push -u origin master第一次推送master分支的所有内容；

此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；

分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，真是太方便了！


## 克隆和拉取
在本地没有版本库的时候，从远程服务器克隆整个版本库到本地，是一个本地从无到有的过程。

如下：

```cpp
git clone  远程仓库的URL
```
git pull的作用是从一个仓库或者本地的分支拉取并且整合代码。

完整格式为：

```cpp
git pull <远程主机名> <远程分支名>:<本地分支名>
```


## 创建与合并分支

我们创建dev分支，然后切换到dev分支：

```cpp
$ git checkout -b dev
```

git checkout命令加上-b参数表示创建并切换，相当于以下两条命令：

```cpp
$ git branch dev
$ git checkout dev
```

然后，用git branch命令查看当前分支：

```cpp
$ git branch
```

git branch命令会列出所有分支，当前分支前面会标一个*号。

然后，我们就可以在dev分支上正常提交，比如对readme.txt做个修改，加上一行：Creating a new branch is quick.  

然后提交：

```cpp
$ git add readme.txt 
$ git commit -m "branch test"
```

现在，dev分支的工作完成，我们就可以切换回master分支：

```cpp
$ git checkout master
```

切换回master分支后，再查看一个readme.txt文件，刚才添加的内容不见了！因为那个提交是在dev分支上，而master分支此刻的提交点并没有变：

现在，我们把dev分支的工作成果合并到master分支上：

```cpp
$ git merge dev
```

git merge命令用于合并指定分支到当前分支。合并后，再查看readme.txt的内容，就可以看到，和dev分支的最新提交是完全一样的。

注意到上面的Fast-forward信息，Git告诉我们，这次合并是“快进模式”，也就是直接把master指向dev的当前提交，所以合并速度非常快。

当然，也不是每次合并都能Fast-forward，我们后面会讲其他方式的合并。

合并完成后，就可以放心地删除dev分支了：

```cpp
$ git branch -d dev
```

删除后，查看branch，就只剩下master分支了：

```cpp
$ git branch
```

因为创建、合并和删除分支非常快，所以Git鼓励你使用分支完成某个任务，合并后再删掉分支，这和直接在master分支上工作效果是一样的，但过程更安全。

我们注意到切换分支使用git checkout <branch>，而前面讲过的撤销修改则是git checkout -- <file>，同一个命令，有两种作用，确实有点令人迷惑。

实际上，切换分支这个动作，用switch更科学。因此，最新版本的Git提供了新的git switch命令来切换分支：

创建并切换到新的dev分支，可以使用：

```cpp
$ git switch -c dev
```

直接切换到已有的master分支，可以使用：

```cpp
$ git switch master
```

使用新的git switch命令，比git checkout要更容易理解。


**小结**

Git鼓励大量使用分支：

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>或者git switch <name>

创建+切换分支：git checkout -b <name>或者git switch -c <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>

## 分支管理策略

通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。

如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。

准备合并dev分支，请注意--no-ff参数，表示禁用Fast forward：

```cpp
$ git merge --no-ff -m "merge with no-ff" dev
```

因为这种合并方法要创建一个新的commit，所以要加上-m参数，把commit描述写进去。

合并后，我们用下方命令看看分支历史：

```cpp
$ git log --graph --pretty=oneline --abbrev-commit

运行结果为：
*   e1e9c68 (HEAD -> master) merge with no-ff
|\  
| * f52c633 (dev) add merge
|/  
*   cf810e4 conflict fixed

```

**小结**

合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。


## git rebase与git merge区别

	Merge会自动根据两个分支的共同祖先和两个分支的最新提交 进行一个三方合并，然后将合并中修改的内容生成一个新的 commit，
	即merge合并两个分支并生成一个新的提交,并且仍然后保存原来分支的commit记录

	Rebase会从两个分支的共同祖先开始提取当前分支上的修改，然后将当前分支上的所有修改合并到目标分支的最新提交后面，
	如果提取的修改有多个，那git将依次应用到最新的提交后面。Rebase后只剩下一个分支的commit记录
 - [git rebase 与 git merge 取舍](https://blog.csdn.net/tang_yi_/article/details/105332094)
 - [Git分支Rebase详解](https://blog.csdn.net/endlu/article/details/51605861)
## git merge时发生冲突
 - [git merge如何判定冲突](https://blog.csdn.net/metheir/article/details/81808766?ops_request_misc=%25257B%252522request%25255Fid%252522%25253A%252522160964746716780262062565%252522%25252C%252522scm%252522%25253A%25252220140713.130102334..%252522%25257D&request_id=160964746716780262062565&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-81808766.pc_search_result_no_baidu_js&utm_term=git%20merge%E4%BB%80%E4%B9%88%E6%97%B6%E5%80%99%E4%BC%9A%E5%86%B2%E7%AA%81)

		git merge的冲突判定机制如下：先寻找两个commit的公共祖先，比较同一个文件分别在ours和theirs下对于公共祖先的差异，
		然后合并这两组差异。如果双方同时修改了一处地方且修改内容不同，就判定为合并冲突，依次输出双方修改的内容。

 - 处理merge冲突：
 	
 		先用git diff查看哪里不同，然后手动修改不同的文件，将文件修改为其中的一个版本，保存并git add、git commit即可。

 - 处理rebase冲突：
		
		先用git diff查看哪里不同，然后手动修改不同的文件，将文件修改为其中的一个版本，保存并git add、git base --continue即可。


## git pull与git fetch

 - [详解git pull和git fetch的区别：](https://blog.csdn.net/weixin_41975655/article/details/82887273)

	
 - [git fetch 和git pull 的差别](https://blog.csdn.net/qq_35014708/article/details/93062231)
## checkout、reset、rm
 - [git add、git checkout、git commit、git reset命令](https://blog.csdn.net/fxkcsdn/article/details/90410743)

		git reset --mixed HEAD 使用最近一次提交来覆盖暂存区
		git reset --hard HEAD 使用最近一次提交来覆盖暂存区和工作区
		git checkout  xxx	撤销工作区的xxx文件的修改，使之与暂存区一致
		
 - [移除文件----git rm命令的使用](https://blog.csdn.net/qq_42780289/article/details/98353792)

		git rm xxx 把xxx文件从暂存区和工作区删除
		git rm --cached 把xxx文件从暂存区删除
 - [git rm 与 git rm --cached](https://blog.csdn.net/dldl1718/article/details/88043850)
