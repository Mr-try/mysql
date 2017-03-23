### 4.6.5 Using User-Defined Variables

您可以使用MySQL用户变量记住结果，而不必将其存储在客户端中的临时变量中。 （见第10.4节“用户自定义变量”。）

例如，要找到最高和最低价格的文章，您可以这样做：

```
mysql>SELECT @min_price:=MIN(price),@max_price:=MAX(price) FROM shop;
mysql>SELECT * FROM shop WHERE price=@min_price OR price=@max_price;
+---------+--------+-------+
| article | dealer | price |
+---------+--------+-------+
|    0003 | D      |  1.25 |
|    0004 | D      | 19.95 |
+---------+--------+-------+
```



