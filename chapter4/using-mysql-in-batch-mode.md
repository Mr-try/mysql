## 4.5 Using mysql in Batch Mode

在前面的部分中，都是以交互方式使用mysql输入语句并查看结果。您也可以在批处理模式下运行mysql。为此，将要运行的语句放在一个文件中，然后告诉mysql从文件中读取其输入：

```
shell>mysql < batch-file
```

如果您在Windows下运行mysql，为了避免特殊字符带来的问题，您可以这样做：

```
C:\>mysql -e "source batch-file"
```

如果需要在命令行中指定连接参数，命令可以如下所示：

```

```

```
shell>mysql -h host -u user -p < batch-file
Enter password: 
********
```



