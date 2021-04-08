## Change Primary Key Value
```SQL
## Note: auto_increment value must be greater than largest index
ALTER TABLE DATABASE.TABLE auto_increment=9000
```

## Drop All Rows/Reset Primary Key Counter
```SQL
truncate DATABASE.TABLE 
```

## cli
* `-q` - don't buffer output into memory (quick)
* `-r` - raw output, don't escape special chars like backslashes
* `-B` - use tabs as column separators in output (results in a tsv)
* `-h '<HOSTNAME>'` - hostname to use
