# PSQL commands

<!-- Index section -->

### List all databases

| Description                           | Command       |
| ---------------------------------     | ------------- |
| List all databases                    | \l            |
| Switch database                       | \c database   |
| List all Tables in current Database   | \dt           |
| Describe a specified table            | \d table      |
| List users in Current Database        | \du           |

### Show active connections

To list all active connections

```sql
SELECT * FROM pg_stat_activity;
```
