### 4.6.6 Using Foreign Keys

在MySQL中，InnoDB表支持检查外键约束。请参见第15章“InnoDB存储引擎”和第1.8.2.3节“外键差异”。

外键约束不仅仅需要连接两个表。对于除InnoDB之外的存储引擎，可以在定义列时使用REFERENCES tbl\_name（col\_name）语句，该参数没有实际的影响，仅作为备注或注释，您当前定义的列旨在引用另一个表中的列。使用这种语法时，理解这一点非常重要：

* MySQL不执行任何类型的CHECK来确保col\_name实际上存在于tbl\_name（或者甚至t​​bl\_name本身存在）中。

* MySQL不对tbl\_name执行任何类型的操作，例如删除行以响应您正在定义的表中的行执行的操作;换句话说，这种语法不会导致任何ON DELETE或ON UPDATE行为。 （虽然可以将ON DELETE或ON UPDATE语句写入REFERENCES语句中，但也被忽略。）



