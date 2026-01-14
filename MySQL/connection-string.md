# CONNECTION STRING REFRENCE
This section will help us to understand how to connect to mysql instances whether in on-prem or cloud hosted instances.

```
mysql -u username -h hostname -P portnumber databasename -p
```
eg.
```
mysql -u sanji -h localhost -P 3306 sakila -p
```
In case of connecting to cloud hoststed instances use the endpoint in the hostname