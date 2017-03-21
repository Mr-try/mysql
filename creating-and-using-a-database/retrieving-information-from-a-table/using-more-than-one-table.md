#### 4.3.4.9 Using More Than one Table

宠物表跟踪你有哪些宠物。如果你想记录关于他们的其他信息，例如在他们的生活中的事件，如访问兽医或出生时，你需要另一个表。这个表应该是什么样子？它需要包含以下信息：

* 宠物名字，让你知道每个事件属于哪个动物。
* 日期，以便您知道事件发生的时间。
* 用于描述事件的字段。
* 如果您想要能够对事件进行分类需要设置事件类型字段。

鉴于这些注意事项，事件表的CREATE TABLE语句可能如下所示：

```
mysql>CREATE TABLE event (name VARCHAR(20), date DATE,
    ->type VARCHAR(15), remark VARCHAR(255));
```



