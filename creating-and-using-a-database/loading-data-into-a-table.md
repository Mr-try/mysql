### 4.3.3 Loading Data into a Table

创建表之后可以用LOAD DATA和INSERT语句来填充表内容。

假设你的pet记录可以做如下描述。 （注意，MySQL期望日期格式为“YYYY-MM-DD”;这可能与以前不同）。

| name | owner | species | sex | birth | death |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Fluffy | Harold | cat | f | 1993-02-04 |  |
| Claws | Gwen | cat | m | 1994-03-17 |  |
| Buffy | Harold | dog | f | 1989-05-13 |  |
| Fang | Benny | dog | m | 1990-08-27 |  |
| Bowser | Diane | dog | m | 1979-08-31 | 1995-07-29 |
| Chirpy | Gwen | bird | f | 1998-09-11 |  |
| Whistler | Gwen | bird |  | 1997-12-09 |  |
| Slim | Benny | snake | m | 1996-04-29 |  |

因为你是从一个空表开始，一个简单的填充它的方法是创建一个文本文件，其中包含每一个动物的行，然后使用单个语句将文件的内容加载到表中。

您可以创建一个pet.txt文件，其中每行包含一条记录，其值由制表符分隔，并按CREATE TABLE语句中列出的顺序给出。对于缺失值（如仍然存在的动物的未知性别或死亡日期），可以使用NULL值。要在文本文件中表示这些，请使用 N（反斜杠，大写-N）。例如，Whistler的鸟的记录看起来像这样（值之间的空格是单个制表符）：

```
Whistler        Gwen    bird    \N      1997-12-09      \N
```

要将pet.txt文件加载到pet表中，请使用以下语句：

```
mysql>LOAD DATA LOCAL INFILE '/path/pet.txt' INTO TABLE pet;
```

如果您在Windows上使用 r  n作为行终止符的编辑器创建了该文件，则应该使用以下语句：

```
mysql>LOAD DATA LOCAL INFILE '/path/pet.txt' INTO TABLE pet
    ->LINES TERMINATED BY '\r\n';
```

（在运行OS X的Apple机器上，您可能要使用LINES TERMINATED BY' \r'。）

如果您愿意，可以在LOAD DATA语句中显式指定列值分隔符和行结束标记，但默认值为tabs和linefeed。这些足以使语句正确读取pet.txt文件。

