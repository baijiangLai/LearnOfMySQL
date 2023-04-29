DCL:data control language，用来管理数据库用户、控制数据库的访问权限。

## 管理用户
1. 查询用户
```mysql
USE mysql;
SELECT * FROM user;
```
2. 创建用户
```mysql
CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';
```
注： 主机名是任意主机的话，那么主机名写`%`

3. 修改用户密码
```mysql
ALTER USER '用户名'@'主机名' IDENTIFIED WITH mysql_native_password BY '新密码';
```
4. 删除用户
```mysql
DROP USER '用户名'@'主机名';
```

## 权限控制

![权限.png](..%2F..%2Fimages%2F%E5%9F%BA%E7%A1%80%2FDCL%2F%E6%9D%83%E9%99%90.png)

1. 查询权限
```mysql
SHOW GRANTS FOR '用户名'@'主机名';
```
2. 授予权限
```mysql
GRANT 权限列表 ON 数据库名.表名 TO '用户名'@'主机名';
```
3. 撤销权限
```mysql
REVOKE 权限列表 ON 数据库名.表名 FROM '用户名'@'主机名';
```
