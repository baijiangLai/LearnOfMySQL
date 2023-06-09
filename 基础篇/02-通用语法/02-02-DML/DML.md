DML:对数据库中表中数据记录进行增删改操作(添加、修改、删除)

 ## 添加
1. 指定字段添加数据
```mysql
insert into 表名(字段名1, 字段名2) values(值1, 值2);
```

2. 给全部字段添加数据
```mysql
insert into 表名 values(值1, 值2);
```


3. 批量添加数据
   4. 指定字段
    ```mysql
    INSERT INTO表名(字段名1,字段名2,...)VALUES(值1,值2,...).(值1,值2...).(值1,值2,.….) ;
    ```
   5. 所有字段
    ```mysql
    INSERT INTO表名VALUES(值1,值2,...),(值1,值2，...)，(值1，值2, ...);
    ```

注意：
1. 插入数据的时候，指定的字段顺序需要和值的顺序一一对应。
2. 插入数据大小应在字段规定范围内。


## 修改
```mysql
update 表名 set 字段名1=值1, 字段名2=值2,....[where 条件];
```

注：修改语句的条件可以有也可以没有，没有天剑就会修改整张表的所有数据。

## 删除
```mysql
delete from 表名 [where 条件];
```

注：
1. delete语句的条件可有可无，没有的话，会删除整张表数据
2. delete语句不能删除某个字段的值，如果想删除每个字段的值，那么使用update将那个位置值设值为null