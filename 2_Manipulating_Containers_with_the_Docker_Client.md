# Manipulating Containers with the Docker Client

This section includes notes from the secon module.

[Back to contents](/README.md)

#### 1) We can execute commands with contariner, for example:

```docker run busybox echo hello```

Output:

```hello```

This works because command *echo* is included in the container busybox

```docker run busybox ls```

Output:

```
bin
dev
etc
home
proc
root
sys
tmp
usr
var
```
If the particular command is not included in the container it will show an error message.

#### 2) Listing running containers
```docker ps``` - shows info on currently running containers, if nothing is running tha table is empty

```docker ps --all``` - shows all the containers ever created on the machine

#### 3) Container lifecycle
```docker run``` = ```docker create``` + ```docker start```

```docker start -a <container-id>``` - means to catch and show the output from the container 

#### 4) Restarting containers
If started earlier container was exited and started again with ```docker start -a <ID>``` command, the command for the container cannot be edited. 

#### 5) Clearing containers
```docker system prune```
После этой команды будет выведено предупреждение:
```
docker system prune
WARNING! This will remove:
        - all stopped containers
        - all networks not used by at least one container
        - all dangling images
        - all build cache
Are you sure you want to continue? [y/N]
```
