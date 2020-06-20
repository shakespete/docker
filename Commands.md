<h1>Commands:</h1>

<table>
  <tr>
    <td>docker container ls</td>
    <td>list running containers</td>
  </tr>
  <tr>
    <td>docker container ls -a</td>
    <td>list all containers</td>
  </tr>
  <tr>
    <td>docker container ls -q</td>
    <td>list the IDs of all containers</td>
  </tr>
  <tr>
    <td>docker container start **container name**</td>
    <td>start specified container</td>
  </tr>
  <tr>
    <td>docker container stop **container name**</td>
    <td>stop specified container</td>
  </tr>
  <tr>
    <td>docker container rm **container ID/name**</td>
    <td>remove a container</td>
  </tr>
  <tr>
    <td>docker container rm -f **container ID/name**</td>
    <td>force remove a container</td>
  </tr>
  <tr>
    <td>docker container inspect **container ID/name**</td>
    <td>inspect a container</td>
  </tr>
  <tr>
    <td>docker container inspect -f "{{json .State}}" **container ID/name** | jq .</td>
    <td>inspect/filter specific info</td>
  </tr>
  <tr>
    <td>docker container exec -i -t **container ID/name** /bin/sh</td>
    <td>exec into a running container. The -i flag signifies that we want to run the additional process interactively, and -t tells Docker that we want it to provide us with a TTY (a Terminal emulator) for the command. Finally, the process we run is /bin/sh.</td>
  </tr>
  <tr>
    <td>docker container attach **container ID/name**</td>
    <td>attach our Terminal's standard input, output, and error (or any combination of the three) to a running container</td>
  </tr>
  <tr>
    <td>docker container logs **container ID/name**</td>
    <td>access the logs of a given container</td>
  </tr>
  <tr>
    <td>docker container logs --tail 5 **container ID/name**</td>
    <td>only get a few of the latest entries</td>
  </tr>
  <tr>
    <td>docker container logs --tail 5 --follow **container ID/name**</td>
    <td>Sometimes, we want to follow the log that is produced by a container. This is possible when using the -f or --follow parameter. The following expression will output the last five log items and then follow the log as it is produced by the containerized process</td>
  </tr>
  <tr>
    <td>docker container diff **container ID/name**</td>
    <td>to see what has changed in our container in relation to the base image</td>
  </tr>
  <tr>
    <td>docker container rm -f $(docker container ls -aq)</td>
    <td>remove all running containers in order to clean up the system</td>
  </tr>
  <tr>
    <td>docker image history **container ID/name**</td>
    <td>to see how our custom image has been built</td>
  </tr>
  <tr>
    <td>docker image save -o ./backup/**file name**.tar **image name**</td>
    <td>takes **image name** image and exports it into a file called ./backup/**file name**.tar</td>
  </tr>
  <tr>
    <td>docker image load -i ./backup/**file name**.tar</td>
    <td>existing tarball and want to import it as an image into our system</td>
  </tr>
  <tr>
    <td>docker-machine create --driver virtualbox **vm name**</td>
    <td>Creates VM running in VirtualBox</td>
  </tr>
  <tr>
    <td>docker-machine ssh **vm name**</td>
    <td>SSH into this VM</td>
  </tr>
  <tr>
    <td>docker volume create **volume name**</td>
    <td>creates a volume called **volume name**</td>
  </tr>
  <tr>
    <td>docker volume inspect **volume name**</td>
    <td>to find out where the data is stored on the host</td>
  </tr>
  <tr>
    <td>docker container run --name **container name** -it -v **data**:/data alpine /bin/sh</td>
    <td>Mounts the **data** volume to the /data folder inside the container. This is mounted in default read/write mode</td>
  </tr>
  <tr>
    <td>docker container run --name **container name** -it -v **data**:/data:ro alpine /bin/sh</td>
    <td>Mounts the **data** volume to the /data folder inside the container. The volume is mounted as read-only (ro).</td>
  </tr>
  <tr>
    <td>docker container run --rm -it -v $(pwd)/src:/app/src alpine:latest /bin/sh</td>
    <td>Interactively starts an alpine container with a shell and mounts the src subfolder of the current directory into the container at /app/src. We need to use $(pwd) (or `pwd`, for that matter), which is the current directory, as when working with volumes, we always need to use absolute paths.</td>
  </tr>
  <tr>
    <td>docker volume rm **volume name**</td>
    <td>deletes volume</td>
  </tr>
 </table>   
 

                
 
     
                 
                   
          
 
                   
                    
  
               
