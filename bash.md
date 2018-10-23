## Loop through lines of a file
```bash
while read theLine || [[ -n $theLine ]]; do
	echo "$theLine"

done < "<THE_FILE_NAME>"
```

## join function
```bash
join_by() {
	local IFS="$1"
	shift
	echo "$*"
}

# example
join_by , a "b c" d #a,b c,d
```