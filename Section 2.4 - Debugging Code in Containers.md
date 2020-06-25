<h1>Debugging Code Running in Containers</h1>

To test the application we have developed so far by running it inside a container. To do this, we have to create a Dockerfile first, so that we can build a container image, from which we can then run a container.

The 0.0.0.0 address simply means all IPv4 addresses on the local machine. If a host has two IP addresses, say 52.11.32.13 and 10.11.0.1, and a server running on the host listens on 0.0.0.0, it will be reachable at both of those IPs.

```
docker container run --rm -it --name <container-name> --volume $(pwd):/app -p 3000:3000 <image-name>
```

The path to the host folder needs to be an absolute path.

Now, if we do mount the current folder into the container as described above, then whatever was in the /app folder of the container image will be overridden by the content of the mapped host folder, that is, in our case, the current folder. That's exactly what we want—we want the current source to be mapped from the host in the container.