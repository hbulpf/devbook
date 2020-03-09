# SRE面试题
1. 实现WEB流量负载均衡的方式有哪些？描述其工作原理及优缺点
1. 查看redhat或centos系统版本的命令
```
cat /proc/version
lsb_release
cat /etc/os-release
cat /etc/redhat-release
```
1. 查看 Linux 启动信息的命令
```
dmesg | more
```
1. 查看 CPU 型号的命令
```
cat /proc/cpuinfo | grep 'name' | cut -f2 -d : |uniq -c
```
输出了 CPU 型号及其 core 数
```
2  Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz
```
1. 查看 CPU Core 数
```
cat /proc/cpuinfo | grep 'cores' | uniq
```
1. 查看进程及其CPU使用率，并查看进程的目录

1. 根据端口号查找进程启动bin
 - 方法1： 使用 `netstat -apn | grep {端口号}` 查找到 pid , 使用 `ps -aux | grep {pid}`  启动的cmd , cmd 里有启动的bin文件 【如果使用的是相对路径启动的，则使用方法2】
 - 方法2： 使用 `netstat -apn | grep {端口号}` 查找到 pid , 使用 'll /proc/{pid}' 查看 `exe` 文件对应的软链接即为启动的bin文件

1. 如何修改 kernel 参数，修改 kernel 参数有什么作用，请举一例

1. 如何分析 nginx 日志，写出过程及使用工具

1. 讲出网线连线顺序
```
568A: 白绿 、绿 、白橙 、蓝 、白蓝、橙 、白棕、棕
568B: 白橙 、橙 、白绿 、蓝 、白蓝、绿 、白棕、棕 【白程程把驴拦下来，白拦了驴，等到胡子白淙淙】
```
1.  

1. 编写一个简单的 nginx 启动脚本，放在 /etc/init.d 下面(nginx目录，nginx配置文件，pid文件自定义即可)
1.  写出接触过的所有监控工具，描述其优缺点

1. 有用户反映网站访问很慢，请给出排查过程和解决办法，需要哪些帮助？

1. 描述用户从输入 http://www.baidu.com 到最后页面显示的过程

1. 描述用户访问 http://www.baidu.com 缓存的使用

1. 


----------------------------------------------------------------------------------------
[`@RunAtWorld的csdn`](https://blog.csdn.net/RunAtWorld)    [`@RunAtWorld的github`](https://github.com/RunAtWorld)

