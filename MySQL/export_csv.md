# Export MySQL query results in CSV format.

This guide will help us to export SQL query results into CSV format.

> Change the hostname, username, query for your config.

```bash
mysql -h localhost -u sanji -p sakila -e "select * from country;" | sed "s/'/\'/;s/\t/\",\"/g;s/^/\"/;s/$/\"/;s/\n//g" > country.csv
```
#### Regex explanation
- s/// means substitute what's between the first // with what's between the second //
- The "g" at the end is a modifier that means "all instance, not just first"
- ^ Beginning of line
- $ Means end of line
