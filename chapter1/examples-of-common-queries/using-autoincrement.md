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

要以非1的AUTO\_INCREMENT值开始，请使用CREATE TABLE或ALTER TABLE设置该值，如下所示：

```
mysql>ALTER TABLE tbl AUTO_INCREMENT = 100;
```

**InnoDB Notes**

有关InnoDB特有的AUTO\_INCREMENT使用信息，请参见第15.8.6节“InnoDB中的AUTO\_INCREMENT处理”。

**MyISAM Notes**

对于MyISAM表，可以在多列索引中的辅助列上指定AUTO\_INCREMENT。在这种情况下，AUTO\_INCREMENT列的生成值计算为MAX\(auto\_increment\_column\)1 WHERE prefix = given-prefix。当您要将数据放入有序组中时，这很有用。

```
CREATE TABLE animals (
    grp ENUM('fish','mammal','bird') NOT NULL,
    id MEDIUMINT NOT NULL AUTO_INCREMENT,
    name CHAR(30) NOT NULL,
    PRIMARY KEY (grp,id)
) ENGINE=MyISAM;

INSERT INTO animals (grp,name) VALUES
    ('mammal','dog'),('mammal','cat'),
    ('bird','penguin'),('fish','lax'),('mammal','whale'),
    ('bird','ostrich');

SELECT * FROM animals ORDER BY grp,id;
```

返回结果：

```
+--------+----+---------+
| grp    | id | name    |
+--------+----+---------+
| fish   |  1 | lax     |
| mammal |  1 | dog     |
| mammal |  2 | cat     |
| mammal |  3 | whale   |
| bird   |  1 | penguin |
| bird   |  2 | ostrich |
+--------+----+---------+
```

在这种情况下（当AUTO\_INCREMENT列是多列索引的一部分时），如果删除任何组中具有最大AUTO\_INCREMENT值的行，则AUTO\_INCREMENT值将重新使用。即使对于MyISAM表也是如此，因为AUTO\_INCREMENT值通常不被重用。

* 如果AUTO\_INCREMENT列是多个索引的一部分，MySQL会使用以AUTO\_INCREMENT列开头的索引生成序列值（如果有的话）。例如，如果动态表中包含索引PRIMARY KEY（grp，id）和INDEX（id），则MySQL将忽略PRIMARY KEY以生成序列值。因此，该表将包含单个序列，而不是每个grp值的序列。

