# Backup and Restore in mysql using mysqldump
This guide will help us to understand how to take logical backups in mysql and restore them.

- [Backup](#backup)<br>
    - [Full backup](#full-backup)<br>
    - [Database backup](#database-backup)<br>
    - [Table backup](#table-backup)<br>
    - [Schema backup](#schema-backup)<br>

- [Restore](#restore)
    - [Restore a single Database](#restore-a-single-database)
    - [Restore a Multiple Database](#restore-multiple-databases)
    - [Restore Tables](#restore-tables)

## Backup
### Full backup

If we want to take a full backup i.e., all databases, procedures, routines, and events without interrupting any connections: [This is not recommended for cloud based instances use specific db backup method]

```bash
mysqldump -h hostname -P portNumber -u username -p -A -R -E --triggers --single-transaction -v > full_backup.sql
```

1. -A For all databases (we can also use --all-databases)<br>
2. -R For all routines (stored procedures & triggers)<br>
3. -E For all events<br>
4. **--single-transaction** without locking the tables i.e., without interrupting any connection (R/W).<br>
5. -v For verbose mode.

### Database backup
If we want to take backup of one database:

```bash 
mysqldump -h hostname -P portNumber -u username -p -R -E --triggers --single-transaction -v database > db_backup.sql
```

If we want to take backup of two or more specified database(s):

```bash
mysqldump -h hostname -P portNumber -u username -p -R -E --triggers --single-transaction -v -B db1 db2 db3 > db_backup.sql
```
Give the name of databases to backup as space seperated using -B option

### Table Backup 

If we want to take backup of one or more tables of a specified database:

```bash
mysqldump -h hostname -P portNumber -u username -p --single-transaction -v db tb1 tb2 > table_backup.sql
```
Simply specify the database followed by the table names.

### Schema Backup

If we want to take backup only DB schema or table schema:

Database:
```bash
mysqldump -h hostname -P portNumber -u username -p -R -E --no-data --triggers --single-transaction -v database > schema.sql
```
Table:
```bash
mysqldump -h hostname -P portNumber -u username --no-data --triggers --single-transaction -v database table > schema.sql
```

## Restore

### Restore a single Database

To Restore a single database simple pipe the backup file by specifying the database

```bash
mysql -h hostname -P portNumber -u username database < database.sql
```

### Restore Multiple Databases

To Restore multiple databases the backup will handle the use db statement.

```bash
mysql -h hostname -P portNumber -u username < database.sql
```

### Restore tables

To restore tables specify the database in which the tables need to be restored.

```bash
mysql -h hostname -P portNumber -u username database < database.sql
```
For more information check out the official documentaion.<br>
:link: [mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)