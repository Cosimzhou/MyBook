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


    INSERT IGNORE INTO <table>[(<column1>, <column2>, ...)] VALUES(<value1>, <value2>, ...)[,(<value1>, <value2>, ...),...]

    REPLACE INTO <table>[(<column1>, <column2>, ...)] VALUES(<value1>, <value2>, ...)[,(<value1>, <value2>, ...),...]
```

# DELETE语句格式
```sql
    DELETE [*] FROM <table> [WHERE <condition>]
```

# UPDATE语句格式
```sql
    UPDATE  <table> SET <column>=<value>[,<column>=<value>...] WHERE <condition>
```

# Insert or Update
```
INSERT INTO customers (name, email)
VALUES('field1_value','field2_value')
ON CONFLICT (unique_field)
DO UPDATE SET field2 = "new_field_value";
-- or DO NOTHING;
```

# Select into
```
INSERT INTO table2 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;

-- all column
INSERT INTO table2
SELECT * FROM table1
WHERE condition;
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

```sql
SELECT *, (CASE WHEN id > 100 THEN 1 ELSE 0 END) AS seg
FROM mapshop.change_records;

---

SELECT *, dense_rank() OVER(ORDER BY id) AS rank
FROM mapshop.change_records
WHERE table_name='mapshop.maps' AND record_id=1073741905
ORDER BY update_time ASC
LIMIT 100;

-- row_number dense_rank and rank

---
SELECT * FROM (
  SELECT *, dense_rank() OVER(ORDER BY id) AS rank
  FROM mapshop.change_records
  WHERE table_name='mapshop.devices' AND record_id=1
) AS t
WHERE rank < 100 AND rank >= 90
ORDER BY (t.updated_time, t.rank);

-- ntile

SELECT NTILE(4) OVER(ORDER BY id DESC) AS ntile, * FROM mapshop.change_records;
```

# CREATE TABLE建表
```sql
CREATE TABLE duty_list(
  Id_P int,
  Name varchar(255)
);
```

```
  ALTER TABLE table ALTER COLUMN column_num
  SET DEFAULT upper(md5(random()::text || clock_timestamp()::text)::varchar);
```

# CREATE INDEX

```sql
CREATE INDEX idx_name ON table_name USING gist (column_name range_ops);
```

# 排序
```sql
ORDER BY <field>[,<field2>,...] [DESC|ASC]
ORDER BY IF(ISNULL(<field>), 0, 1), <field> [DESC|ASC]
ORDER BY FIELD(<field>, vals.....)
```

```
CASE WHEN <field> xxx THEN xxx
     WHEN <field> xxx THEN xxx
     WHEN <field> xxx THEN xxx
     ELSE xxx END
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
# Join
* INNER JOIN 两表皆存才输出
* LEFT JOIN 前表存在就输出
* RIGHT JOIN 后表存在就输出
* FULL JOIN 任何表有都会输出

## 内连连表查询
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

Multi-Join Query
```
SELECT t1.name, t2.image_id, t3.path
FROM table1 AS t1
INNER JOIN table2 t2 ON t1.person_id = t2.person_id
INNER JOIN table3 t3 ON t2.image_id = t3.image_id
```


```
WITH pipeline_tasks AS (
  SELECT t1.job_id, CONCAT(t1.dag_id,'.',t1.task_id),
    t1.task_status, t1.create_time, alignment_id,
    ROW_NUMBER() OVER (
      PARTITION BY (t1.job_id,
        t1.dag_id,
        t1.task_id)
      ORDER BY t1.create_time DESC
    ) AS rank
  FROM pipeline.pipeline_job_logs AS t1
  JOIN pipeline.pipeline_jobs AS t2
  ON t1.job_id = t2.job_id
  WHERE CONCAT(t1.dag_id,'.',t1.task_id) IN ('%s')
    AND t2.alignment_id IN (%s)
    AND t1.task_status IN ('%s')
) SELECT * FROM pipeline_tasks WHERE rank = 1;
```

```
WITH pipeline_tasks AS (
    SELECT t1.job_id, CONCAT(t1.dag_id, '.', t1.task_id),
           t1.task_status, t1.create_time, t2.alignment_id,
					 t2.region_id, t2.track_id,
          ROW_NUMBER() OVER (
            PARTITION BY (t1.job_id, t1.dag_id, t1.task_id)
            ORDER BY t1.create_time DESC
          ) AS rank
    FROM pipeline.pipeline_job_logs AS t1
    JOIN pipeline.pipeline_jobs AS t2
    ON t1.job_id = t2.job_id
		WHERE t1.dag_id IN (
'track_generation_full_workflow',
'recording_session_alignment',
'omap_patch_workflow',
'commit_alignment',
'lmap_patch_workflow',
'commit_alignment',
'lane_el_creation_and_review_iterative_workflow',
'map_release_full_workflow',
'map_delivery_workflow')
) SELECT * FROM pipeline_tasks WHERE rank = 1;
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

```
DROP TRIGGER [ IF EXISTS ] update_time_trigger ON mapshop.devices [ CASCADE | RESTRICT ]
```

# PostGres命令
```
copy t_aa  from '/tmp/aa.csv' with delimiter ',';
copy (select * from t_aa where xxxx)  to '/tmp/aa.csv' with delimiter ',';
```

```

SELECT uuid_in(
  overlay(
    overlay(
      md5(
        random()::text || ':' || random()::text
      ) placing '4' from 13
    ) placing to_hex(
      floor(random()*(11-8+1) + 8)::int
    )::text from 17
  )::cstring
);

SELECT uuid_in(md5(random()::text || random()::text)::cstring);
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



-------------------
# SQL 优化

in  >
exists <

union / union all

in -> join

force index
