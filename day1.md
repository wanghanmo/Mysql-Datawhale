<center><font size=5 color='green'>数据库基础知识</font></center>
1. 数据库的定义
<p>　　数据库是一个以某种有组织的方式存储的数据集合。最简单的办法是将数据库想象为一个文件柜。这个文件柜是一个存放数据的物理位置，不管数据是什么，也不管数据是如何组织的。</p>
2. 关系型数据库
<p>　　关系数据库，是建立在关系模型基础上的数据库，借助于集合代数等数学概念和方法来处理数据库中的数据。(百度百科)</p>
3.  二维表
<p>　　有一个唯一的表名，表结构是二维的，有行和列</p>
4. 行
<p>　　表中的一条记录</p>
5. 列
<p>　　表中的一个字段</p>
6. 主键
<p>　　唯一标识表中每行的这个列（或几列构成的元祖），当有索引时会与主键构成B+树</p>
7. 外键
<p>　　外键与主键连接，外键的表被称为主表的从表</p>
<center><font size=5 color='green'>MySQL数据库管理系统</font></center>
1. 数据库
<p>　　A database is a structured collection of data. It may be anything from a simple shopping list to a picture gallery or the vast amounts of information in a corporate network. To add, access, and process data stored in a computer database, you need a database management system such as MySQL Server. Since computers are very good at handling large amounts of data, database management systems play a central role in computing, as standalone utilities, or as parts of other applications. </p>
<p>　　A relational database stores data in separate tables rather than putting all the data in one big storeroom. The database structures are organized into physical files optimized for speed. The logical model, with objects such as databases, tables, views, rows, and columns, offers a flexible programming environment. You set up rules governing the relationships between different data fields, such as one-to-one, one-to-many, unique, required or optional, and “pointers” between different tables. The database enforces these rules, so that with a well-designed database, your application never sees inconsistent, duplicate, orphan, out-of-date, or missing data. (摘自官方文档)</p>
2. 数据表

```c
/**
  Prepares a dd::Table object from mysql_prepare_create_table() output
  and return it to the caller.
  @param thd                Thread handle
  @param sch_obj            Schema.
  @param table_name         Table name.
  @param create_info        HA_CREATE_INFO describing the table to be created.
  @param create_fields      List of fields for the table.
  @param keyinfo            Array with descriptions of keys for the table.
  @param keys               Number of keys.
  @param keys_onoff         Enable or disable keys.
  @param fk_keyinfo         Array with descriptions of foreign keys for the
  table.
  @param fk_keys            Number of foreign keys.
  @param file               handler instance for the table.
  @returns Constructed dd::Table object, or nullptr in case of an error.
*/
std::unique_ptr<dd::Table> create_table(
    THD *thd, const dd::Schema &sch_obj, const dd::String_type &table_name,
    HA_CREATE_INFO *create_info, const List<Create_field> &create_fields,
    const KEY *keyinfo, uint keys,
    Alter_info::enum_enable_or_disable keys_onoff,
const FOREIGN_KEY *fk_keyinfo, uint fk_keys, handler *file);
```

线程句柄，schema对象，数据表的名字，创建的信息，创建的fields(字段名+类型名)，索引信息，索引个数，索引开关，外键信息，外键个数，table的句柄信息，返回一个dd::Table对象。

3. 视图
<p>　　视图是对多张表的引用是虚表，不会真实存储数据，对select语句的表进行操作。这篇文章讲解的很清楚<a href="https://www.cnblogs.com/chenpi/p/5133648.html#_label4">Mysql中的视图</a></p>

4. 存储过程
<p>　　存储过程就是为以后使用而保存的一条
或多条 SQL语句。可将其视为批文件，虽然它们的作用不仅限于批处理。可以参考下面这篇文章<a href='https://www.cnblogs.com/mark-chan/p/5384139.html'>MySQL存储过程</a></p>
