# DDL
DDL主要用来定义数据库、表、字段。

## 关于数据库
### 查询
查询所有数据库:
```mysql
SHOW DATABASES;
```
---
查询当前数据库:
```mysql
SELECT DATABASE();
```
---
### 创建
```mysql
CREATE DATABASE [IF NOT EXISTS] 数据库名 [DEFAULT CHARSET 字符集] [COLLATE 排序规则];
```
字符集不推荐utf8，因为存储长度存储3个字节; 
推荐使用utf8mb4;
----

### 删除
```mysql
DROP DATABASE [IF EXISTS] 数据库名;
```
---
### 使用
```mysql
USE 数据库名;
```

## 关于表
### 查询
查询当前数据库所有表:
```mysql
SHOW TABLES;
```
---
查询表结构:
```mysql
DESC 表名;
```
---
查询指定表的建表语句:
```mysql
SHOW CREATE TABLES 表名;
```


### 创建
```mysql
CREATE TABLE 表名 (
    字段1 字段1类型[COMMENT 字段1注释],
    字段2 字段2类型[COMMENT 字段2注释],
    字段3 字段3类型[COMMENT 字段3注释],
    ...
    字段n 字段n类型[COMMENT 字段n注释]
)[COMMENT 表注释]
```

#### 数据类型
数值类型：

![数值类型.png](..%2F..%2Fimages%2F%E5%9F%BA%E7%A1%80%2F%E6%95%B0%E5%80%BC%E7%B1%BB%E5%9E%8B.png)

---
字符串类型：

![字符串类型.png](..%2F..%2Fimages%2F%E5%9F%BA%E7%A1%80%2F%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%B1%BB%E5%9E%8B.png)

char(10):如果存储1个字符，也会占用10个字符的空间，会使用空格进行占位。性能高

varchar(10):如果存储1个字符，只用存储1个字符的空间，但是最大只存存储10个字符。性能较低。

---

日期类型：
![日期时间类型.png](..%2F..%2Fimages%2F%E5%9F%BA%E7%A1%80%2F%E6%97%A5%E6%9C%9F%E6%97%B6%E9%97%B4%E7%B1%BB%E5%9E%8B.png)

### 修改

添加字段
```mysql
ALTER  TABLE 表名 ADD 字段名 类型(长度) [COMMENT 注释] [约束]; 
```

---

修改字段

修改数据类型
```mysql
ALTER TABLE 表名 MODIFY 字段名 新数据类型(长度);
```


修改字段名和字段类型
```mysql
ALTER  TABLE 表名 CHANGE 旧字段名 新字段名 类型(长度) [COMMENT 注释](约束);
```

---

删除字段

```mysql
ALTER TABLE 表名 DROP 字段名;
```


---

修改表名
```mysql
ALTER TABLE 表名 RENAME TO 新表名;
```


### 删除

删除表
```mysql
DROP TABLE [IF EXISTS] 表名;
```

删除指定表，并重新创建该表
```mysql
TRUNCATE TABLE 表名;
```