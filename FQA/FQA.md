





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

















