表写顺序(语法):

```mysql
SELECT
    字段列表
FROM
    表名列表
WHERE
    条件列表N
GROUP BY
    分组字段列表
HAVING
    分组后条件列表
ORDER BY
    排序字段列表
LIMIT
    分页参数
```

## 基本查询
1. 查询多个字段
```mysql
SELECT 字段1，字段2,字段3 ... FROM表名;
SELECT * FROM 表名;
```
2. 设值别名
```mysql
SELECT 字段1[AS 别名1], 字段2[AS 别名2] ... FROM 表名;
```
3. 去除重复数据
```mysql
SELECT DISTINCT 字段列表 FROM 表名;
```

## 条件查询
```mysql
SELECT 字段列表 FROM 表名 WHERE 条件列表;
```
条件:

![条件查询比较运算符.png](..%2F..%2Fimages%2F%E5%9F%BA%E7%A1%80%2FDQL%2F%E6%9D%A1%E4%BB%B6%E6%9F%A5%E8%AF%A2%E6%AF%94%E8%BE%83%E8%BF%90%E7%AE%97%E7%AC%A6.png)

![条件查询逻辑运算符.png](..%2F..%2Fimages%2F%E5%9F%BA%E7%A1%80%2FDQL%2F%E6%9D%A1%E4%BB%B6%E6%9F%A5%E8%AF%A2%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6.png)


## 聚合函数
定义: 将一列数据作为一个整体进行纵向计算

![聚合函数.png](..%2F..%2Fimages%2F%E5%9F%BA%E7%A1%80%2FDQL%2F%E8%81%9A%E5%90%88%E5%87%BD%E6%95%B0.png)

语法:
```mysql
SELECT 聚合函数(字段列表) FROM 表名;
```

注: null值不参与所有聚合函数运算。


## 分组查询
```mysql
SELECT 字段列表 FROM 表名 [WHERE 条件] GROUP BY 分组字段名 [HAVING 分组后过滤条件]
```

where和having区别:
1. where是分组之前进行过滤，不满足where条件，不参与分组;having是分组之后对结果的过滤
2. where不能对聚合函数进行判断，having可以。

注:
1. 执行顺序: where > 聚合函数 > having
2. 分组过后，查询字段一般为聚合函数和分组字段，查询其他字段无任何意义。


## 排序查询
```mysql
SELECT 字段列表 FROM 表名 ORDER BY 字段1 排序方式1，字段2 排序方式2；
```
排序方式:
1. ASC:升序(默认)
2. DESC:降序

注意：如果是多个字段排序，当第一个字段值相同的时候，才会根据第二个字段进行排序


## 分页查询
1. 语法
```mysql
SELECT 字段列表 FROM 表名 LIMIT 起始索引,查询记录数;
```

注意:
- 起始索引从0开始，起始索引=(查询页码-1)*每页显示记录数。 
- 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT。 
- 如果查询的是第一页数据，起始索引可以省略，直接简写为limit 10。


## 执行顺序
```mysql
FROM
    表名列表
WHERE
    条件列表 
GROUP BY
    分组字段列表
HAVING
    分组后条件列表
SELECT
    字段列表
ORDER BY
    排序字段列表
LIMIT
    分页参数
```