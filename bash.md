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
## ! commands
```bash
# re-run last command
!!

# Re-run command N commands ago
!-N

# Last parameter from previous command
!$

# All params from previous command
!*
```


## Job Control
```bash
# list all jobs
jobs

# bring job to foreground
fg %N # where N is the job number obtained from jobs

# bring job to background
bg %N # where N is the job number obtained from jobs
```


## Arrays
```bash
# Prepend Foo to every array element
${arr[@]/#/Foo}

# Append Foo to every array element
${arr[@]/%/Foo}
```


## Special Variables
```bash
# Get cli args but only from the 2nd element and onwards
"${@:2}"
```