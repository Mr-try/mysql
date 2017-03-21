#### 4.3.4.6 Working with NULL Values

从概念上讲，NULL意味着“缺少未知值”，并且它与其他值有些不同。要测试NULL，请使用IS NULL和IS NOT NULL运算符，如下所示：

```
mysql>SELECT 1 IS NULL, 1 IS NOT NULL;
+-----------+---------------+
| 1 IS NULL | 1 IS NOT NULL |
+-----------+---------------+
|         0 |             1 |
+-----------+---------------+
```



