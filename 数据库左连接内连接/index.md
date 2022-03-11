# 数据库左连接内连接


* left join （左连接）：返回包括左表中的所有记录和右表中连接字段相等的记录。 
* right join （右连接）：返回包括右表中的所有记录和左表中连接字段相等的记录。 
* inner join（等值连接或者叫内连接）：只返回两个表中连接字段相等的行。 
* full join （全外连接）：返回左右表中所有的记录和左右表中连接字段相等的记录。

```mysql
A表　　　　　　　　　　
　　id　  name　　
　　1　　小王
　　2　　小李
　　3　　小刘
```

```mysql
B表
　　id　　A_id　　job
　　1　　2　　　　老师
　　2　　4　　　　程序员
```

1. 左连接：（左边的表不加限制）

```mysql
select a.name, b.job
from A a
         left join B b on a.id = b.A_id
```

返回结果

```mysql
三条记录
　　小王　　null
　　小李　　老师
　　小刘　　null
```

2. 右连接：（右边的表不加限制）

```mysql
select a.name, b.job
from A a
         right join B b on a.id = b.A_id
```

返回结果

```mysql
两条记录
　　小李　　老师
　　null　　程序员
```

3. 内连接：（只有2张表匹配的行才能显示）

```mysql
select a.name, b.job
from A a
         inner join B b on a.id = b.A_id
```

返回结果

```mysql
只能得到一条记录
　小李　　老师
```

4. 全外连接：(左右2张表都不加限制）

```mysql
select a.name, b.job
from A a full join B b
on a.id=b.A_id
```

```mysql
四条数据
　　小王　　null
　　小李　　老师
　　小刘　　null
　　null　　程序员
```
