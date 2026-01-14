# CONNECTION STRING REFRENCE
This section will help us to understand how to connect to mysql instances whether in on-prem or cloud hosted instances and some basic operations.

### connection string
```
mysql -u username -h hostname -P portnumber databasename -p
```
eg.
```
mysql -u sanji -h localhost -P 3306 sakila -p
```
In case of connecting to cloud hosted instances use the endpoint in the hostname by cloud provider.

### Execute queries from CLI

To execute a singe query we can use the -e option 
```
mysql -u sanji -h localhost -P 3306 sakila -e"SELECT * FROM sakila.country LIMIT 1;" -p
```
To execute multiple queries use a sql file to pass on it.
```
mysql -u sanji -h localhost -P 3306 database -p < scripts.sql
```

