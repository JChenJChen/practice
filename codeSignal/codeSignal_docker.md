# CODESIGNAL COURSE PATH "Mastering Docker: Containers, Networking, and Orchestration" NOTES

- https://codesignal.com/learn/paths/complete-docker-mastery-path
- https://codesignal.com/learn/courses/docker-images-containers

5 Courses:
1. [Docker Images & Containers](https://codesignal.com/learn/courses/docker-images-containers)  -- 5 lessons
2. [Diving Deeper into Images & Containers](https://codesignal.com/learn/courses/diving-deeper-into-images-containers)  -- 5 lessons
3. [Managing Data & Working with Volumes](https://codesignal.com/learn/courses/managing-data-working-with-volumes)  -- 4 lessons
4. [Networking and Cross-Container Communication](https://codesignal.com/learn/courses/networking-and-cross-container-communication)  -- 5 lessons
5. [Multi-Container Orchestration with Docker Compose](https://codesignal.com/learn/courses/multi-container-orchestration-with-docker-compose)  -- 5 lessons

## Misc Notes

- 


## Course 1. Docker Images & Containers

### [Unit 1: Introduction to Docker and Containerization](https://codesignal.com/learn/courses/docker-images-containers/lessons/introduction-to-docker-and-containerization)

- docker image: code, runtime, libraries, settings. can create multiple containers
- docker container: running instance of docker image. Executes applications in isolated environments from host.
- docker vs VM:
  - VM: 
    - full copy of OS, application, necessary binaries, and libraries -- heavier and requiring more resources
    - run on a hypervisor that emulates hardware for each VM -- allowing multiple VMs to run on a single physical machine. 
    - This offers strong isolation but at the cost of performance and efficient resource usage.
  - Docker Containers: 
    - share host system's OS kernel -- much lighter and faster to start.
    - package the application and dependencies, but do not include an entire OS, relying instead on features provided by the host OS
    - faster performance and more efficient resource utilization compared to VMs.
    - especially suited for cloud-native and distributed apps where quick scaling and portability across envs are critical
- Docker setup:
  - install docker desktop: includes Docker Engine, Docker CLI, Docker Compose, GUI, and other essential components. Everything needed to develop, test, and manage containers.
    - Docker Daemon (or dockerd):
      - background service running on host system, manages Docker objects (images, containers, networks, volumes). 
      - listens for API requests both from CLI and other tools, to build, run, and manage Docker containers.
      - responds to Docker CLI cmds to facilitate the overall Docker workflow.
    - Docker Engine: client-server application that includes: the server (Docker Daemon), a REST API, and the client (Docker CLI).
      - REST API manages communication between client and server, container management tasks such as building, running, and distributing Docker containers.

```sh
docker run hello-world
docker images
docker ps # list running containers
docker ps -a # list all running containers, including stopped
```

### [Unit 2: Step-by-Step Container Management](https://codesignal.com/learn/courses/docker-images-containers/lessons/step-by-step-container-management)

- docker hub, popular images: Nginx, MySQL, Redis, Node.js, Ubuntu
- docker run: pull, create, start
- docker pull
- docker create: creates container WITHOUT starting
```sh
# Pulling an external Docker image from Docker Hub
docker pull nginx

docker create --name my-nginx nginx # --name optional, randomly assigns name if omitted
# container ID to stdout: c49adf897b2a74bcbed915a76eea458b19eae8afa4a71e9b007eb9dbb3723c89
```
- docker start & stop:
```sh
# Option 1: Start the container using the name
docker start my_nginx # or docker stop
# Output: my_nginx

# Option 2: Start the container using the container ID
docker start c49adf897b2a # or docker stop
# Output: c49adf897b2a

# Option 1: Stop the container using the name
docker stop my-nginx
# Output: my-nginx

# Option 2: Stop the container using the container ID
docker stop c49adf897b2a
# Output: c49adf897b2a

docker run --name my-nginx nginx
# ctrl+C to stop
```

### Unit 3: Building Custom Images with Dockerfile

- convention is to place Dockerfile at project root dir.
- more effective caching: less frequently changed layers at top, more frequent at bottom.

#### Basic Syntax of a Dockerfile

- `FROM`: base image. Always in beginning.
- `RUN`: executes instructions (only once) during image build to set up app env. Ex: install software, apply system updates.
  - merge similar steps into a single RUN cmd to minimize layers & size.
- `COPY`: moves files from host machine to image's filesystem.
- `CMD`: default cmd to run when container starts/launches.

Example Dockerfile contents:
```Dockerfile
# Use the official nginx image as the base image
FROM nginx:1.27.2

# Run an update using the package manager
RUN apt-get update

# Copy custom HTML file to the default nginx directory
COPY index.html /usr/share/nginx/html/

# Set the default command to run when starting the container
CMD ["nginx", "-g", "daemon off;"] 
# -g: stay active in foreground instead of running in background, to keep container running & responsive
# semi-colon at end of CMD not always necessary
```

#### Building Your Custom Image

```sh
# Build custom image from Dockerfile
docker build -t custom-nginx .
```

### Unit 4: Executing Containers with Custom Port Mapping

```Dockerfile
# Expose port 80
EXPOSE 80
```

```sh
docker create --name my-nginx -p 8080:80 custom-nginx
docker start my-nginx

# Run the first container, mapping its port 80 to host port 8080
docker run -p 8080:80 custom-nginx
# NOTE: host port: container port

# Run the second container, mapping its port 80 to host port 8081
docker run -p 8081:80 custom-nginx
```

### Unit 5: Mastering Attached and Detached Modes

- attached mode: stdin, stdout, stderr in terminal

- detached mode, container:
  - works silently in background
  - no container output in terminal, but
  - will receive confirmation message in stdout, i.e.: container ID: `884fda246c7aec578f8476c6d96a602f518eda6869047c08ecf2560bfda92d78`


```sh

# Run a container in attached mode (default)
docker run nginx

# Run a container in detached mode
docker run -d nginx

# Start an existing container in detached mode (default)
docker start <container-id-or-name>

# Start an existing container in attached mode
docker start -a <container-id-or-name>

# View logs of a container identified by container ID or name
docker logs <container-id-or-name>
# ex: docker logs my-nginx

# Continuously monitor logs in real-time
docker logs -f <container-id-or-name>

# Start an existing container in attached mode
docker start -a <container-id-or-name>

# Run a container in detached mode with port mapping and a specific name
docker run -d -p 8080:80 --name my-nginx nginx

```

## Course 2. Diving Deeper into Images & Containers

### [Unit 1. Explore Interactive Container Mode with Docker](https://codesignal.com/learn/courses/diving-deeper-into-images-containers/lessons/explore-interactive-container-mode-with-docker)

#### Starting an Existing Container in Interactive Mode

- `docker start -ai command`: restart stopped container that was initially created in interactive mode and work with it interactively again
  - `-a` flag: enables seeing output, attaches to container's stdout and stderr.
  - `-i` flag: keeps stdin open for interactive input.

### [Unit 2. Deleting Images and Containers](https://codesignal.com/learn/courses/diving-deeper-into-images-containers/lessons/deleting-images-and-containers)

#### Removing Containers

```sh
# Remove a stopped container
docker rm ubuntu-container

# output: if successful: returns container name in stout
# will error if container still running. Stop container to fix 
```

#### Removing Images

```sh
# Remove an image that's not being used
docker rmi ubuntu
```

- will error if image is being used by container &rarr; remove dependent container then `rmi`

#### Forcing Removal with the -f / --force Flag

```sh
# Forcefully remove a running container or one w/ dependencies
docker rm -f ubuntu-container
```

```sh
# Forcefully delete a referenced image
docker rmi -f ubuntu
```

## Course 3. Managing Data & Working with Volumes



## Course 4. Networking and Cross-Container Communication



## Course 5. Multi-Container Orchestration with Docker Compose


