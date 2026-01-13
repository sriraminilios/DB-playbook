# DB objects size

## This guide will help us to get the size of DB objects counts to get the overall picture of our DB instance.

### Overall DB size-GB
```sql
SELECT 
ROUND(SUM(DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024 / 1024, 3) AS total_db_size_gb
FROM information_schema.TABLES;
```