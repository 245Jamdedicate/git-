安装好git之后可以通过在当前目录下执行git init 建立版本库

 

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps1.jpg)

Git 是版本库信息

Readme.txt代表了你的代码信息

 

git  add ./readme.txt(添加指定文件)  

git  add ./  （添加当前目录下的所有文件）

git commit -m  “提交功能说明”

如果没有进行 git  add 操作那么此时可以通过git status 指令查看当前代码提交的状况，如下图

表示代码只是被modified了，红色表示只是别修改但是没有被保存到版本库中

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps2.jpg)

执行 git  add ./readme.txt操作后，再次执行git status 如下

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps3.jpg)

执行了git commit -m  “提交功能说明”操作后：

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps4.jpg)

再次用 git  status 查看状态

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps5.jpg)

发现此时modified消失了这就代表你已经成功的向版本库中提交了

git log 查看历史提交日志

git log --oneline  逐条查看提交日志

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps6.jpg) 

Head相当于一个指针，指向你所有提交过的版本号

箭头所指的是当前head指向的版本号（就是最新的版本号）

 git reset --hard head~1 是指向版本一的命令（注意版本号是从0开始的、当前版本是0号、从上到下）

利用git reset --hard head~1 如果在版本好比较少的情况还是可以的，但是如果有100个版本，你还要一个个去数吗？当然不是

我们发现在我们提交的版本说明前面有一串字符串，这也是我们版本的唯一标识

我们可以利用git reset --hard 版本号

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps7.jpg)

执行 git reset --hard 182616a操作后

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps8.jpg)

 

 

如果我们回退到了第一个版本

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps9.jpg)

此时执行 git log --oneline  逐条查看提交日志发现日志只是显示该版本以前的日志

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps10.jpg) 

此时有一个神奇的命令出来啦

git  reflog  （这个命令相当于你的切换版本操作记录，可以看到你所有的版本号，额和网页历史记录一样。）

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps11.jpg) 

（commit：对应的就是对应的以前的提交记录）

这是你又可以通过前面的字符串标识来巡找你的版本号啦

***\*分支：\****

背景

如果你写的代码不想被其他人看到，可以提交到分支上。（我们上面的提交都是在master上提交的也就是主分支，你提交后别人就可以用了，但是如果的功能没有完成岂不是尴尬了），可以通过创建私人仓库，然后在合并的master上。

创建分支：

git branch “分支名字”

查看分支：

git branch        //////其中*号表示当前我们所在的分支

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps12.jpg)

切换的dev分支

git checkout dev

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps13.jpg) 

接下来你就可以通过和master分支一样的操作：

git  add ./  （添加当前目录下的所有文件）

git commit -m  “提交功能说明”

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps14.jpg)

此时只不过所有的功能是在dev分支上提交的，如果我们想合并到master分支上。

首先切换的master上查看日志

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps15.jpg) 

在master下执行merge操作：

git merge dev 

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps16.jpg)

此时发现我们的dev分支已经和master主分支合并了。

删除分支：

在主分支下：git branch -d dev

注：如果你在同一个修改通过dev向master提交了一次，假如你忘了提交了，你又通过master做了一次相同修改的提交，此时就会出现如下图：

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps17.jpg)

![img](file:///C:\Users\Administrator\AppData\Local\Temp\ksohtml6376\wps18.jpg)

此时就只能通过手动修改了，删除、保存、然后add、comit就行啦

\#####

Github 不是git，只不过是一个网站允许别人上传代码。

把自己的代码提交到githuab上去

git push 地址 master

git push https://github.com/245Jamdedicate/git-.git master

pull从github上往下拉代码（首先本地要初始化一个仓库）

git pull https://github.com/245Jamdedicate/git-.git master

Clone  从github上往下拉代码（首先本地要初始化一个仓库）

从github上往下拉代码（不需要本地要初始化一个仓库）

//会得到远程仓库相同的数据，如果多次执行会覆盖本地的内容，一般用pull

 

ssh方式：

生成公钥秘

ssh-keygen -t rsa -C ["xiaoming@qq.com"](mailto:\)

git push git@github.com:账户名/git2.git master

 

在提交的时候先pull在push

这样做的优点是让错误产生在本地而不是服务器上避免了服务器上出现错误不容易修改。

通过git remote add orign  [git@github.com:账户名/git2.git](mailto:git@github.com:账户名/git2.git) 设置地址的局部变量

 

通过git push orign  -u  master（加上-u之后使得服务器端的master分支和本地master分支相互关联）直接可以使用git push操作直接就可以push到服务器端，pull同理。