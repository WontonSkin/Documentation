#### Linux下彻底卸载mysql 

```
0、停止服务
systemctl disable mysqld
systemctl stop    mysqld
ps -el | grep mysql  #查看相关mysql进程
```

```
1、清理mariadb
rpm -qa | grep mariadb
yum remove mariadb-libs -y
```

```
2、清理历史mysql
rpm -qa|grep -i mysql
rpm -ev MySQL-client-5.5.25a-1.rhel5
rpm -ev MySQL-client-5.5.25a-1.rhel5 --nodeps
rpm -e --noscripts MySQL-client-5.5.25a-1.rhel5
```

```
3、删除MySQL目录
find / -name mysql

/var/lib/mysql
/var/lib/mysql/mysql
/usr/lib64/mysql

rm -rf /var/lib/mysql
rm -rf /var/lib/mysql
rm -rf /usr/lib64/mysql
```

```
4、删除配置文件
rm -rf /etc/init.d/mysqld
rm -rf /etc/my.cnf
```

```
5、删除数据目录
rm -rf /data/mysql_data
```

```
参考链接：
```

https://cloud.tencent.com/developer/article/1402251

