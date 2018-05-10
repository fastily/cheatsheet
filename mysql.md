## Change Primary Key Value
```SQL
## Note: auto_increment value must be greater than largest index
ALTER TABLE DATABASE.TABLE auto_increment=9000
```

## Drop All Rows/Reset Primary Key Counter
```SQL
truncate DATABASE.TABLE 
```