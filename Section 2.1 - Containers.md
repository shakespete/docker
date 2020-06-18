<h1>Mastering Containers</h1>

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


<h3>Anatomy of containers:</h3>

Containers are specially encapsulated and secured processes running on the host system. Containers leverage a lot of features and primitives available in the Linux OS. The most important ones are namespaces and cgroups. All processes running in containers only share the same Linux kernel of the underlying host operating system. This is fundamentally different compared with VMs, as each VM contains its own full-blown operating system.

<strong>Namespace:</strong> A namespace is an abstraction of global resources such as filesystems, network access, and process trees (also named PID namespaces) or the system group IDs and user IDs.

<strong>cgroups:</strong> Linux cgroups are used to limit, manage, and isolate resource usage of collections of processes running on a system.

<strong>Union filesystem (Unionfs):</strong> Unionfs forms the backbone of what is known as container images. Unionfs is mainly used on Linux and allows files and directories of distinct filesystems to be overlaid to form a single coherent filesystem.


The basement on top of which the Docker engine is built; is the container plumbing and is formed by two components, runc and containerd.

<strong>runC:</strong> runC is a lightweight, portable container runtime. runC is a tool for spawning and running containers according to the Open Container Initiative (OCI) specification.

<strong>Containerd:</strong> runC is a low-level implementation of a container runtime; containerd builds on top of it and adds higher-level features, such as image transfer and storage, container execution, and supervision as well as network and storage attachments.

![alt text](https://github.com/shakespete/docker/blob/master/img/docker_architecture.png)
