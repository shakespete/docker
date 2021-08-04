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
    <td>shows you all the details of a container</td>
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
    <td>docker image build -t **image-name** .</td>
    <td>Note that there is a period at the end of the preceding command. This command means that the Docker builder is creating a new image called image-name using the Dockerfile that is present in the current directory. Here, the period at the end of the command stands for current directory.</td>
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
  <tr>
    <td>docker image prune -f</td>
    <td>According to Docker, dangling images are layers that have no relationship to any tagged images. Such image layers are certainly useless to us and can quickly fill up our disk—it's better to remove them from time to time.</td>
  </tr>
  <tr>
    <td>docker container prune -f</td>
    <td>Stopped containers can waste precious resources too. If you're sure that you don't need these containers anymore, then you should remove them.</td>
  </tr>
  <tr>
    <td>docker volume prune</td>
    <td>Unused Docker volumes too can quickly fill up disk space. It is a good practice to tender your volumes, specifically in a development or CI environment where you create a lot of mostly temporary volumes. But I have to warn you, Docker volumes are meant to store data. Often, this data must live longer than the life cycle of a container.</td>
  </tr>
  <tr>
    <td>docker ps -a --format "table {{.Names}}\t{{.Image}}\t{{.Status}}"</td>
    <td>Show the name of the container, the name of the image, and the state of the container</td>
  </tr>
  <tr>
    <td>docker image ls --filter dangling=false --filter "reference=*/*/*:latest"</td>
    <td> outputs images that are not dangling, that is, real images whose fully qualified name is of the form registry/user|orgrepository>:tag, and the tag is equal to latest. </td>
  </tr>
  <tr>
    <td>docker container top **container_id**</td>
    <td>lists the processes running in the container</td>
  </tr>
  <tr>
    <td>docker container stats **container_id**</td>
    <td>shows a live view of how much CPU, memory, network, and disk the container is using</td>
  </tr>
  <tr>
    <td>docker container rm --force $(docker container ls --all --quiet)</td>
    <td>The $() syntax sends the output from one command into another command--it works just as well on Linux and Mac terminals, and on Windows PowerShell. Combining these commands gets a list of all the container IDs on your computer, and removes them all. This is a good way to tidy up your containers, but use it with caution, because it won’t ask for confirmation.</td>
  </tr>
  <tr>
    <td>docker container run --detach --publish 8088:80 **container ID/name**</td>
    <td>--detach Starts the container in the background and shows the container ID and --publish Publishes a port from the container to the computer</td>
  </tr>
 </table>
