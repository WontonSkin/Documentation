#### 参考链接

- http://www.excelib.com/article/287/show/

---------------------------------

#### 常用命令总结

##### 1、运行、停止、禁用firewalld

```
启动：# systemctl start  firewalld
查看状态：# systemctl status firewalld 或者 firewall-cmd --state
停止：# systemctl disable firewalld
禁用：# systemctl stop firewalld
```

##### 2、防火墙打开某个端口

```
firewall-cmd --zone=public --add-port=9988/tcp
firewall-cmd --zone=public --add-port=3306/tcp
```

