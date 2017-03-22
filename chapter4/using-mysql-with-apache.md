## 4.7 Using MySQL with Apache

有一些程序会让您通过MySQL数据库验证用户，还可以将日志文件写入MySQL表。

您可以通过将以下内容放入Apache配置文件中使Apache日志记录格式更改为易于读取：

```

```

```
LogFormat \
        "\"%h\",%{%Y%m%d%H%M%S}t,%>s,\"%b\",\"%{Content-Type}o\",  \
        \"%U\",\"%{Referer}i\",\"%{User-Agent}i\""
```



