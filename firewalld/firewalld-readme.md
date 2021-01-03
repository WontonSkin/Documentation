#### 参考链接

- http://www.excelib.com/article/287/show/

---------------------------------

#### 常用命令总结

##### 1、运行、停止firewalld

```
启动服务：# systemctl start  firewalld
停止服务：# systemctl stop firewalld
查看状态：# systemctl status firewalld 或者 firewall-cmd --state
在开机时启用：# systemctl enable  firewalld
在开机时禁用：# systemctl disable firewalld
```

##### 2、防火墙打开某个端口

```
firewall-cmd --zone=public --add-port=9988/tcp
firewall-cmd --zone=public --add-port=3306/tcp
```

##### 3、保存为永久配置

```
firewall-cmd --permanent --add-service=http     #永久开放http
firewall-cmd --zone=public --add-port=3306/tcp  --permanent  #保存 
firewall-cmd --zone=public --remove-port=80/tcp --permanent  #删除
```

##### 4、查看防火墙信息/开放的端口

```
firewall-cmd --list-all     #centos7查看防火墙所有信息 
firewall-cmd --list-ports   #centos7查看防火墙开放的端口信息 
```

