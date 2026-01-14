# Backup and Restore in mysql
This guide will help us to understand how to take logical backups in mysql and restore them.

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

### Databases backup

If we want to take a backup of one or more specified database(s):

```bash
mysqldump -h hostname -P portNumber -u username -p -R -E --triggers --single-transaction -v -B db1 db2 db3 > db_backup.sql
```
Give the name of databases to backup as space seperated using -B option
