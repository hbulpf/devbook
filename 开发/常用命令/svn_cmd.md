# svn 常用命令
1. 添加
	```
	svn add . --no-ignore --force #递归目录下所有文件
	```
	
1. 添加文件并提交
	```
	svn add test.cpp
	svn ci -m "add test" test.cpp
	```

1. 删除文件并提交(注意，将会删除远程库的文件和本地文件)
	```
	svn delete test.cpp
	svn ci -m "svn test.cpp is deleted"
	svn delete --keep-local [path] #只从svn中忽略，而不删除文件
	```
1. 忽略
	```
	svn propset svn:ignore *.class . #忽略当前文件夹中*.class 
	svn propset svn:ignore bin . #忽略当前文件夹中bin文件夹
	svn propset svn:ignore -R *.class . #-R 递归忽略当前文件夹中bin文件夹
	```
> svn通过属性来判断如何处理仓库中的文件。其中有一个属性便是svn：ignore。你可以使用 svn propset 来设置svn：ignore在单独的目录。你可以给svn：ignore设置一个值，文件名或者是表达式。

1. 全局忽略.svnignore
	```
	svn propset svn:ignore -R -F .svnignore .
	```
1. 取消,svn add后，这个提交的数据又不需要了,不受SVN 版本控制
	```
	svn revert testcase/perday.php
	```
	- 递归取消
	```
	svn revert --depth=infinity .
	```

1. 查看状态
	```
	svn status
	svn status --no-ignore
	```
1. svn 批量删除
	```
	svn status|grep ! |awk '{print $2}'|xargs svn del
	```

1. svn 批量添加 
	- 方法1
	```
	svn status |grep '^\?' |tr '^\?' ' ' |sed 's/[ ]*//' | sed 's/[ ]/\\ /g' |xargs svn add
	```
	- 方法2
	```
	svn st |awk '{if ( $1 == "?") { print $2}}' |xargs svn add
	```