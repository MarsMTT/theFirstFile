## 本地库

### 文件查看

- 进入文件夹

==cd  weChat==

- 路径回退

==cd ../==







- 查看当前文件夹的所有内容

==ll==

![image-20200624181208044](D:\Tools\TyporaPIC\image-20200624181208044.png)





- 查看当前文件夹的隐藏内容

==ls-la==

![image-20200624181326096](D:\Tools\TyporaPIC\image-20200624181326096.png)





- 查看当前文件夹的特定内容(隐藏的也可查看)

==ll .git/==

![image-20200624181457338](D:\Tools\TyporaPIC\image-20200624181457338.png)







### 初始化



- 本地库初始化，先进入相关文件夹，然后

==git init==

![image-20200624181030184](D:\Tools\TyporaPIC\image-20200624181030184.png)





- 配置本地name和email

==git config user.name MarsMTT==

==git config user.email 869823401@qq.com==

![image-20200624181725161](D:\Tools\TyporaPIC\image-20200624181725161.png)



- 查看配置信息

==cat .git/config==

![image-20200624181834373](D:\Tools\TyporaPIC\image-20200624181834373.png)









- 配置系统name和email（在本地的基础上加--global）

![image-20200624182314324](D:\Tools\TyporaPIC\image-20200624182314324.png)



- 查看系统配置的信息（需要进入到c盘用户文件夹）

![image-20200624183212595](D:\Tools\TyporaPIC\image-20200624183212595.png)









### 添加提交命令



- 状态查看

==git status==

![image-20200624223538149](D:\Tools\TyporaPIC\image-20200624223538149.png)





- 添加操作

==git add [file name]==

![image-20200624223638628](D:\Tools\TyporaPIC\image-20200624223638628.png)



- 提交命令

==git commit  -m  "注释"  [file name]==

![image-20200624223714597](D:\Tools\TyporaPIC\image-20200624223714597.png)









### 查看历史记录



- 查看最完整记录

==git log==

![image-20200624224047535](D:\Tools\TyporaPIC\image-20200624224047535.png)



- 查看略微简洁的记录

==git log --pretty=oneline==

![image-20200624230818528](D:\Tools\TyporaPIC\image-20200624230818528.png)





- 查看超级简洁的记录

==git log --oneline==

![image-20200624230927993](D:\Tools\TyporaPIC\image-20200624230927993.png)





- 比oneline多了到当前版本需要的步数的记录

==git reflog==

![image-20200624231103617](D:\Tools\TyporaPIC\image-20200624231103617.png)









### 前进后退版本



- 基于索引值操作[推荐]

==git reset --hard [索引值]==

（推荐使用 ==git reflog==）

![image-20200624232632817](D:\Tools\TyporaPIC\image-20200624232632817.png)





- 使用 ^ 符号，只能后退，找以前的版本

==git reset --hard HEAD^==  (可以用多个^符号)

(建议使用==git log --oneline==)

![image-20200624233057921](D:\Tools\TyporaPIC\image-20200624233057921.png)





- 使用 ~ 符号，只能后退

==git reset --hard HEAD~n==  （n表示回退的步数）

![image-20200624233542484](D:\Tools\TyporaPIC\image-20200624233542484.png)





- hard--soft--mixed 参数对比

soft参数：仅仅修改本地库的HEAD指针（移动后用==git status==查看状态，文件变为绿色，是因为本地库移动，与缓存区无法对应）

mixed参数：修改本地库的指针+重置缓存区（移动后用==git status==查看状态，文件变为红色，是因为缓存区移动，与工作区无法对应）

hard参数：修改本地库的指针+重置缓存区+重置工作区







### 文件删除及找回相关操作

- 文件删除

==rm [文件名]==

![](D:\Tools\TyporaPIC\image-20200624235416923.png)





- 删除的一套操作，也是需要==add==和==commit==

![image-20200624235609476](D:\Tools\TyporaPIC\image-20200624235609476.png)





- 找回操作（指的是本地库有记录的找回，其实就是版本回退）

![image-20200625000145137](D:\Tools\TyporaPIC\image-20200625000145137.png)





- rm操作添加到缓存区，怎么找回

原因：由于本地库还没有变，HEAD指针仍然指向原来的commit，所以可以直接用==git reset --hard HEAD==返回

![image-20200625000828750](D:\Tools\TyporaPIC\image-20200625000828750.png)







- 总结：只要本地库有commit的提交记录，啥都可以找回











### 文件比较



- 第一种

==git diff [文件名]==

说明：将工作区的文件与缓存区的文件比较

![image-20200625102151002](D:\Tools\TyporaPIC\image-20200625102151002.png)

(vim编辑后，工作区改变，缓存区依然是老版本，此方法比较工作区和缓存区的差异，add之后，缓存区变为新版本，git diff就无法找到差异)







- 第二种

==git diff [本地库中历史版本] [文件名]==

说明：将工作区和缓存区的文件进行比较

![image-20200625102400288](D:\Tools\TyporaPIC\image-20200625102400288.png)

（此时还没有commit，所以存在different）



- 第三种

   ==git diff==        ==git diff HEAD==

   说明：如果不加文件名，可以比较所有的变化

![image-20200625102808775](D:\Tools\TyporaPIC\image-20200625102808775.png)















### 分支



- 什么是分支？？？

答：在版本控制的过程中，使用多条线，同时推进多个任务

![image-20200625103723340](D:\Tools\TyporaPIC\image-20200625103723340.png)

（第一次注册后，操作一直在master上）

（分支出来后，每个分支的操作互不影响，若开发失败只需要删除分支）



- 合并回主干

![image-20200625104154897](D:\Tools\TyporaPIC\image-20200625104154897.png)



#### 创建查看切换分支



- 创建分支

==git branch [分支名]==

![image-20200625104704958](D:\Tools\TyporaPIC\image-20200625104704958.png)





- 查看分支

==git branch -v==

![image-20200625104910899](D:\Tools\TyporaPIC\image-20200625104910899.png)





- 切换分支

==git checkout [分支名]==

![image-20200625104942814](D:\Tools\TyporaPIC\image-20200625104942814.png)



- 小测验

当我对hot_fix分支中的good1.txt进行修改后

![image-20200625105434431](D:\Tools\TyporaPIC\image-20200625105434431.png)

（查看两个分支的进度，不相同）





#### 合并分支

1. 切换到接受修改的分支  ==git checkout [分支名]==
2. 执行merge命令   ==git merge [分支名]==

![image-20200625111051836](D:\Tools\TyporaPIC\image-20200625111051836.png)







#### 合并冲突

说明：当两个分支，都在同一个位置进行了修改，合并时会产生冲突，需自己来决定，使用哪个



![image-20200625112125489](D:\Tools\TyporaPIC\image-20200625112125489.png)

（出现自动合并失败的情况）



- 分支冲突的表现

![image-20200625112337443](D:\Tools\TyporaPIC\image-20200625112337443.png)



- 解决方法

进入vim编辑器，自行修改，之后add，commit（注意commit不需要加文件名，但是日志还是要的）

![image-20200625130614998](D:\Tools\TyporaPIC\image-20200625130614998.png)

















## 远程库





### 本地库创建远程库地址别名

- 创建别名

==git remote add [别名]  [地址]==

![image-20200625145907878](D:\Tools\TyporaPIC\image-20200625145907878.png)



- 查看别名及地址

==git remote -v==

![image-20200625145951545](D:\Tools\TyporaPIC\image-20200625145951545.png)







### 推送操作

==git push [地址或者别名] [分支名]==

![image-20200625150422729](D:\Tools\TyporaPIC\image-20200625150422729.png)









### 克隆操作

==git clone [远程地址]==

![image-20200625153442477](D:\Tools\TyporaPIC\image-20200625153442477.png)

有如下三个效果

1. 把远程库下载到本地库（一个文件夹）
2. 创建origin远程地址别名（就是远程库中设置的）
3. 直接初始化本地库，本地库在克隆前，不需要初始化，git init不要的











### 邀请成员加入

![image-20200625154126580](D:\Tools\TyporaPIC\image-20200625154126580.png)

![image-20200625154152865](D:\Tools\TyporaPIC\image-20200625154152865.png)

- 此时输入需要邀请成员的用户名，然后复制链接给成员，那个成员跳转到链接即可（其实成员的邮箱应该也会收到）







### 远程库的拉取

- pull操作由fetch和merge组成



1. 以下是分开的操作

- 拉取

==git fetch [远程库地址别名] [远程库分支]==

![image-20200625162621974](D:\Tools\TyporaPIC\image-20200625162621974.png)

(fetch操作之后，本地的文件不会变)

如果想查看fetch下来的内容，需要将分支切换到origin下的master

![image-20200625162838455](D:\Tools\TyporaPIC\image-20200625162838455.png)



- 进行merge操作之前，先回到本地需要合并的库，然后进行merge

==git merge [远程库别名/远程库分支名]==





2. pull操作一步完成，抓取&合并

==git pull [远程库别名] [远程库分支名]==





### 解决冲突

1. 如果不是基于GitHub远程库的最新版本所做的修改，不能push，必须先pull最新版本下来修改
2. pull下来后，如果进入冲突状态，则按照“分支冲突”解决（commit的时候不需要分支名，可以有日志）













### SSH免密登录

![image-20200625170237075](D:\Tools\TyporaPIC\image-20200625170237075.png)

![image-20200625170412955](D:\Tools\TyporaPIC\image-20200625170412955.png)

![image-20200625170529840](D:\Tools\TyporaPIC\image-20200625170529840.png)