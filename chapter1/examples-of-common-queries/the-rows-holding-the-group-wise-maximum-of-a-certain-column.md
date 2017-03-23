### 4.6.4 The Rows Holding the Group-wise Maximum of a Certain Column

任务：找到最贵价格的文章的经销商。

```
SELECT article, dealer, price
FROM   shop s1
WHERE  price=(SELECT MAX(s2.price)
              FROM shop s2
              WHERE s1.article = s2.article);

+---------+--------+-------+
| article | dealer | price |
+---------+--------+-------+
|    0001 | B      |  3.99 |
|    0002 | A      | 10.99 |
|    0003 | C      |  1.69 |
|    0004 | D      | 19.95 |
+---------+--------+-------+
```

上述示例使用相关的子查询，可能无效（请参见第14.2.10.7节“相关子查询”）。解决问题的其他可能性是在FROM或LEFT JOIN语句中使用不相关的子查询。

