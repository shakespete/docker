Mastering Containers:

Anatomy of the docker container run expression:

$ docker container run alpine echo "Hello World"

tool: Docker CLI
context
command
container image
process to run inside container


Stopping a container:
When you try to stop the trivia container, you will probably note that it takes a while until this command is executed. To be precise, it takes about 10 seconds. Why is this the case?

Docker sends a Linux SIGTERM signal to the main process running inside the container. If the process doesn't react to this signal and terminate itself, Docker waits for 10 seconds and then sends SIGKILL, which will kill the process forcefully and terminate the container.


Commands:
docker container ls                                         - list running containers
docker container ls -a                                      - list all containers
docker container ls -q                                      - list the IDs of all containers
docker container start <container name>                     - start specified container
docker container stop <container name>                      - stop specified container
docker container rm <container ID/name>                     - remove a container
docker container rm -f <container ID/name>                  - force remove a container
docker container inspect <container ID/name>                - inspect a container
docker container inspect -f "{{json .State}}" trivia | jq . - inspect specific info
docker container exec -i -t <container ID/name> /bin/sh     - exec into a running container
docker container attach <container ID/name>                 - attach our Terminal's standard input, output, and error (or any combination of the three) to a running container
docker container logs <container ID/name>                   - access the logs of a given container
docker container logs --tail 5 <container ID/name>          - only get a few of the latest entries
docker container logs --tail 5 --follow <container ID/name> - follow the log that is produced by a container




