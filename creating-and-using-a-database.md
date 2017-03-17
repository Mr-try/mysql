## 4.3 Creating and Using a Database

[4.3.1 Creating and Selecting a Database](https://dev.mysql.com/doc/refman/5.7/en/creating-database.html)

[4.3.2 Creating a Table](https://dev.mysql.com/doc/refman/5.7/en/creating-tables.html)

[4.3.3 Loading Data into a Table](https://dev.mysql.com/doc/refman/5.7/en/loading-tables.html)

[4.3.4 Retrieving Information from a Table](https://dev.mysql.com/doc/refman/5.7/en/retrieving-data.html)

一旦知道如何输入SQL语句，就可以访问数据库了。

假设你在家里有几个宠物（你的食品），你想跟踪各种类型的信息。您可以通过创建表来保存数据并加载所需的信息来实现。然后，您可以通过从表中检索数据来回答关于您的动物的不同类型的问题。本节介绍如何执行以下操作：

* 创建数据库
* 创建表
* 将数据加载到表中
* 以各种方式从表中检索数据
* 使用多个表

menagerie数据库很简单，但是不难想到现实世界中可能使用类似类型的数据库的情况。例如，这样的数据库可以被农民用来跟踪牲畜，或者由兽医来跟踪患者记录。可以从MySQL Web站点获取包含以下部分中使用的一些查询和样本数据的menagerie分发。它提供压缩的tar文件和Zip格式在[http://dev.mysql.com/doc/。](http://dev.mysql.com/doc/。)

使用SHOW语句查找服务器上当前存在哪些数据库：

```
mysql>
SHOW DATABASES;
+----------+
| Database |
+----------+
| mysql    |
| test     |
| tmp      |
+----------+
```



