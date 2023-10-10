## 命令
	- 总结常用
		- ```
		  #select
		  limit 0,2
		  
		  ##where
		  =
		  != <>
		  like %value%
		  is null
		  between 1 and 2
		  and
		  or
		  ## order by
		  desc 倒叙
		  ```
	- 最常用
		- ```mysql
		  
		  
		  mysql -h 主机名 -u 用户名 -p
		  
		  create database; 数据库名 [其他选项] ;
		  create database; samp_db character set gbk;  --指定编码为gbk
		  
		  show databases; --展示所有数据库
		  use 数据库名称; --选择数据库
		  
		  show tables; --展示数据库中的表
		  
		  #创建表名
		  create table students
		  	（
		  		id int unsigned not null auto_increment primary key,
		  		name char(8) not null,
		  		sex char(4) not null,
		  		age tinyint unsigned not null,
		  		tel char(13) null default "-"
		  	);
		  
		  -- 或者
		  mysql -D samp_db -u root -p < createtable.sql
		  
		  -- 插入
		  insert into 表名 values(params1,params2); -- 须传入所有的值
		  insert into 表名 (key2,key3,key4) values(value2,value3,value4) -- 可以传部分参数
		  
		  -- 查询
		  select 列名称 from 表名称 [查询条件];
		  select name,age from students; -- 举例
		  select * from students;-- 查询所有
		  select distinct 列名称 from 表名称;  --检索列中不同的值
		  select 列名 from 表名 limit 5 offset 4 --offset表示从第几行开始，limit表示选第几个，表示从4开始选五个
		  select 列名 from 表名 limit 4,5 --同上 注意这个位置是相反的
		  
		  # 查询-过滤数据 支持=、>、<、>=、<、!=,!<,!>,<>,  is [not] null、in、like 等等等
		  select 列名称 from 表名称 where 条件; 
		  select * from students where sex='女';
		  select * from students where sex!='女';
		  select * from students where sex<>'女'; -- 和上面同，但是Microsoft Access支持这种不支持上面的
		  select * from students where name like "%王%"; -- 查询名字中带有 "王" 字的所有人信息
		  select * from students where id<5 and age>20; -- 查询id小于5且年龄大于20的所有人信息:
		  select * from students where name is null; --判断空值
		  select * from students where id between 1 and 8; #寻找1-8中的值
		  select * from students where id<>6 and id between 1 and 8; #通过and符链接
		   select name,sex from students where age=12 or sex='女';#通过or连接，尽量使用圆括号包裹
		  -- 查询-排序 必须是最后一个子句
		  select 列名 from 表名 order by 列名 --排序 须放到最后末尾
		  select 列名 from 表名 order by 列名1,列名2 --须知，在不打乱1前提下，对1相同项进行列名2的排序
		  select 列名 from 表名 order by 2,3 --按照列位置排序，列位置从1开始而不是0
		  select 列名 from 表名 order by 列名 desc --降序
		  select 列名 from 表名 order by 列名1 desc,列名2 desc --针对前一个列名降序
		  
		  #更新表中数据
		  update 表名称 set 列名称=新值 where 更新条件;
		  update students set name="张伟鹏", age=19 where tel="13288097888"; --将手机号为 13288097888 的姓名改为 "张伟鹏", 年龄改为 19
		  
		  #删除表中数据
		  delete from 表名称 where --删除条件;
		  delete from students where id=2; --删除表中id=2
		  delete from students; --删除表中所有数据 
		  
		  #创建后表的修改
		  #添加列
		  alter table 表名 add 列名 列数据类型 [after 插入位置];
		  alter table students add address char(60); --表最后添加列
		  alter table students add birthday date after age; --在名为 age 的列后插入列 birthday
		  
		  #修改列
		  alter table 表名 drop 列名；
		  alter table students drop birthday;
		  
		  #重命名
		  alter table 表名 rename 新表名称;
		  
		  #删除整张表
		  drop table 表名;
		  
		  删除数据库
		  drop database 数据库名称;
		  ```
	- 注释
		- ```mysql
		  select * from students; -- 这个是注释
		  
		  #我是注释
		  
		  /* 我们都是注释
		  你看我们长不长 */
		  select * from students;
		  
		  ```
- SQL必知必会
	- ## 检索数据
		-
- 重要
	- 命令必须分号结尾
		-