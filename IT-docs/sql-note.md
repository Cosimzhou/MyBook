SQL note
========

注：[]表示可选项，<>表示说明项，如<table>表示表名

@ SELECT语句格式
    SELECT <columns> FROM <table> [WHERE <condition>] [LIMIT <num>] [ORDER BY <column>] [GROUP BY <column>]

@ INSERT语句格式
    INSERT INTO <table>[(<column1>, <column2>, ...)] VALUES(<value1>, <value2>, ...)[,(<value1>, <value2>, ...),...]

@ DELETE语句格式
    DELETE [*] FROM <table> [WHERE <condition>]

@ UPDATE语句格式
    UPDATE  <table> SET <column>=<value>[,<column>=<value>...] WHERE <condition>


@ALTER语句格式
    增加字段
     ALTER TABLE <table> ADD <column> <type>
    -- ALTER TABLE t_sample ADD c_example char(200)
    删除字段
     ALTER TABLE <table> DROP COLUMN <column>
    -- 不支持DROP COLUMN功能的数据库可以使用下的命令组合
    CREATE TABLE temp AS SELECT Id_P, Name FROM duty_list WHERE 1 = 1;
    DROP TABLE duty_list;
    ALTER TABLE temp RENAME TO duty_list;
    修改字段类型
    ALTER TABLE <table> ALTER COLUMN <column> <type>
    修改表名
    ALTER TABLE <table-old> RENAME TO <table-new>;

@DISTINCT 去重
    SELECT DISTINCT <columns> FROM <table> [WHERE <condition>] [LIMIT <num>] [ORDER BY <column>] [GROUP BY <column>]

@COUNT
    SELECT COUNT(DISTINCT <columns>) FROM <table> [WHERE <condition>] [LIMIT <num>] [ORDER BY <column>] [GROUP BY <column>]

@CREATE TABLE建表
CREATE TABLE duty_list(
Id_P int,
Name varchar(255)
);

@排序
ORDER BY <field> [DESC|ASC]


@查询重复的记录
select name   
from   emp       
group by   name     
having count(*)>1;
--显示重复的记录
select *
from   emp 
where name in (
       select name
       from   emp 
       group by   name
       having count(*)>1
); 



@PostGres命令
copy t_aa  from '/tmp/aa.csv' with delimiter ',';
copy (select * from t_aa where xxxx)  to '/tmp/aa.csv' with delimiter ',';


@备份MySQL
--只备份表结构
mysqldump --opt -d -u%(user)s -p%(password)s %(database)s > %(sqlfile).sql

--只备份数据
mysqldump -t %(database)s -u%(user)s -p%(password)s > %(sqlfile).sql
--全部
mysqldump --add-drop-table -u%(user)s -p%(password)s %(database)s > %(sqlfile).sql

@MySql的输出文件
SELECT uid FROM dianping ORDER BY uid INTO outfile "d://aaa.txt"

@内连连表查询
select count(*)
from (
              select *
              from t_workset_old
              where city_code='110000'
                         and batch='20131017'
         ) as a
         inner join
         (
               select *
               from t_workset_old
               where city_code='110000'
                          and batch='20131201'
         ) as b
         on a.pid = b.pid
               and a.oid = b.oid;
注：上句的效率远低于下一句(当pid和oid均有索引的情况下)
select count(*)
from t_workset_old
where city_code = '110000'
           and batch = '20131201'
           and (pid, oid) in (
                  select pid, oid
                  from t_workset_old
                  where city_code = '110000'
                             and batch = '20131017'
           ); 
原因很简单，由于上一句有三个select而下一句只需要两次






@查询重复的记录
select name   
from   emp       
group by   name     
having count(*)>1;
--显示重复的记录
select *
from   emp 
where name in (
       select name
       from   emp 
       group by   name
       having count(*)>1
); 



@PostGres命令
copy t_aa  from '/tmp/aa.csv' with delimiter ',';
copy (select * from t_aa where xxxx)  to '/tmp/aa.csv' with delimiter ',';


@备份MySQL
--只备份表结构
mysqldump --opt -d -u%(user)s -p%(password)s %(database)s > %(sqlfile).sql

--只备份数据
mysqldump -t %(database)s -u%(user)s -p%(password)s > %(sqlfile).sql
--全部
mysqldump --add-drop-table -u%(user)s -p%(password)s %(database)s > %(sqlfile).sql

@MySql的输出文件
select uid from dianping order by uid into outfile "d://aaa.txt"

@内连连表查询
select count(*)
from (
              select *
              from t_workset_old
              where city_code='110000'
                         and batch='20131017'
         ) as a
         inner join
         (
               select *
               from t_workset_old
               where city_code='110000'
                          and batch='20131201'
         ) as b
         on a.pid = b.pid
               and a.oid = b.oid;
注：上句的效率远低于下一句(当pid和oid均有索引的情况下)
select count(*)
from t_workset_old
where city_code = '110000'
           and batch = '20131201'
           and (pid, oid) in (
                  select pid, oid
                  from t_workset_old
                  where city_code = '110000'
                             and batch = '20131017'
           ); 
原因很简单，由于上一句有三个select而下一句只需要两次


@增加字段
     alter table docdsp     add dspcode char(200)
@删除字段
     ALTER TABLE table_NAME DROP COLUMN column_NAME
@修改字段类型
     ALTER TABLE table_name  ALTER COLUMN column_name new_data_type

