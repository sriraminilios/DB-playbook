# DB objects size

This guide will help us to get the size of DB objects counts to get the overall picture of our DB instance.

### Overall DB size-GB
```sql
SELECT 
ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 3) AS total_db_size_gb
FROM information_schema.TABLES;
```

### Overall DB size-MB
```sql
SELECT 
ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 3) AS total_db_size_mb
FROM information_schema.TABLES;
```

### Order DB by size GB
```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 3) AS size_gb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA NOT IN (
  'mysql',
  'information_schema',
  'performance_schema',
  'sys'
)
GROUP BY TABLE_SCHEMA
ORDER BY size_gb DESC;
```

### Order DB by size mb
```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 , 3) AS size_mb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA NOT IN (
  'mysql',
  'information_schema',
  'performance_schema',
  'sys'
)
GROUP BY TABLE_SCHEMA
ORDER BY size_mb DESC;
```

### Order tables by size GB
```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  TABLE_NAME,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 3) AS size_gb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA NOT IN (
  'mysql',
  'information_schema',
  'performance_schema',
  'sys'
)
ORDER BY size_gb DESC;
```

### Order tables by size MB
```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  TABLE_NAME,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 3) AS size_mb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA NOT IN (
  'mysql',
  'information_schema',
  'performance_schema',
  'sys'
)
ORDER BY size_mb DESC;
```