## Loop through lines of a file
```bash
while read theLine || [[ -n $theLine ]]; do
	echo "$theLine"

done < "<THE_FILE_NAME>"
```