<h1>Creating and Managing Container Images</h1>


<h3>What are images?</h3>
In Linux, everything is a file. The whole operating system is basically a
filesystem with files and folders stored on the local disk. This is an important
fact to remember when looking at what container images are.
As we will see, an image is basically a big tarball containing a filesystem.
More specifically, it contains a layered filesystem.

<h3>The layered filesystem</h3>
Container images are templates from which containers are created.
These images are not made up of just one monolithic block but are composed of
many layers. The first layer in the image is also called the base layer.

The layers of a container image are all immutable. Immutable means that once generated,
the layer cannot ever be changed. The only possible operation affecting the layer is its
physical deletion.

<h3>The writable container layer</h3>
As we have discussed, a container image is made of a stack of immutable or read-only layers.
When the Docker Engine creates a container from such an image, it adds a writable container
layer on top of this stack of immutable layers.
The Container Layer is marked as read/write.

![alt text](https://github.com/shakespete/docker/blob/master/img/writable_container_layer.png)

Another advantage of the immutability of image layers is that they can be shared among many containers created from this image. All that is needed is a thin, writable container layer for each container:

![alt text](https://github.com/shakespete/docker/blob/master/img/multiple_rw_layers.png)

<h3>Creating images</h3>
<h4>1) Interactive image creation</h4>
- We run the container interactively with an attached teletypewriter (TTY) using the -it parameter
- Run a shell inside the container using /bin/sh

<h4>2) Using Dockerfiles</h4>
A Dockerfile is a text file that is usually literally called Dockerfile. It contains instructions
on how to build a custom container image. It is a declarative way of building images.
- Each line of the Dockerfile results in a layer in the resulting image.
- The base layer is always the lowest layer in the stack

Don't let yourself be confused by this. In reality, the base layer is always the lowest layer in the stack.

![alt text](https://github.com/shakespete/docker/blob/master/img/layer_stack.png)

<h3>KEYWORDS:</h3>

FROM
- Every Dockerfile starts with the FROM keyword. With it, we define which base image we want to start building our custom image from.
- If we really want to start from scratch, we can also use the following statement: FROM scratch

RUN
- The argument for RUN is any valid Linux command
- RUN yum install -y wget => The preceding command is using the yum CentOS package manager to install the wget package into the running container.
- RUN apt-get update && apt-get install -y wget => Ubuntu uses apt-get as a package manager
- If we use more than one line, we need to put a backslash (\) at the end of the lines to indicate to the shell that the command continues on the next line.

COPY and ADD
- These two keywords are used to copy files and folders from the host into the image that we're building.
- The two keywords are very similar, with the exception that the ADD keyword also lets us copy and unpack TAR files, as well as providing a URL as a source for the files and folders to copy.

WORKDIR
- Defines the working directory or context that is used when a container is run from our custom image.
- So, if I want to set the context to the /app/bin folder inside the image => WORKDIR /app/bin
- All activity that happens inside the image after the preceding line will use this directory as the working directory.
- Only the WORKDIR keyword sets the context across the layers of the image. The cd command alone is not persisted across layers.

CMD and ENTRYPOINT
- The CMD and ENTRYPOINT keywords are special. While all other keywords defined for a Dockerfile are executed at the time the image
is built by the Docker builder, these two are actually definitions of what will happen when a container is started from the image we define.
- When the container runtime starts a container, it needs to know what the process or application will be that has to run inside that container.
- CMD and ENTRYPOINT are used to tell Docker what the start process is and how to start that process.
- ENTRYPOINT is used to define the command of the expression
- CMD is used to define the parameters for the command
- For both ENTRYPOINT and CMD, the values are formatted as a JSON array of strings, where the individual items correspond to the tokens of the expression that are separated by whitespace.
This is the preferred way of defining CMD and ENTRYPOINT. It is also called the exec form.
- If you leave ENTRYPOINT undefined, then it will have the default value of /bin/sh -c, and whatever the value of CMD is will be passed as a string to the shell command.


<h3>So, how does the builder work, exactly?</h3>

It starts with the base image. From this base image, once downloaded into the local cache, the builder creates a container
and runs the first statement of the Dockerfile inside this container. Then, it stops the container and persists the changes
made in the container into a new image layer. The builder then creates a new container from the base image and the new layer
and runs the second statement inside this new container. Once again, the result is committed to a new layer.
This process is repeated until the very last statement in the Dockerfile is encountered.

![alt text](https://github.com/shakespete/docker/blob/master/img/builder.png)

<h3>Multi-step builds</h3>
We have some stages that are used to build the final artifacts, and then a final stage, where we use the minimal necessary base image and copy the artifacts into it. This results in very small Docker images.

<h3>Dockerfile best practices</h3>
- First and foremost, we need to consider that containers are meant to be ephemeral. By ephemeral, we mean that a container can be stopped and destroyed, and a new one built and put in place with an absolute minimum of setup and configuration.
- The next best practice tells us that we should order the individual commands in the Dockerfile so that we leverage caching as much as possible.
** When we're rebuilding a previously built image, the only layers that are rebuilt are the ones that have changed, but if one layer needs to be rebuilt, all subsequent layers also need to be rebuilt.
- A further best practice is to keep the number of layers that make up your image relatively small. 
- Remember that in a Dockerfile, each line that starts with a keyword such as FROM, COPY, or RUN creates a new layer. The easiest way to reduce the number of layers is to combine multiple individual RUN commands into a single one.

<h4>3) The third way to create a new container image is by importing or loading it from a file.</h4>
- A container image is nothing more than a tarball.
** In computing, tar is a computer software utility for collecting many files into one archive file, often referred to as a tarball, for distribution or backup purposes.
