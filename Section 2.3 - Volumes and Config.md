<h1>Data Volumes and Configuration:</h1>


<h3>Creating and mounting data volumes</h3>
Volumes allow containers to consume, produce, and modify a state. Volumes have a life cycle that goes beyond the life cycle of containers. When a container that uses a volume dies, the volume continues to exist. This is great for the durability of the state.

<h3>Creating volumes</h3>
The default volume driver is the so-called local driver, which stores the data locally in the host filesystem.

<h3>Mounting a volume</h3>
Once we have created a named volume, we can mount it into a container.

Docker volume persists beyond the lifetime of a container, and also, that volumes can be reused by other, even different, containers from the one that used it first.

It is important to note that the folder inside the container to which we mount a Docker volume is excluded from the Union filesystem. That is, each change inside this folder and any of its subfolders will not be part of the container layer, but will be persisted in the backing storage provided by the volume driver. This fact is really important since the container layer is deleted when the corresponding container is stopped and removed from the system.

