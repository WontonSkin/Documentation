## shell脚本

常用shell命令用法记录，包括sed、awk等

### 1. 常用命令

#### 1.1 sed用法

```shell
#语法
sed [-hnV][-e<script>][-f<script文件>][文本文件]
#以行为单位的新增/删除
nl /etc/passwd | sed '2d'    ## 删除第2行
#以行为单位的替换与显示
nl /etc/passwd | sed '2,5c No 2-5 number'  ## 将第2-5行的内容取代成为"No 2-5 number"
#数据的搜寻并显示
nl /etc/passwd | sed -n '/root/p' ## 搜索有root关键字的行，p参数将某个选择的数据打印出来
#数据的搜寻并替换
sed 's/要被取代的字串/新的字串/g'

#直接修改文件内容(危险动作)
sed -i 's/\.$/\!/g' regular_express.txt          ## 将文件中的每一行结尾若为 . 则换成 !
sed -i '$a This is a test' regular_express.txt   ## 在最后一行加入"This is a test"字符串
## 其中$代表的是最后一行，而a的动作是新增
## sed 的 -i 选项可以直接修改文件内容，这功能非常有帮助
```

参考链接：https://www.runoob.com/linux/linux-comm-sed.html



### 2. 常用案例

#### 2.1 统计某个进程有多少线程数

```shell
#!/bin/bash
XX_PID=$(ps -e | grep mysqld | awk '{ print $1}')  #获取某个进程号
echo "pid is:"
echo "${XX_PID}"

for i in $XX_PID     #由于可能有多个同名进程，故需要遍历链表
do
	echo "----------------------"
	echo "name:" 
	cat /proc/${i}/comm           #打印进程名

	echo "task nums:"
	ls -l /proc/${i}/task | wc -l     #统计线程数，此处统计的时候将"."也统计了，故需要总数-1
done
```

#### 2.2 获取主机ip地址

```shell
#!/bin/bash
VAR="eth0"
HOST_IP=$(ifconfig $VAR | grep "inet " | awk '{ print $2}')
echo $HOST_IP
```

#### 2.3 文本替换

```shell
# 将源字符串"ClientAliveInterval"，替换为"#ClientAliveInterval"
sed -i 's/'ClientAliveInterval'/'#ClientAliveInterval'/g' /etc/ssh/sshd_config
```

