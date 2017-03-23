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



