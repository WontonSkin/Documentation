





##### 如何查看glibc版本

```
方式一:  ls -l /lib/libc.so.*
方式二:  ldd --version
方式三:  /lib/libc.so.6
```

![image-20201223223659783](pic/image-20201223223659783.png)

-----------------------------------------

##### 如何查看函数符号表

```
nm -C libPocoNetd.so | grep "RawSocket::RawSocket"
```

![image-20201223224935289](pic/image-20201223224935289.png)

-----------------------

##### systemctl 使用总结

```
systemctl enable mysqld    #配置开机启动
systemctl disable mysqld   #取消开机启动

systemctl start mysqld     #启动mysql服务
systemctl stop  mysqld     #停止mysql服务

systemctl status mysqld            #查看mysql服务状态
systemctl status mysqld.service    #查看mysql服务状态
```

-------------------------------------------

##### SeLinux 操作说明

```
setenforce 0       #临时关闭SeLinux
sestatus           #查看SeLinux状态
vi /etc/selinux/config，将SELINU置为disabled    #永久关闭SeLinux，需要重启机器 
```

-----------------------------

##### linux 防火墙操作说明

```
systemctl stop firewalld.service       #停止防火墙服务，临时
systemctl disable firewalld.service    #防火墙开机不启用
```

------------------------------

##### 添加smb服务到防火墙

```
firewall-cmd --add-service samba --permanent  #永久添加samba服务到防火墙策略中
firewall-cmd --reload                         #重启防火墙
firewall-cmd --list-all|grep samba            #查看samba服务是否添加到防火墙中
```

---------------------









