# DB-objects-size

This guide will help us to get the size of DB objects counts to get the overall picture of our DB instance.

<table>
  <tr>
    <th>Command</th>
    <th>Description</th>
  </tr>
  <tr>
    
  </tr>
</table>


### Overall DB size GB

```sql
SELECT 
ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 2) AS total_db_size_gb
FROM information_schema.TABLES;
```

### Overall DB size MB

```sql
SELECT 
ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 2) AS total_db_size_mb
FROM information_schema.TABLES;
```

### Order DB by size GB

```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 2) AS size_gb
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

### Order DB by size GB

```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 , 2) AS size_mb
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

### Get DB size in GB

```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 2) AS size_gb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = 'your_database_name' -- change your DB Name
GROUP BY TABLE_SCHEMA;
```

### Get DB size in MB

```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 , 2) AS size_mb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = 'your_database_name' -- change your DB Name
GROUP BY TABLE_SCHEMA;
```


### Order tables by size GB

```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  TABLE_NAME,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 2) AS size_gb
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
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 2) AS size_mb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA NOT IN (
  'mysql',
  'information_schema',
  'performance_schema',
  'sys'
)
ORDER BY size_mb DESC;
```

### Get Table size in GB
```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  TABLE_NAME,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 2) AS size_gb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = 'your-db-name' -- change your db name
AND TABLE_NAME = 'your-table-name'; -- change your table name
```

### Get Table size in MB
```sql
SELECT 
  TABLE_SCHEMA AS database_name,
  TABLE_NAME,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 2) AS size_mb
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = 'your-db-name' -- change your db name
AND TABLE_NAME = 'your-table-name'; -- change your table name
```