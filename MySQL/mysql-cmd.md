# MySQL Reference Documentaion

## Basic Mysql shell commands

[List all databases](#list-all-databases)<br>
[Use a Database](#use-a-database)<br>
[List all Tables](#list-all-tables)<br>
[Describe a Table](#describe-a-table)<br>
[Get table schema](#get-table-schema)<br>
[List running process](#list-running-process)<br>
[List running process with full sql](#list-running-process-full-sql-text)<br>
[List long running process](#list-process-based-on-time)<br>
[show innodb status](#show-innodb-status)<br>

### List all databases
```
SHOW DATABASES;
```
### Use a Database
```
USE database;
```
### List all Tables
```
SHOW TABLES;
```
### Describe a Table
```
DESC tablename;
```
### Get table schema
```
SHOW CREATE TABLE tablename;
```
### List running process
```
SHOW PROCESSLIST;
```
### List running process full SQL text
```
SHOW FULL PROCESSLIST;
```
### List process based on time
```sql
SELECT 
    ID,
    USER,
    HOST,
    DB,
    COMMAND,
    TIME,
    STATE,
    INFO
FROM information_schema.PROCESSLIST
WHERE COMMAND != 'Sleep'
  AND TIME > 60 -- set the desired time here
ORDER BY TIME DESC;
```

### Show innodb status
```
SHOW ENGINE INNODB STATUS\G
```







