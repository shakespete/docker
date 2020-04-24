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
docker container diff <container ID/name>                   - to see what has changed in our container in relation to the base image
docker image history <container ID/name>                    - to see how our custom image has been built
docker image save -o ./backup/<file name>.tar <image name>  - takes <image name> image and exports it into a file called ./backup/<file name>.tar
docker image load -i ./backup/<file name>.tar               - existing tarball and want to import it as an image into our system