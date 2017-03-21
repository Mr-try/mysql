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

与宠物表一样，通过创建包含以下信息的制表符分隔的文本文件来加载初始记录是最容易的。

| name | date | type | remark |
| :--- | :--- | :--- | :--- |
| Fluffy | 1995-05-15 | litter | 4 kittens, 3 female, 1 male |
| Buffy | 1993-06-23 | litter | 5 puppies, 2 female, 3 male |
| Buffy | 1994-06-19 | litter | 3 puppies, 3 female |
| Chirpy | 1999-03-21 | vet | needed beak straightened |
| Slim | 1997-08-03 | vet | broken rib |
| Bowser | 1991-10-12 | kennel |  |
| Fang | 1991-10-12 | kennel |  |
| Fang | 1998-08-28 | birthday | Gave him a new chew toy |
| Claws | 1998-03-17 | birthday | Gave him a new flea collar |
| Whistler | 1998-12-09 | birthday | First birthday |

按照如下命令加载记录：



```
mysql>LOAD DATA LOCAL INFILE 'event.txt' INTO TABLE event;
```



