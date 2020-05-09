<h1>What’s the difference between Docker Engine and Docker Machine?</h1>

When people say “Docker” they typically mean **Docker Engine**, the client-server application made up of:
1) the Docker daemon
2) a REST API that specifies interfaces for interacting with the daemon
3) and a command line interface (CLI) client that talks to the daemon (through the REST API wrapper).

Docker Engine accepts docker commands from the CLI, such as docker run <image>, docker ps to list running containers, docker image ls to list images, and so on.


**Docker Machine** is a tool for provisioning and managing your Dockerized hosts (hosts with Docker Engine on them). Typically, you install Docker Machine on your local system. Docker Machine has its own command line client docker-machine and the Docker Engine client, docker. You can use Machine to install Docker Engine on one or more virtual systems. These virtual systems can be local (as when you use Machine to install and run Docker Engine in VirtualBox on Mac or Windows) or remote (as when you use Machine to provision Dockerized hosts on cloud providers). The Dockerized hosts themselves can be thought of, and are sometimes referred to as, managed “machines”.