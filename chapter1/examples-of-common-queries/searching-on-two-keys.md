### 4.6.7 Searching on Two Keys

使用单个key的OR和AND被优化，一个棘手的情况是在OR上搜索两个不同的键：

```
SELECT field1_index, field2_index FROM test_table
WHERE field1_index = '1' OR  field2_index = '1'
```

MySql对这种情况进行了优化。请参见第9.2.1.3节“索引合并优化”。

