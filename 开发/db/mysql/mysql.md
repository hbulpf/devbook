mysql 知识总结
    - [mysql官方文档](https://dev.mysql.com/doc/refman/5.7/en/)

# 性能监控

# schema 与数据优化

## 字符集选择

尽量选择 `utf8mb4` , 不要用 `utf8`, utf8 对于某些字符会无法显示。

## 存储引擎的选择

## 适当的数据冗余

## 适当拆分

# 执行计划

explain select语句

# 通过索引进行优化

二叉树，红黑树，b树，b+树，BST， AVL，多叉树

## 索引基本知识

### 索引的用处

### 索引的优点

### 索引的分类

hash索引
组合索引
聚簇索引
覆盖索引
索引监控

### 面试名词

### 采用的数据结构

### 索引的匹配方式

## 简单案例

# 查询优化

## 查询慢的原因


# 分区表


# 服务器参数设置
# mysql 运维

1. 查看MySQL连接数，查看当前处于连接未关闭状态的进程列表

    ```
    show full processlist;  
    ```
    若不加上full选项，则最多显示100条记录。若以root帐号登录，你能看到所有用户的当前连接。如果是其它普通帐号，只能看到自己占用的连接。

2. 查看MySQL数据库状态，将DB所有的状态打印出来，如需其中特定的项可以加上like '%变量名称%'
    ```
    show status;
    show status like '%变量名称%';
    ```
      * Aborted_clients 由于客户没有正确关闭连接已经死掉，已经放弃的连接数量。
      * Aborted_connects 尝试已经失败的MySQL服务器的连接的次数。
      * Connections 试图连接MySQL服务器的次数。
      * Created_tmp_tables 当执行语句时，已经被创造了的隐含临时表的数量。
      * Delayed_insert_threads 正在使用的延迟插入处理器线程的数量。
      * Delayed_writes 用INSERT DELAYED写入的行数。
      * Delayed_errors 用INSERT DELAYED写入的发生某些错误(可能重复键值)的行数。
      * Flush_commands 执行FLUSH命令的次数。
      * Handler_delete 请求从一张表中删除行的次数。
      * Handler_read_first 请求读入表中第一行的次数。
      * Handler_read_key 请求数字基于键读行。
      * Handler_read_next 请求读入基于一个键的一行的次数。
      * Handler_read_rnd 请求读入基于一个固定位置的一行的次数。
      * Handler_update 请求更新表中一行的次数。
      * Handler_write 请求向表中插入一行的次数。
      * Key_blocks_used 用于关键字缓存的块的数量。
      * Key_read_requests 请求从缓存读入一个键值的次数。
      * Key_reads 从磁盘物理读入一个键值的次数。
      * Key_write_requests 请求将一个关键字块写入缓存次数。
      * Key_writes 将一个键值块物理写入磁盘的次数。
      * Max_used_connections 同时使用的连接的最大数目。
      * Not_flushed_key_blocks 在键缓存中已经改变但是还没被清空到磁盘上的键块。
      * Not_flushed_delayed_rows 在INSERT DELAY队列中等待写入的行的数量。
      * Open_tables 打开表的数量。
      * Open_files 打开文件的数量。
      * Open_streams 打开流的数量(主要用于日志记载）
      * Opened_tables 已经打开的表的数量。
      * Questions 发往服务器的查询的数量。
      * Slow_queries 要花超过long_query_time时间的查询数量。
      * Threads_connected 当前打开的连接的数量。
      * Threads_running 不在睡眠的线程数量。
      * Uptime 服务器工作了多少秒。
  
 
3. 在调试程序时，如怀疑应用程序中存在申请DB连接未释放的情况，可以通过该命令查询连接数(以应用程序中的user登录)。如程序运行过程中连接数越来越多，则可以判断程序中有DB资源未释放。如需修改允许建立的最大连接数，win环境下需修改/mysql-advanced-5.6.19-win32/mysql-test/suite/ndb/下的my.cnf文件。

    ```
    set-variable=max_user_connections=30         #单用户的连接数
    set-variable=max_connections=800             #全局的限制连接数
    ```


# 参考
1. [查看mysql连接数和状态](https://www.cnblogs.com/pegasus827/p/8692290.html) . https://www.cnblogs.com/pegasus827/p/8692290.html
