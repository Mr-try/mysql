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

对于足够大的AUTO\_INCREMENT列，使用最小的整数数据类型来保存您需要的最大序列值。当列达到数据类型的上限时，下一次生成序列号则会失败。如果可能，使用UNSIGNED属性允许更大的范围。例如，如果使用TINYINT，最大允许序列号为127.对于TINYINT UNSIGNED，最大值为255.请参见第12.2.1节“整数类型（精确值） -  INTEGER，INT，SMALLINT，TINYINT，MEDIUMINT，BIGINT “对于所有整数类型的范围。

**注意：**

**对于多行插入，LAST\_INSERT\_ID\(\)和mysql\_insert\_id\(\)实际上从第一个插入的行返回AUTO\_INCREMENT键。这样可以在复制设置中在其他服务器上正确再现多行插入。**

