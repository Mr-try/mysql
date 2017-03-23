### 4.6.3 Maximum of Column per Group

任务：查找最贵文章的数量、经销商和价格。

```
SELECT article, dealer, priceFROM   shop
WHERE  price=(SELECT MAX(price) FROM shop);
+---------+--------+-------+
| article | dealer | price |
+---------+--------+-------+
|    0004 | D      | 19.95 |
+---------+--------+-------+
```

其他解决方案是使用LEFT JOIN或按价格降序排序所有行，并使用MySQL特定的LIMIT语句仅获取第一行：

