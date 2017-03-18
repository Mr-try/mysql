### 4.3.1 Creating and Selecting a Database

如果管理员在创建数据库，为您设置了权限。您可以开始使用它。否则，你需要自己创建：

```
mysql>CREATE DATABASE menagerie;
```

在UNIX，数据库名称是区分大小写的（不像SQL关键字）。（在Windows的领导下，该限制不适用，虽然你要参考数据库和表使用相同的lettercase在一个给定的查询。然而，由于种种原因，推荐的最佳实践是使用相同的lettercase被用来当数据库被创建。）

**注：如果你得到一个错误，如错误1044（42000）：用户访问被拒绝”micah'@'localhost'数据库'menagerie'在尝试创建一个数据库，这意味着，您的用户帐户没有这样做的必要的权限。以管理员或见 7.2章节： Section 7.2, “The MySQL Access Privilege System”。**

创建数据库不会默认选择使用它，必须显式地执行它。把menagerie设置为当前数据库，使用此语句：

```
mysql>USE menagerie
Database changed
```



