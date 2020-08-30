# Git常用操作
```
git help #查看git帮助
```

### 配置账户
```
git config --global user.name "lipengfei"	#配置用户名   
git config --global user.email "goodlpf00@gmail.com"	#配置电子邮箱   
ssh-keygen -t rsa -C "goodlpf00@gmail.com"	#生成公钥和私钥对  
cat ~/.ssh/id_rsa.pub #查看公钥信息
ssh git@bitbucket.org	#测试ssh的密钥对  #在linux下，如果测试不通过，键入命令: add-ssh ~/.ssh/id_rsa   
```
### 从本地仓库创建远程仓库
```
git push --set-upstream ssh://git@github.com:RunAtWorld/$(git rev-parse --show-toplevel | xargs basename).git $(git rev-parse --abbrev-ref HEAD)
```

### 克隆仓库
```
git clone git@github.com:RunAtWorld/quietalk.git	#从远程克隆一个仓库   
```

### 拉取操作
```
git fetch origin  #从远程仓库 origin 下载所有变化数据,但是不放到工作区  
git merge origin/dev #将远程仓库中的dev分支与当前本地分支合并  
git pull <远程主机名> <远程分支名>:<本地分支名>  #相当于git fetch origin 和git merge origin/dev 两条命令的合并
git pull origin dev:master #拉取远程dev分支与本地master分支合并
```

### 提交文件
常用的操作
```
git add .  #添加当前文件夹下所有文件到下一次提交,并被跟踪   
git commit -m "abc" #带信息"abc"提交一次变化到本地仓库   
git commit -n       #不带信息提交
git commit --no-commit   #不带信息提交
git push    #提交本地文件到远程仓库
```

更多操作
```
git add 1.txt  #添加1.txt到下一次提交,并被跟踪   
git add .  #添加当前文件夹下所有文件到下一次提交,并被跟踪   
git add *.txt #添加所有txt文件到下一次提交,并被跟踪   
git commit -m "abc"	#带信息提交一次变化到本地仓库   
git commit -am "abc"	#带信息提交所有修改的文件变化到本地仓库，可以省略 git add 操作 
git commit --amend	#修改上一次提交   
```

### 查看状态与日志
1. 查看状态
```
git status #显示当前git的状态   
git remote -v   #列出当前配置的远程库  
```
2. 查看日志
```
git log #查看git日志 
git log --after="2018-05-21 00:00:00" --before="2018-07-25 23:59:59" # 查看某个时间段日志
git log --oneline --since ="2018-07-19 00:00:00" --until=="2018-11-19 23:00:00" #单行查看某段时间的日志
git log --graph --oneline #点线图查看日志 
git log --no-merges origin/dev  #列出远程dev分支没有合并前的变化  
```

### 分支
1. 创建分支
```
git branch	#查看当前分支   
git branch dev	#创建dev分支   
git checkout dev	#切换到一个分支dev 
git checkout -b dev	#创建并切换到分支dev
git branch -m old_name new_name #本地分支重命名
```

1. 删除分支
```
git branch -d branch4	#删除一个本地分支branch4  
git push origin --delete branch4  #删除远程分支branch4
```

1. 合并分支
```
git merge branch4 #将branch4分支与当前分支合并
```

1. 查看分支
```
git branch -r   #列出远程分支
git branch -v   #列出本地分支
git branch -a   #列出本地和远程所有分支
git branch -vv   #列出本地分支与远程分支的对应关系
```

1. 与远程分支建立联系
```
git checkout -b dev_loacal --track origin/dev   #新建一个本地dev_loacal分支并与远程dev分支关联  
git branch --set-upstream-to dev_loacal origin/dev  #将本地分支dev_loacal与远程的dev建立联系  
git branch --set-upstream-to=origin/dev dev_loacal #将本地分支dev_loacal与远程的dev建立联系  
```

1. [储存当前状态](https://git-scm.com/book/zh/v1/Git-%E5%B7%A5%E5%85%B7-%E5%82%A8%E8%97%8F%EF%BC%88Stashing%EF%BC%89)
```
git stash #储藏当前状态，切换到其他分支  
git stash save stash_1 #储存当前状态，并命名为stash_1
git stash list	#查看储藏状态的列表  
git stash apply stash_1	#回到原来某个工作状态stash_1，恢复之前的工作状态  
git stash drop stash_1 #删除stash_1储藏
git stash pop stash_1 #弹出stash_1,回到原来某个工作状态stash_1,不删除stash_1
git stash branch testchanges #从储藏中创建分支testchanges,检出你储藏工作时的所处的提交，重新应用你的工作，如果成功，将会丢弃储藏
git stash clear # 清空所有储藏
```

### 合并: merge/rebase

1. 变基/rebase：

```
git rebase master
```
以上在 dev 分支执行变基，是将dev分支的commit暂存，将 master 分支的commit应用后再将dev分支暂存的commit拿出来应用在dev分支。为了让master分支也获得最新的 commit. 将master分支快进到dev当前commit即可。

1. 合并/merge：
```
git merge dev
```
这和 merge 有些不同，merge是将另一个分支新的commit直接放在当前分支的commit之后，rebase是将当前分支的commit暂存，将另一分支的commit应用后再将当前分支暂存的commit拿出来应用在当前分支，因而保持了分支图关系的清晰。

### 远程
#### 远程分支
```
git remote show origin  #列出远程仓库 origin 的信息  
git remote rename origin origin1    #重命名远程仓库为 origin1  
git remote rm origin  #删除远程仓库origin
```

#### 远程推送
```
git push origin dev_local:dev  #推送本地分支dev_local到 origin 远程仓库(新建)dev分支  
git push --set-upstream origin dev_local:dev  #推送并设置本地分支dev_local到 origin 远程仓库(新建)dev分支  
git push origin :experimental #删除远程的 experimental 分支
git push origin [name] 创建远程分支(本地分支push到远程)
git branch --set-upstream-to=origin/dev dev_loacal #将本地分支dev_loacal与远程的dev建立联系  
```

### Tag
>创建一个tag来指向软件开发中的一个关键时期，比如版本号更新的时候可以建一个"v2.0"、"v3.1"之类的标签，这样在以后回顾的时候会比较方便。tag的使用很简单，主要操作有：查看tag、创建tag、验证tag以及共享tag。

#### Tag 本地操作
1. 查看tag
```
git tag   #查看tag,列出所有tag，按字母排序的，和创建时间没关系
git tag -l 'v1.4.2.*'  #查看指定版本的tag
git show v1.4  #显示tag信息
```

2. 创建tag
```
git tag v1.0  #创建轻量级tag，这样创建的tag没有附带其他信息
git tag -a v1.0 -m 'first version' #创建轻量级tag：这样创建的tag没有附带其他信息
```

4. 删除tag
```
git tag -d v1.0  #删除本地tag
```

5. 创建一个基于指定tag的分支
```
git checkout -b tset v0.1.0
```

#### Tag 远程操作
1. 创建 tag 后,tag不会上传github服务器, `git push` 在github网页上看不到tag,需要带 tag 推送
```
git push origin v1.0  #将v1.0的tag推到服务器
git push origin --tags   #将所有tag 一次全部push到github上
```

1. 查看远程tag
```
git show-ref
```

1. 删除远程tag
```
git push origin :refs/tags/v1.0.0  #删除github远端的指定tag
git push origin --delete v1.0.0 
```

### 重置仓库/丢弃修改
```
git checkout . #本地所有修改的。没有的提交的，都返回到原来的状态
git stash #把所有没有提交的修改暂存到stash里面。可用git stash pop回复。

git clean -df #返回到某个节点
git clean 参数
    -n 显示 将要 删除的 文件 和  目录
    -f 删除 文件
    -df 删除 文件 和 目录
#恢复到上一次提交前
git checkout . && git clean -xdf
```


###  本地仓库重置
```
git reset --mixed <指定版本HASH> #不删除工作空间改动代码，撤销commit，并且撤销git add . 操作
                               #这个是默认参数,git reset --mixed HEAD^ 和 git reset HEAD^ 效果是一样的。
git reset --soft <指定版本HASH> #不删除工作空间改动代码，撤销commit，不撤销git add .
git reset --hard <指定版本HASH> #删除工作空间改动代码，撤销commit，撤销git add . ，恢复到了上一次的commit状态

git reset --soft HEAD^  #撤销commit
git reset --soft HEAD~1 #撤销前1次commit
git reset --soft HEAD~2  #撤销前2次commit
```

### 撤销/回滚 revert 
#### 单个 commit 撤销
git revert 撤销某次操作，此次操作之前和之后的commit和history都会保留，并且把这次撤销，作为一次最新的提交。git revert提交一个新的版本，将revert的版本的内容再反向修改回去，版本会递增，不影响之前提交的内容.
```
git revert HEAD          #撤销前一次 commit
git revert HEAD^         #撤销前前一次 commit    
git revert commit_id  #（比如:fa042ce57ebbe5bb9c8db709f719cec2c58ee7ff）
```

#### 多个 commit 撤销
##### 连续

```
git revert -n commit_id_start..commit_id_end #提交撤回到commit_id_start的位置
```

##### 不连续
撤回到commit_id_1和commit_id_3的提交

```
git revert -n commit_id_1
git revert -n commit_id_3
```

#### 撤销 merge
由于 merge 是两个分支 多个commit 合并在一个 commit中，因此撤销 merge 需要告诉系统使用哪个 branch
```
git revert merge_commit_id -m 1
```
如果不用 `-m` 参数将会出现错误 `is a merge but no -m option was given`
这是因为revert的那个commit是一个merge commit，它有两个parent, Git不知道base是选哪个parent，就没法diff,所以你要显示告诉Git用哪一个parent。
一般来说，如果在 master 上 merge dev_branch, 那么parent 1 就是 master ，parent 2 就是 dev_branch

### 补丁/patch
> patch和cherry-pick的功能都是重用commit,功效几乎一样, 但是cherry-pick更为简单.

1. 生成patch文件:
```
git format-patch <old-commit-sha>...<new-commit-sha> -o <patch-file-dir>
```
如:
```
git format-patch 0f500e44965c2e1d3449c05...d37885d260bb228f0a8841d48b -o ~/temp_patch/
```

生成文件/Users/stone/temp_patch/0001-add-content-to-bb.c.patch
查看 `git log` 或 `git log -p` (有详细的更改内容)

```
git format-patch commit_id -N #表示生成对应id的commit
git format-patch commit_id #表示从某个id开始所有的commit
git format-patch commit_start...commit_end #表示从start到end
```

2. 测试patch文件:

检查patch文件
```
git apply --stat ~/temp_patch/0001-add-content-to-bb.c.patch
```

查看是否能应用成功
```
git apply --check ~/temp_patch/0001-add-content-to-bb.c.patch
```

3. 应用patch文件
```
git am -s < ~/temp_patch/0001-add-content-to-bb.c.patch
```

使用 `git apply`  一个patch 会直接把对应的changed修改到对应的文件上，需要重新进行一个commit进行添加，这样的操作会导致 patch 的commit丢失。
使用 `git am` 一个patch 会保留commit。**apply中有冲突时对应patch的commit是无法保留的。**

### cherry-pick/重演commit
基于release-2.0分支新建分支release-2.1, 并且到新创建的分支上
```
git checkout -b release-2.1 release-2.0
```

将dev-3.0分支上的某些commit在release-2.1分支上重演
```
git cherry-pick {dev-3.0分支的某些commit-hash}
```
如
```
git cherry-pick  
20c2f506d789bb9f041050dc2c1e954fa3fb6910 
2633961a16b0dda7b767b9264662223a2874dfa9 
5d5929eafd1b03fd4e7b6aa15a6c571fbcb3ceb4  
```
多个commit-hash使用空格分割, commit-hash最好按提交时间先后排列, 即最先提交的commit放在前面.

# Git各个状态之间转换指令总结   
![Git各个状态之间转换指令总结](imgs/1352126739_7909.jpg) <br>  
**工作区**：就是你在电脑里能看到的目录。<br>
**暂存区**：英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。<br>
**版本库**：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。<br>
<br>
在版本库中标记为 "index" 区域是暂存区（stage, index），标记为 "master" 的是 master 分支所代表的目录树。<br>
"HEAD" 实际是指向 master 分支的一个"游标"。图中出现 HEAD 的地方可以用 master 来替换。objects 标识的区域为 Git 的对象库，实际位于 ".git/objects" 目录下，里面包含了创建的各种对象及内容。<br>

- 当对工作区修改（或新增）的文件执行 `git add` 命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中，而该对象的ID被记录在暂存区的文件索引中。<br>
- 当执行提交操作 `git commit` 时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。<br>
- 当执行 `git reset HEAD` 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。<br>
- 当执行 `git rm --cached <file>` 命令时，会直接从暂存区删除文件，工作区则不做出改变。<br>
- 当执行 `git checkout .` 或者 `git checkout -- <file>` 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。<br>
- 当执行 `git checkout HEAD .` 或者 `git checkout HEAD <file>` 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。<br>

# Git 示例
### 1. git 切换远程分支<br>
git clone只能clone远程库的master分支，无法clone所有分支。
```
git clone http://myrepo.xxx.com/project/.git 
cd project
```
列出所有分支：
```
git branch -a 
```
>remotes/origin/dev  
>remotes/origin/release

checkout远程的dev分支，在本地起名为dev分支，并切换到本地的dev分支
```
git checkout -b dev origin/dev #checkout远程的dev分支，在本地起名为dev分支，并切换到本地的dev分支
```
切换回dev分支开始开发
```
git checkout dev  #切换回dev分支开始开发
```
将本地dev分支与远程dev分支建立关联
```
git branch --set-upstream-to=origin/dev dev 
git push --set-upstream origin dev_local:dev #本地分支dev_local推送到远程dev分支
```

新建本地分支，并推送为远程的新分支
```
git checkout -b dbg_lichen_star
git push origin dbg_lichen_star:dbg_lichen_star
```
### 2. 树形展示日志

```
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative
```

### 3. 彻底删除远程仓库所有文件
```
git clone git@github.com:ACCOUNT/REPO.wiki.git
cd REPO.wiki
git checkout --orphan empty
git rm --cached -r .
git commit --allow-empty -m 'wiki deleted'
git push origin empty:master --force
```

### 4. 如果commit注释写错了，只是想改一下注释，只需要：
```
git commit --amend
```

### gitignore 说明
```
#               表示此为注释,将被Git忽略
*.a             表示忽略所有 .a 结尾的文件
!lib.a          表示但lib.a除外
/TODO           表示仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/          表示忽略 build/目录下的所有文件，过滤整个build文件夹；
doc/*.txt       表示会忽略doc/notes.txt但不包括 doc/server/arch.txt
 
bin/:           表示忽略当前路径下的bin文件夹，该文件夹下的所有内容都会被忽略，不忽略 bin 文件
/bin:           表示忽略根目录下的bin文件
/*.c:           表示忽略cat.c，不忽略 build/cat.c
debug/*.obj:    表示忽略debug/io.obj，不忽略 debug/common/io.obj和tools/debug/io.obj
**/foo:         表示忽略/foo,a/foo,a/b/foo等
a/**/b:         表示忽略a/b, a/x/b,a/x/y/b等
!/bin/run.sh    表示不忽略bin目录下的run.sh文件
*.log:          表示忽略所有 .log 文件
config.php:     表示忽略当前路径的 config.php 文件
 
/mtk/           表示过滤整个文件夹
*.zip           表示过滤所有.zip文件
/mtk/do.c       表示过滤某个具体文件
```
# FAQ
#### 1. SSH生成id_rsa,id_rsa.pub后，连接服务器却报：`Agent admitted failure to sign using the key` 错误。  
解决：在当前用户下执行命令：
```
ssh-add
```
即可解决。

#### 2. 本地文件夹与远程库建立关联
```
git init .
git remote add origin git@github.com:RunAtWorld/ceph_manual.git  #与远程主机关联
git branch --set-upstream-to=origin/master master #建立本地master分支与远程master分支的关联
```

#### 3. 本地项目上传到git   
(1) 进入项目文件夹,通过命令 git init 把这个目录变成git可以管理的仓库
```
git init
```
(2) 把文件添加到版本库中
```
git add .
```
(3) 用命令 git commit告诉Git，把文件提交到仓库。引号内为提交说明
```
git commit -m 'first commit'
```
(4) 关联到远程库
```
git remote add origin 你的远程库地址
```
如
```
git remote add origin https://github.com/cade8800/ionic-demo.git
```
(5) 获取远程库与本地同步合并（如果远程库不为空必须做这一步，否则后面的提交会失败）
```
git pull --rebase origin master
```
(6) 把本地库的内容推送到远程，使用 git push命令，实际上是把当前分支master推送到远程。执行此命令后会要求输入用户名、密码，验证通过后即开始上传。
```
git push -u origin master
```

#### 4. 上传ssh-key后仍须输入密码
这通常发生使用https方式克隆仓库的时候，解决的方法是使用ssh方式克隆仓库。
如果已经用https方式克隆了仓库，就不必删除仓库重新克隆，只需将 .git/config文件中的
```
 url = https://github.com/Name/project.git
```
一行改为
```
 url = git@github.com:Name/project.git
```

# 参考
1. [易百git教程：https://www.yiibai.com/git/git_basic_concepts.html](https://www.yiibai.com/git/git_basic_concepts.html)
2. [git官方教程：https://git-scm.com/book/zh/v2/](https://git-scm.com/book/zh/v2/)
3. [git菜鸟教程:http://www.runoob.com/git/git-tutorial.html](http://www.runoob.com/git/git-tutorial.html)
4. [git简明指南:http://rogerdudler.github.io/git-guide/index.zh.html](http://rogerdudler.github.io/git-guide/index.zh.html)
