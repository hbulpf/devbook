# centos7忘记mysql的密码
## 方法一. 找回安装是的初始密码：

```
grep 'temporary password' /var/log/mysqld.log
```

## 方法二. 使用操作系统账号和密码，进行修改密码

```
mysql -uroot -p
```

输入你的centos的密码

```
ALTER user 'root'@'localhost' IDENTIFIED BY '新密码';
```

注：如果显示 ERROR 1819 (HY000): Your password does not satisfy the current policy requirements，说明你的密码不符合安全要求，

```
FLUSH PRIVILEGES;
quit;
```

## 方法三. 强制进行修改密码

```
systemctl stop mysqld
systemctl set-environment MYSQLD_OPTS="--skip-grant-tables"
systemctl start mysqld
mysql -u root
```

进入 mysql

```
ALTER user 'root'@'localhost' IDENTIFIED BY '新密码';
```

注：如果显示ERROR 1819 (HY000): Your password does not satisfy the current policy requirements，说明你的密码不符合安全要求，

```
FLUSH PRIVILEGES;
quit;
```

```
systemctl stop mysqld
systemctl set-environment MYSQLD_OPTS=""
systemctl start mysqld
```
# 参考
1. [centos7忘记mysql的密码的解决方法](https://www.2cto.com/database/201809/778139.html)
