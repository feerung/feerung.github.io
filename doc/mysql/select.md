---
layout: doc
title: mysql
keywords: mysql选择
description: mysql选择
---




### 选择库
```
help show;
服务器状态信息      show status;
显示授予用户权限    show grants;
显示错误或警告消息  show errors;    show warnings;

显示创建库的语句    show create database database_name;
显示创建表的语句    show create table table_name;

查看库   show database;
选择库   use database;
查看表   show tables;
显示表列   show columns from table_name;
```

### 检索数据
```
所有列数据   select * from table_name;   # * 替换指定列字段,分割
检索不同行   select distinct column_name from table_name;
限制条数     select * from table_name limit 0,5;        # limit 开始,条数
限定表明     select * from database_name.table_name;
```

### 排序数据
```
单个列排序   select * from table_name order by id desc;    #order by 排序 按照id倒序，asc默认 正序，asc倒序
多个列排序   select * from table_name order by group_id desc, id desc;    #按字段顺序排序，具有相同group_id才会对id排序
排序结合限定条数  select * from table_name order by id desc limit 10;
```

### 过滤数据
```
select * from table_name where id > 10;   #where 条件 检索id大于10的数据
=         等于
<>        不等于
!=        不等于
<         小于
<=        小于等于
>         大于
>=        大于等于
between and   指定两个值之间(包含指定值)    # where id between 10 and 20
is null       空值检查      #where id is null;
is not null   空值检查      #where id is not null;

and         追加多条件都匹配(优先级高于or)    #where id >10 and pid >10;
or          多条件匹配任一条件               #where id >10 or pid >10;
in(val,val)     指定条件范围      #where group_id in (21,22);
not in(val,val) 排除指定范围      #where group_id not in (21,22);

like   通配符(%任意字符)    #where username like '张%';    #多模式匹配  %张% %张
like   通配符(_任意字符)    #where username like '张丽_';  #多模式匹配 _丽
```

### 组合过滤