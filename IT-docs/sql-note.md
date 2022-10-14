SQL note
========

注：`[]`表示可选项，`<>`表示说明项，如`<table>`表示表名

# SELECT语句格式
```sql
    SELECT <columns> FROM <table> [WHERE <condition>] [LIMIT <num>] [ORDER BY <column> [DESC|ASC]] [GROUP BY <column>]
```

# INSERT语句格式
```sql
    INSERT INTO <table>[(<column1>, <column2>, ...)] VALUES(<value1>, <value2>, ...)[,(<value1>, <value2>, ...),...]
```

# DELETE语句格式
```sql
    DELETE [*] FROM <table> [WHERE <condition>]
```

# UPDATE语句格式
```sql
    UPDATE  <table> SET <column>=<value>[,<column>=<value>...] WHERE <condition>
```


# ALTER语句格式

    增加字段

```sql
     ALTER TABLE <table> ADD <column> <type>

    -- ALTER TABLE t_sample ADD c_example char(200)
```

    删除字段

```sql
     ALTER TABLE <table> DROP COLUMN <column>
```

    不支持DROP COLUMN功能的数据库可以使用下的命令组合

```sql
    CREATE TABLE temp AS SELECT Id_P, Name FROM duty_list WHERE 1 = 1;
    DROP TABLE duty_list;
    ALTER TABLE temp RENAME TO duty_list;
```

    修改字段类型

```sql
    ALTER TABLE <table> ALTER COLUMN <column> <type>
```

    修改表名

```sql
    ALTER TABLE <table-old> RENAME TO <table-new>;
```

```sql
ALTER SEQUENCE mapshop.devices_id_seq RESTART WITH 20;

TRUNCATE xxx_seq RESTART identity;  -- truncating a table back to 1
```

# DISTINCT 去重
```sql
    SELECT DISTINCT <columns> FROM <table> [WHERE <condition>] [LIMIT <num>] [ORDER BY <column> [DESC|ASC]] [GROUP BY <column>]
```

# COUNT
```sql
    SELECT COUNT(DISTINCT <columns>) FROM <table> [WHERE <condition>] [LIMIT <num>] [ORDER BY <column> [DESC|ASC]] [GROUP BY <column>]
```

# CREATE TABLE建表
```sql
CREATE TABLE duty_list(
  Id_P int,
  Name varchar(255)
);
```

# 排序
```sql
ORDER BY <field> [DESC|ASC]
```


# 查询重复的记录
```sql
SELECT name   
FROM   emp       
GROUP BY   name     
HAVING COUNT(*)>1;
--显示重复的记录
SELECT *
FROM   emp 
WHERE name in (
  SELECT name
  FROM   emp 
  GROUP BY   name
  HAVING COUNT(*)>1
); 
```

```sql
SELECT *
FROM table
WHERE batch in (......)
ORDER BY id ASC
LIMIT 20
OFFSET 2000;
```

# Sequence
```
SELECT pg_catalog.setval('mapshop.calibrations_id_seq', 4, true);
```

# 内连连表查询
```sql
SELECT COUNT(*)
FROM (
  SELECT *
  FROM t_workset_old
  WHERE city_code='110000'
    AND batch='20131017'
) AS a
INNER JOIN (
  SELECT *
  FROM t_workset_old
  WHERE city_code='110000'
    AND batch='20131201'
) AS b
ON a.pid = b.pid
  AND a.oid = b.oid;
```
注：上句的效率远低于下一句(当pid和oid均有索引的情况下)
```sql
SELECT COUNT(*)
FROM t_workset_old
WHERE city_code = '110000'
  AND batch = '20131201'
  AND (pid, oid) IN (
    SELECT pid, oid
    FROM t_workset_old
    WHERE city_code = '110000'
      AND batch = '20131017'
  ); 
```
原因很简单，由于上一句有三个select而下一句只需要两次

```
SELECT t2.name, t2.model_name,
   t1.create_timestamp, t1.calibration_configuration
FROM mapshop.calibrations as t1
JOIN mapshop.devices as t2
On t1.device_id = t2.id
WHERE t2.id = 3;
```

# Trigger
```sql
CREATE OR REPLACE FUNCTION update_timestamp()
RETURNS TRIGGER AS $$
BEGIN
  NEW.last_updated = now() at time zone 'UTC';
  RETURN NEW;
END;
$$ LANGUAGE plpgsql VOLATILE;

CREATE TRIGGER update_time_trigger BEFORE UPDATE ON mapshop.devices
FOR EACH ROW
EXECUTE PROCEDURE update_timestamp();
```

# PostGres命令
```
copy t_aa  from '/tmp/aa.csv' with delimiter ',';
copy (select * from t_aa where xxxx)  to '/tmp/aa.csv' with delimiter ',';
```


# MySQL

## 备份MySQL
只备份表结构
```bash
mysqldump --opt -d -u%(user)s -p%(password)s %(database)s > %(sqlfile).sql
```

只备份数据
```bash
mysqldump -t %(database)s -u%(user)s -p%(password)s > %(sqlfile).sql
```

全部
```bash
mysqldump --add-drop-table -u%(user)s -p%(password)s %(database)s > %(sqlfile).sql
```

## MySql的输出文件
```sql
SELECT uid FROM dianping ORDER BY uid INTO outfile "d://aaa.txt"
```

