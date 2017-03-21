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

您不能使用算术比较运算符（例如=，&lt;或&lt;&gt;）来测试NULL,下面是个反面教材：

```
mysql>SELECT 1 = NULL, 1 <> NULL, 1 <NULL, 1 >NULL;
+----------+-----------+----------+----------+
| 1 = NULL | 1 <>NULL  | 1 <NULL  | 1 >NULL  |
+----------+-----------+----------+----------+
|     NULL |      NULL |     NULL |     NULL |
+----------+-----------+----------+----------+
```

因为与NULL的任何算术比较的结果也为NULL，您不能从这种比较获得任何有意义的结果。

在MySQL中，0或NULL表示false，任何其他值都表示真。布尔运算的真值默认为1。

这也是在前面的部分，在确定哪些动物不再活着使用death IS NOT NULL而不是death &lt;&gt; NULL的原因。

在GROUP BY中，两个NULL值被视为相等。

