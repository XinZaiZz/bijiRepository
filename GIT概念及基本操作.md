### GIT概念：

Git是一个免费的，开源的分布式版本控制系统，可以快速高效地处理小型或大型项目

### 什么是版本控制：

版本控制是一种记录一个或若干个文件内容变化，以便将来查询特定版本修订情况的系统。

### 为什么要使用版本控制：

有了版本控制可以将某个文件回溯到之前的状态，甚至将整个项目都回退到某个时间点的状态；就算对整个项目修改，也可以轻松恢复到原来的样子；但额外增加的工作量却微乎其微，可以比较文件细节变化，查到最后是谁修改了哪个地方，从而找出问题原因和功能缺陷。

#### 版本控制系统分类：

##### 集中化的版本控制系统：

集中化版本控制系统如CVS,SVN,Perforce等，都有一个单一的，集中管理的服务器，保存所有版本，每个人可以在一定程度上看到其他人在做什么，管理员可以掌握每个开发者的权限，并且集中管理，维护起来更加轻松。

但如果服务器出现问题，所有项目都不能提交和更新，不能更好的协调工作。

存放的是最新版本与历史版本之间的差异，对于想要回滚操作非常麻烦。

##### 分布式版本控制系统：

由于集中化版本控制的缺点，出现了分布式版本控制系统。如Git，Bitkeeper等，客户端并不是只提取最新版本的文件快照，而是把代码仓库完整的镜像下来。即git后直接下载所有历史版本，客户端就是服务器，服务器就相当于客户端。这样可以在同一个项目中和不同的工作组的人相互协作。

git存放的是最新版本和历史版本的索引，如果想要进行回滚操作非常简单。（极致的压缩算法和解压算法，比集中化版本控制大一点，但存了更多的内容）

### Git下载安装：

git下载地址：<[Git (git-scm.com)](https://git-scm.com/)>,安装时直接下一步，注意选择要将git集成到右键。

![image-20210720115736293](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720115736293.png)

### GIT基本使用：

####打开Git终端

点击右键可以使用GUI或者Bash方式进行git操作：

![image-20210720142658005](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720142658005.png)

一般是使用Git Bash Here：（控制台方式）

![image-20210720142754784](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720142754784.png)

#### git结构：

分为本地结构和远程结构，本地结构只提交到本地仓库，远程结构则要提交到代码托管平台中心。

![image-20210720143424076](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720143424076.png)

#### 团队内部协作：

![image-20210720144609942](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720144609942.png)

#### 跨团队合作：

![image-20210720144703793](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720144703793.png)

#### 代码托管中心：

代码托管中心的任务就是帮我们维护远程仓库，可以更好的进行垮团队协作。

局域网环境下：可以搭建GitLab服务器作为代码托管中心，GitLab可以自己搭建。

外网环境下：可以由github或gitee作为代码托管中心，github和gitee是现成的托管中心，不用自己去搭建。

#### 初始化本地仓库：

创建Git本地仓库文件夹：

![image-20210720145523731](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720145523731.png)

打开git终端：git bash here

`$ cd ~` 可直接进入用户主目录中

`$ git --version` 可以查看当前安装git版本：

![image-20210720145900494](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720145900494.png)

`$ clear` 进行清屏操作

设置签名：

设置用户名和邮箱：

`git config --global user.name "liaoyouxin"` git配置用户名

`git config --global user.email "liaodagege@outlook.com"`  配置邮箱

#####本地仓库的初始化：

`$ cd GitRepository` 定位进入全面创建的本地仓库文件夹：

![image-20210720150631818](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720150631818.png)

`$ git init` 创建空的本地仓库（生成.git隐藏文件夹）（`ll` 可以看到文件夹下的所有文件）：

![image-20210720150837025](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720150837025.png)

![image-20210720151115815](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720151115815.png)

添加文件add，提交问价commit

首先创建需要的文件：

![image-20210720151712318](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720151712318.png)

打开git终端：

输入`$ git add test.txt` 提交文件到缓存区：

![image-20210720151844095](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720151844095.png)

`$ git commit -m "这是提交的第一个test.txt文件" test.txt` 提交到本地仓库，其中`-m` 代表后面双引号的内容，即提交的注释：

![image-20210720152252276](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720152252276.png)

### 注意：文件只能在本地仓库文件夹中才能上传，即使放在本地仓库中的文件git也不进行管理，只有进行add和commit后git才进行管理。

git status 查看是暂存区还是工作区状态

![image-20210720153303692](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720153303692.png)

如果有未被管理的文件：

![image-20210720153654028](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720153654028.png)

如果只是add操作：

![image-20210720153823596](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720153823596.png)

可再次提交：

![image-20210720154543598](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720154543598.png)

如遇

```text
Another git process seems to be running in this repository, e.g.
an editor opened by 'git commit'. Please make sure all processes
are terminated then try again. If it still fails, a git process
may have crashed in this repository earlier:
remove the file manually to continue.
```

因为git在使用过程中遇到崩溃，部分被上锁资源没有被释放导致。所以需要在.git文件中删除以.lock结尾的文件后重新执行操作。

修改文件中内容后查看状态：

![image-20210720155137808](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720155137808.png)

需要重新add后commit:

![image-20210720155418969](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720155418969.png)

`$ git log` 可以查看提交日志（显示由近到远顺序）（如果日志太多会显示冒号，空格：下一页，B键：上一页，到尾页了显示end，end后点击Q键可退出）：

![image-20210720155701999](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720155701999.png)

![image-20210720160438414](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720160438414.png)

日志方式2：`$ git log --pretty=oneline` 一行上展示日志

![image-20210720160706455](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720160706455.png)

日志方式3：`$ git log --oneline` 更加简洁

![image-20210720160804536](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720160804536.png)

日志方式4：`$ git reflog` 多了HEAD@{数字} 数字表示当前回到该历史版本需要多少步：

![image-20210720161019772](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720161019772.png)

`$ git reset --hard b5fb6cc` reset用于回退（往前往后都可以）历史版本（后面的十六进制数为上面日志的十六进制数索引）：

![image-20210720161835187](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720161835187.png)

其中：

--hard参数：本地库指针移动的同时，重置暂存区，重置工作区（用的最多）。

--mixed参数：本地库指针移动的同时，重置暂存区，但是工作区不变。

--soft参数：本地库指针移动的同时，暂存区和工作区都不动。

新建一个demo.txt文件，并用add和commit提交本地库，

![image-20210720163124135](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720163124135.png)

`$ rm demo.txt` 删除工作区中demo.txt文件：

将这个删除操作同步到暂存区和本地库：再进行add和commit操作即可：

![image-20210720163441571](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720163441571.png)

查看日志：

![image-20210720163539645](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720163539645.png)

找回本地库中删除的文件，实际上就是将历史版本切换到删除文件之前版本即可。

如果想找回暂存区删除文件，也可用hard关键字回退版本。`$ git reset --hard HEAD`





#####比对工作区与暂存区：

在test.txt文件中修改：![image-20210720165112338](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720165112338.png)

用`$ git diff test.txt` 如果不加文件名，这比对所有文件

![image-20210720165314365](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720165314365.png)

##### 暂存区与本地库比较

`$ git diff HEAD test.txt` head可以用十六进制索引代替

![image-20210720165956390](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720165956390.png)



##### 分支：

一般一个独立的功需要开辟一个新的分支。

![image-20210720171030912](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720171030912.png)

分支的好处：多个分支可以并行开发，互不影响，提高开发效率，如果有一个分支功能开发失败，直接删除这个分支就可以了，不会对其他分支产生任何影响。

##### 创建一个分支：

在工作区中创建test4.txt并同步到本地库

`$ git branch -v`  查看分支，前面有个星号代表当前在对应分支

![image-20210720171646109](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720171646109.png)

创建一个新的分支：`$ git branch branch01`

![image-20210720171808446](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720171808446.png)

切换分支：`$ git checkout branch01` 

![image-20210720172018419](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720172018419.png)

#####如果对当前分支进行修改后提交，再切换到其他分支，其他分支本地库的内容也不会改变，只有当前的分支本地库内容会改变。

`$ cat test4.txt` 在当前分支下查看test4.txt中内容

![image-20210721102428954](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721102428954.png)

##### 将branch01合并到master中：

`$ git merge branch01` 进行合并，如果显示有`master|MERGING`则表示有冲突，处在合并状态中（master与branch01相同文件有重复冲突）

当出现冲突时需要内部商讨自行解决，存留哪一个版本。如果要解决，需再次commit且不能带文件名。

![image-20210721103141877](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721103141877.png)

##### 创建github远程仓库

![image-20210720173236440](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720173236440.png)

远程库地址比较长，每次复制很麻烦

可以在git本地将地址保存，通过别名：

`$ git remote -v` 查看是否本地库是否有别名：

![image-20210720173806414](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720173806414.png)

`$ git remote add origin https://github.com/XinZaiZz/GitRepository.git` 为本地库取别名为origin(别名可以按照自己需求取):

![image-20210720173953582](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720173953582.png)

#####推送本地仓库

`$ git push origin master` 将本地库推送到远程库的master分支中：

![image-20210720174930029](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720174930029.png)

##### 克隆远程仓库

`$ git clone https://github.com/XinZaiZz/GitRepository.git` 克隆远程仓库：

![image-20210720175437020](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720175437020.png)



`ssh-keygen -t rsa -C "liaodagege@outlook.com"`  生成密钥，三次回车确认默认值

![image-20210510125811654](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210510125811654.png)

`cat ~/.ssh/id_rsa.pub` 拿出密钥

在github添加密钥：

![image-20210720184626981](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720184626981.png)

![image-20210720184659088](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720184659088.png)

![image-20210720184833646](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210720184833646.png)

自此完成免密登陆

`ssh -T git@gitee.com` 测试是否配置成功

#### IDEA集成git

setting-->version control-->Git-->找到本地git安装路径-->apply

idea中创建本地仓库：

![image-20210721104304637](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721104304637.png)

![image-20210721104409094](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721104409094.png)



创建一个文件就会提示是否进行add操作：

![image-20210721104701323](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721104701323.png)

右键module先add 再commit:

![image-20210721105121479](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721105121479.png)





![image-20210721104954400](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721104954400.png)

未提交的数据前面有绿条显示：

![image-20210721105704519](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721105704519.png)



在idea建的本地库中拉取远程仓库：

`$ git pull https://github.com/XinZaiZz/GitRepository.git master --allow-unrelated-histories` 后面代表允许不相关历史记录。

拉取后用I键备注，在esc退出用:wq退出。

![image-20210721110845085](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721110845085.png)

`$ git push -u https://github.com/XinZaiZz/GitRepository.git master -f` 再次推送到远程仓库中

![image-20210721111924908](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721111924908.png)

在idea中推送：

![image-20210721111959634](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721111959634.png)

#### 一般在开发中，会先pull操作，再push操作！

idea进行克隆操作：

![image-20210721112543286](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721112543286.png)

推送中如果有冲突，则选择进行合并（merge）操作

![image-20210721113837090](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721113837090.png)

![image-20210721113909666](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721113909666.png)

![image-20210721113510386](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210721113510386.png)
