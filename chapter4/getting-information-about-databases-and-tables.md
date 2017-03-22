## Getting Information About Databases and Tables

如果忘记了数据库或表的名称，或者给定表的结构是什么（例如，它的列是什么），该怎么办？ MySQL通过提供有关其支持的数据库和表的信息的几个语句来解决这个问题。

您以前看过SHOW DATABASES，其中列出了由服务器管理的数据库。要查找当前选择的数据库，请使用DATABASE\(\)函数：

```
mysql>SELECT DATABASE();
+------------+
| DATABASE() |
+------------+
| menagerie  |
+------------+
```

如果您尚未选择任何数据库，则结果为NULL。

要找出默认数据库包含的表（例如，当您不确定表的名称）时，请使用以下语句：

```
mysql>SHOW TABLES;
+---------------------+
| Tables_in_menagerie |
+---------------------+
| event               |
| pet                 |
+---------------------+
```



