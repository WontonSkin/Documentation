#### SQL语句总结 

##### 查看有哪些数据库

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
```

##### 创建一个数据库

```
mysql> create database test;
```

##### 使用某个数据库

```
mysql> use test;              #切换到test数据库
Database changed
mysql> select database();     #查看当前使用的是哪个数据库
+------------+
| database() |
+------------+
| test       |
+------------+
```

##### 创建表

```
mysql> create table pet (name VARCHAR(20), owner VARCHAR(20), species VARCHAR(20), sex CHAR(1), birth DATE, death DATE);
```

##### 查看表

```
mysql> show tables;
+----------------+
| Tables_in_test |
+----------------+
| pet            |
+----------------+
```

##### 删除表

```
mysql> drop table pet;
```

##### 查看某个表的结构信息

```
mysql> describe pet;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| name    | varchar(20) | YES  |     | NULL    |       |
| owner   | varchar(20) | YES  |     | NULL    |       |
| species | varchar(20) | YES  |     | NULL    |       |
| sex     | char(1)     | YES  |     | NULL    |       |
| birth   | date        | YES  |     | NULL    |       |
| death   | date        | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
```

##### 在表中插入数据

```
INSERT INTO pet VALUES ('Puffball','Diane','hamster','f','1999-03-30',NULL);
INSERT INTO pet VALUES ('Fluffy','Harold','cat','f','1993-02-04',NULL);
INSERT INTO pet VALUES ('Claws','Gwen','cat','m','1994-03-17',NULL);
INSERT INTO pet VALUES ('Buffy','Harold','dog','f','1989-05-13',NULL);
INSERT INTO pet VALUES ('Fang','Benny','dog','m','1990-08-27',NULL);
INSERT INTO pet VALUES ('Bowser','Diane','dog','m','1979-08-31','1995-07-29');
INSERT INTO pet VALUES ('Chirpy','Gwen','bird','f','1998-09-11',NULL);
INSERT INTO pet VALUES ('Whistler','Gwen','bird',NULL,'1997-12-09',NULL);
INSERT INTO pet VALUES ('Slim','Benny','snake','m','1996-04-29',NULL);
```

##### 检索表中内容

```
语法规则：SELECT what_to_select  FROM which_table  WHERE conditions_to_satisfy;
```

```
mysql> SELECT * FROM pet;           #检索表中所有内容
+----------+--------+---------+------+------------+------------+
| name     | owner  | species | sex  | birth      | death      |
+----------+--------+---------+------+------------+------------+
| Puffball | Diane  | hamster | f    | 1999-03-30 | NULL       |
| Fluffy   | Harold | cat     | f    | 1993-02-04 | NULL       |
| Claws    | Gwen   | cat     | m    | 1994-03-17 | NULL       |
| Buffy    | Harold | dog     | f    | 1989-05-13 | NULL       |
| Fang     | Benny  | dog     | m    | 1990-08-27 | NULL       |
| Bowser   | Diane  | dog     | m    | 1979-08-31 | 1995-07-29 |
| Chirpy   | Gwen   | bird    | f    | 1998-09-11 | NULL       |
| Whistler | Gwen   | bird    | NULL | 1997-12-09 | NULL       |
| Slim     | Benny  | snake   | m    | 1996-04-29 | NULL       |
+----------+--------+---------+------+------------+------------+
```

```
mysql> SELECT name,owner,species FROM pet;    #检索表中name,owner,species三列
+----------+--------+---------+
| name     | owner  | species |
+----------+--------+---------+
| Puffball | Diane  | hamster |
| Fluffy   | Harold | cat     |
| Claws    | Gwen   | cat     |
| Buffy    | Harold | dog     |
| Fang     | Benny  | dog     |
| Bowser   | Diane  | dog     |
| Chirpy   | Gwen   | bird    |
| Whistler | Gwen   | bird    |
| Slim     | Benny  | snake   |
+----------+--------+---------+
```

```
mysql> select * from pet limit 1;         #检索查询第一行数据
+----------+-------+---------+------+------------+-------+
| name     | owner | species | sex  | birth      | death |
+----------+-------+---------+------+------------+-------+
| Puffball | Diane | hamster | f    | 1999-03-30 | NULL  |
+----------+-------+---------+------+------------+-------+
```

```
mysql> select * from pet limit 1, 3;     #检索查询第2行开始的连续3行的数据
+--------+--------+---------+------+------------+-------+
| name   | owner  | species | sex  | birth      | death |
+--------+--------+---------+------+------------+-------+
| Fluffy | Harold | cat     | f    | 1993-02-04 | NULL  |
| Claws  | Gwen   | cat     | m    | 1994-03-17 | NULL  |
| Buffy  | Harold | dog     | f    | 1989-05-13 | NULL  |
+--------+--------+---------+------+------------+-------+
```

