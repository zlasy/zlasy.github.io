- [mysql notes](#mysql-notes)
  - [mysql server](#mysql-server)
  - [cluster](#cluster)
  - [mysql router](#mysql-router)
  - [mysql workbench](#mysql-workbench)
  - [mysql shell](#mysql-shell)
  - [connectors & apis](#connectors--apis)
- [Relative Framework](#relative-framework)
- [Reference](#reference)

# mysql notes
1. [mysql版本](https://blog.csdn.net/liang_0609/article/details/77334959)

## mysql server
1. Program
   - mysqld `The SQL daemon (that is, the MySQL server).`
   - mysqld_safe  `A server startup script. mysqld_safe attempts to start mysqld.`
   - mysql.server   `A server startup script. This script is used on systems that use System V-style run directories containing scripts that start system services for particular run levels. It invokes mysqld_safe to start the MySQL server.`
   - mysqld_multi  `A server startup script that can start or stop multiple servers installed on the system.`
2. Environment Variables
   - [Environment Variables Lists](https://dev.mysql.com/doc/refman/8.0/en/environment-variables.html)
3. Server Config
   - `mysqld --verbose --help`
   - `mysqladmin variables`
   - `mysqladmin extended-status`
   - `mysql> SHOW VARIABLES;`
   - `mysql> SHOW STATUS;`
4. Server Log
   - query log
   - slow query log
   - error log
   - binary log
5. Server Plugins
   - Enterprise Thread Pool
   - Rewriter Query Rewrite Plugin
   - The ddl_rewriter Plugin
   - The Clone Plugin
6. Backup and Recovery
   - Physical vs Logical
   - Online vs Offline
   - Local vs Remote
   - Full vs Incremental vs Point-In-Time
7. [Optimization](https://dev.mysql.com/doc/refman/8.0/en/optimization.html)
8. [Data Type](https://dev.mysql.com/doc/refman/8.0/en/data-types.html)
9. [Function & Operation](https://dev.mysql.com/doc/refman/8.0/en/func-op-summary-ref.html)
10. The InnoDB Storage Engine
   - Best Practices
     - Specifying a primary key for every table using the most frequently queried column or columns, or an auto-increment value if there is no obvious primary key.   
     指定主键，最好用最常用来查询的列，如果没有这样的列，就用自增。
     - Using joins wherever data is pulled from multiple tables based on identical ID values from those tables. For fast join performance, define foreign keys on the join columns, and declare those columns with the same data type in each table. Adding foreign keys ensures that referenced columns are indexed, which can improve performance. Foreign keys also propagate deletes or updates to all affected tables, and prevent insertion of data in a child table if the corresponding IDs are not present in the parent table.   
     多表同id联查使用joins。使用外键来提高查询效率。
     - Turning off autocommit. Committing hundreds of times a second puts a cap on performance (limited by the write speed of your storage device).
     - Grouping sets of related DML operations into transactions, by bracketing them with START TRANSACTION and COMMIT statements. While you don't want to commit too often, you also don't want to issue huge batches of INSERT, UPDATE, or DELETE statements that run for hours without committing.   
     用事务批量处理相关的dml，避免频繁commit
     - Not using LOCK TABLES statements. InnoDB can handle multiple sessions all reading and writing to the same table at once, without sacrificing reliability or high performance. To get exclusive write access to a set of rows, use the SELECT ... FOR UPDATE syntax to lock just the rows you intend to update.   
     不要锁表。
     - Enabling the innodb_file_per_table option or using general tablespaces to put the data and indexes for tables into separate files, instead of the system tablespace.   
     每张表单独记录文件（默认的）
     - Evaluating whether your data and access patterns benefit from the InnoDB table or page compression features. You can compress InnoDB tables without sacrificing read/write capability.
     - Running your server with the option --sql_mode=NO_ENGINE_SUBSTITUTION to prevent tables being created with a different storage engine if there is an issue with the engine specified in the ENGINE= clause of CREATE TABLE.
   - [architecture](https://dev.mysql.com/doc/refman/8.0/en/innodb-architecture.html)   
   ![](https://dev.mysql.com/doc/refman/8.0/en/images/innodb-architecture.png)
   - InnoDB Limits
     - 最大1017列
     - 最多64个二级索引
     - 不同的row format有不同的索引长度限制，3072或者767
     - 索引里最多16列
     - 一行的数据大小不能超过page size的一半，默认16KB的页大小，行限制就是8000bytes。但是对于64k的页大小，行大小限制是16k。LONGBLOB和LONGTEXT限制是4GB，同时行大小最大不能超过4GB
     - 虽然innodb支持超过64k的行大小，但是mysql本身只支持到64k
   - Replication


## cluster
[ndb vs innodb](https://dev.mysql.com/doc/mysql-cluster-excerpt/5.7/en/mysql-cluster-ndb-innodb-engines.html)

## mysql router
innodb cluster的一部分

## mysql workbench

## mysql shell

## connectors & apis

# Relative Framework
- jpa
- [mybatis]()
- [sharding-sphere]()

# Reference

- [mysql document](https://dev.mysql.com/doc/)
