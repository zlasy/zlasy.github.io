- [mysql notes](#mysql-notes)
  - [mysql server](#mysql-server)
  - [cluster](#cluster)
  - [mysql router](#mysql-router)
  - [mysql workbench](#mysql-workbench)
  - [mysql shell](#mysql-shell)
  - [connectors & apis](#connectors--apis)
- [reference](#reference)

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
4. 
## cluster
[ndb vs innodb](https://dev.mysql.com/doc/mysql-cluster-excerpt/5.7/en/mysql-cluster-ndb-innodb-engines.html)

## mysql router
innodb cluster的一部分

## mysql workbench

## mysql shell

## connectors & apis

# reference

- [mysql document](https://dev.mysql.com/doc/)
