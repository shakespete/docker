<h1>Commands:</h1>

<table>
  <tr>
    <td>docker container ls</td><td>- list running containers</td>
  </tr>
  <tr>
    <td>docker container ls -a</td><td>- list all containers</td>
  </tr>
  <tr>
    <td>docker container ls -q</td><td>- list the IDs of all containers</td>
  </tr>
  <tr>
    <td>docker container start <container name></td><td>- start specified container</td>
  </tr>
  <tr>
    <td>docker container stop <container name></td><td>- stop specified container</td>
  </tr>
  <tr>
    <td>docker container rm <container ID/name></td><td>- remove a container</td>
  </tr>
  <tr>
    <td>docker container rm -f <container ID/name></td><td>- force remove a container</td>
  </tr>
  <tr>
    <td>docker container inspect <container ID/name></td><td>- inspect a container</td>
  </tr>
  <tr>
    <td>docker container inspect -f "{{json .State}}" trivia | jq .</td><td>- inspect specific info</td>
  </tr>
  <tr>
    <td>docker container exec -i -t <container ID/name> /bin/sh</td><td>- exec into a running container</td>
  </tr>
  <tr>
    <td>docker container attach <container ID/name></td><td>- attach our Terminal's standard input, output, and error (or any combination of the three) to a running container</td>
  </tr>
  <tr>
    <td>docker container logs <container ID/name></td><td>- access the logs of a given container</td>
  </tr>
  <tr>
    <td>docker container logs --tail 5 <container ID/name></td><td>- only get a few of the latest entries</td>
  </tr>
  <tr>
    <td>docker container logs --tail 5 --follow <container ID/name></td><td>- follow the log that is produced by a container</td>
  </tr>
  <tr>
    <td>docker container diff <container ID/name></td><td>- to see what has changed in our container in relation to the base image</td>
  </tr>
  <tr>
    <td>docker image history <container ID/name></td><td>- to see how our custom image has been built</td>
  </tr>
  <tr>
    <td>docker image save -o ./backup/<file name>.tar <image name></td><td>- takes <image name> image and exports it into a file called ./backup/<file name>.tar</td>
  </tr>
  <tr>
    <td>docker image load -i ./backup/<file name>.tar</td><td>- existing tarball and want to import it as an image into our system</td>
  </tr>
 </table>   
 

                
 
     
                 
                   
          
 
                   
                    
  
               
