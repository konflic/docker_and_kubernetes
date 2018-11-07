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

```-a``` flag is telling system to output everython into terminal.

#### 4) Restarting containers
If started earlier container was exited and started again with ```docker start -a <ID>``` command, the command for the container cannot be edited. 

#### 5) Clearing containers
If you want to clean your system completely from container images use

```docker system prune```

After this command you will get warning

```
docker system prune
WARNING! This will remove:
        - all stopped containers
        - all networks not used by at least one container
        - all dangling images
        - all build cache
Are you sure you want to continue? [y/N]
```

#### 6) Getting the logs from shutted down container

In order to get logs from started earlier and shut down container use **logs** command with container id.

This will not run the container, but get logs from it.

```bash
> sudo docker create busybox echo hi there
9d8e7bf88b01b426d08869ad86af6a0d5270dd0092e0243fc5d8f9a23dc2aee4
> sudo docker start 9d8e7bf88b01b426d08869ad86af6a0d5270dd0092e0243fc5d8f9a23dc2aee4
9d8e7bf88b01b426d08869ad86af6a0d5270dd0092e0243fc5d8f9a23dc2aee4
> sudo docker logs 9d8e7bf88b01b426d08869ad86af6a0d5270dd0092e0243fc5d8f9a23dc2aee4
hi there
```
