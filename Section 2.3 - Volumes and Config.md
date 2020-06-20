<h1>Data Volumes and Configuration:</h1>

<h3>Creating and mounting data volumes</h3>
Volumes allow containers to consume, produce, and modify a state. Volumes have a life cycle that goes beyond the life cycle of containers. When a container that uses a volume dies, the volume continues to exist. This is great for the durability of the state.

<h3>Creating volumes</h3>
The default volume driver is the so-called local driver, which stores the data locally in the host filesystem.

<h3>Mounting a volume</h3>
Once we have created a named volume, we can mount it into a container.

Docker volume persists beyond the lifetime of a container, and also, that volumes can be reused by other, even different, containers from the one that used it first.

It is important to note that the folder inside the container to which we mount a Docker volume is excluded from the Union filesystem. That is, each change inside this folder and any of its subfolders will not be part of the container layer, but will be persisted in the backing storage provided by the volume driver. This fact is really important since the container layer is deleted when the corresponding container is stopped and removed from the system.

It is also important to note that the updates are now propagated bi-directionally. If you make changes on the host, they will be propagated to the container, and vice versa. Also important is the fact that when you mount the current folder into the container target folder, the content that is already there is replaced by the content of the host folder.

<h3>Defining volumes in images</h3>
Luckily, there is a way of defining volumes in the Dockerfile. The keyword to do so is VOLUME, and we can either add the absolute path to a single folder or a comma-separated list of paths. These paths represent folders of the container's filesystem.

```
VOLUME /app/data 
VOLUME /app/data, /app/profiles, /app/config 
VOLUME ["/app/data", "/app/profiles", "/app/config"] 
```

When a container is started, Docker automatically creates a volume and mounts it to the corresponding target folder of the container for each path defined in the Dockerfile. Since each volume is created automatically by Docker, it will have an SHA-256 as its ID.

At container runtime, the folders defined as volumes in the Dockerfile are excluded from the Union filesystem, and thus any changes in those folders do not change the container layer but are persisted to the respective volume. It is now the responsibility of the operations engineers to make sure that the backing storage of the volumes is properly backed up.

```
$ docker image pull mongo:3.7
$ docker run --name my-mongo -d mongo:3.7
$ docker inspect --format '{{json .Mounts}}' my-mongo | jq .
```