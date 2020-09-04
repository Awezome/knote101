### 查看建表语句
```
show create table xxx
```

### 创建hive表
```
CREATE external TABLE table_app (app_id string,group int) row format delimited fields terminated by '\t' LOCATION '/home/test2';
CREATE external TABLE table_app (app_id string) PARTITIONED BY (pday int) STORED AS PARQUET LOCATION '/home/test/';
```

### 导入hdfs文件，会把原hdfs的删掉
```
load data inpath 'hdfs://home/app_info/' overwrite into table app_info partition (day='20200616');
```

### 查询并保存在hdfs
```
insert overrite directory '/home/app_info/' row format delimited fields terminated by  ',' select * table_app where day=20200617;
```

### 创建分区信息
```
//外表生成完文件要创建分区信息
ALTER TABLE table_app ADD if not exists PARTITION(day=20190723) LOCATION '/home/app/20190723';
```
### 删除分区
```
//如果是外表，删除分区数据还在
ALTER TABLE app_info DROP IF EXISTS PARTITION(day='20200801'); 
```


