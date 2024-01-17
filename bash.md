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

## Variables
```bash
# Get cli args but only from the 2nd element and onwards
"${@:2}"

# Prepend Foo to every element of an array, MY_ARRAY
${MY_ARRAY[@]/#/Foo}

# Append Foo to every element of an array, MY_ARRAY
${MY_ARRAY[@]/%/Foo}

# Convert a string, referenced by MY_VAR, to lowercase
"${MY_VAR,,}"
```

## slurp file into variable
```bash
myVariable=$(<'<FILE_TO_SLURP>')
```

## append string to files (before the extension)
```bash
# ${f%.*} - all chars before ext
# ${f##*.} - all chars after ext (dot not incl)
for f in *; do
	mv -v "$f" "${f%.*}<TEXT_TO_APPEND>.${f##*.}"
done
```

## debug
```bash
bash -x "<COMMAND_TO_RUN>"
```

## truncate file
```bash
> '<PATH_TO_FILE>'
```

## Recursively move files to new directory
```bash
# recursively move all MOV files in cwd to a new dir
mv ./**/*.MOV '<TARGET_DIR>'
```