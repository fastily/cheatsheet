## Get Task information
```bash
gradle tasks --all
```

## Create a new java gradle build in current dir
```bash
# new java application
gradle init --type java-application

# new java library
gradle init --type java-library
```

## Run continuous tasks on change in the background
```bash
gradle -t '<TASK_NAME_1>' '<TASK_NAME_2>'
```