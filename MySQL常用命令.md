### 设置临时编码
```
SET NAMES utf8mb4
```

### 修改字符集
```
alter table table_book CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 新增字段
```
alter table table_book ADD COLUMN `number` bigint(20) NOT NULL DEFAULT 0 COMMENT 'number';
alter table table_book add column `number` int(11) unsigned not null default 0 comment 'number' after `status`;
```

### 修改字段
```
alter table table_book modify column book_name varchar(64) not null default '' comment 'name' ;
```

### 删除索引
```
alter table table_book drop index uniq_book_id;
```

### 增加索引
```
alter table table_book add unique index uniq_book_id (`book_id`);
alter table quote_list add column `id` int(11) unsigned primary KEY AUTO_INCREMENT;  
```
