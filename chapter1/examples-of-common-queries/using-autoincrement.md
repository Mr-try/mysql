### 4.6.9 Using AUTO\_INCREMENT

AUTO\_INCREMENT属性可用于为新行生成的唯一标识：

```
CREATE TABLE animals (
     id MEDIUMINT NOT NULL AUTO_INCREMENT,
     name CHAR(30) NOT NULL,
     PRIMARY KEY (id)
);

INSERT INTO animals (name) VALUES
    ('dog'),('cat'),('penguin'),
    ('lax'),('whale'),('ostrich');

SELECT * FROM animals;
```

返回结果：

```
+----+---------+
| id | name    |
+----+---------+
|  1 | dog     |
|  2 | cat     |
|  3 | penguin |
|  4 | lax     |
|  5 | whale   |
|  6 | ostrich |
+----+---------+
```

没有为AUTO\_INCREMENT列指定值，因此MySQL会自动分配序列号。您也可以明确地将0分配给列以生成序列号，除非启用了NO\_AUTO\_VALUE\_ON\_ZERO SQL模式。如果列被声明为NOT NULL，那么也可以为列分配NULL以生成序列号。当您将任何其他值插入到AUTO\_INCREMENT列中时，列被设置为该值，并且重置序列，以便下一个自动生成的值按照最大的列值顺序。

您可以使用LAST\_INSERT\_ID\(\) SQL函数或mysql\_insert\_id\(\) C API函数检索最近自动生成的AUTO\_INCREMENT值。这些功能是特定于连接的，所以它们的返回值不受另外一个也执行插入的连接的影响。

