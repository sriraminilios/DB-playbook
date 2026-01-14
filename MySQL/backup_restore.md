# Backup and Restore in mysql
This guide will help us to understand how to take logical backups in mysql and restore them.

## Backup
### Full backup

If you want to take a full backup i.e., all databases, procedures, routines, and events without interrupting any connections:

```bash
mysqldump -u [username] -p -A -R -E --triggers --single-transaction > full_backup.sql
```

1.-A For all databases (you can also use --all-databases)
2.-R For all routines (stored procedures & triggers)
3.-E For all events
4.--single-transaction Without locking the tables i.e., without interrupting any connection (R/W).