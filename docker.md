# Docker Documentation

## 1. What Is Docker?

Docker is an open-source platform used to build, package, and run applications inside containers.

- It helps developers package applications with their dependencies.
- It makes applications portable across different environments.
- It simplifies application deployment.
- It provides isolation between applications.
- It supports microservices architecture.
- It helps maintain consistency between development, testing, and production environments.

**Example:** A Node.js application can be packaged with its dependencies into a Docker image and run on different servers.

## 2. What Is a Container?

A container is a lightweight, isolated environment used to run an application.

- It contains application code and required dependencies.
- It shares the host operating system kernel.
- It provides process and filesystem isolation.
- It starts faster than traditional virtual machines.
- Multiple containers can run on the same host.
- Containers can be started, stopped, and removed independently.

**Example:**

```bash
docker run -d --name my-container nginx
```

This command creates and starts an Nginx container.

## 3. What Are Docker Features?

Docker provides several important features:

- **Portability:** Applications can run across different supported environments.
- **Lightweight:** Containers generally consume fewer resources than virtual machines.
- **Isolation:** Applications run in isolated environments.
- **Scalability:** Multiple containers can run to handle application workloads.
- **Versioning:** Docker images can have different versions using tags.
- **Networking:** Containers can communicate through Docker networks.
- **Storage:** Docker volumes provide persistent data storage.
- **Automation:** Docker integrates with CI/CD pipelines.

## 4. History of Docker

Docker was introduced in 2013.

- Docker was initially developed by dotCloud.
- Solomon Hykes was one of its original creators.
- Docker was initially based on Linux container technologies.
- Docker became popular by simplifying container creation and management.
- It helped make containerization accessible to developers.
- Docker is widely used in modern DevOps and cloud-native environments.

## 5. What Is the Usage of Docker?

Docker is used in different stages of software development and deployment.

- Running applications inside containers.
- Packaging applications with dependencies.
- Creating development and testing environments.
- Building CI/CD pipelines.
- Deploying microservices.
- Running applications on cloud servers.
- Managing application environments.
- Supporting continuous integration and continuous deployment.

**Real-world example:**

A developer creates a Node.js application, builds a Docker image, pushes it to Docker Hub, and deploys it on an AWS EC2 server.

## 6. What Is Docker Architecture?

Docker follows a client-server architecture.

Its main components are:

1. Docker Client
2. Docker Daemon
3. Docker Images
4. Docker Containers
5. Docker Registry

- Docker Client sends commands to Docker Daemon.
- Docker Daemon manages Docker objects.
- Docker Images are used to create containers.
- Docker Containers run applications.
- Docker Registry stores and distributes Docker images.

**Example:**

```bash
docker pull nginx
docker run -d -p 8080:80 nginx
```

The Docker client sends these commands to the Docker daemon, which performs the requested operations.

<img width="1009" height="527" alt="image" src="https://github.com/user-attachments/assets/3c79305a-c632-428d-99c2-3eb079ce9047" />


## 7. What Are Docker Editions?

Docker provides different products and distribution options.

**1. Docker Desktop**

- Provides a graphical interface for working with Docker.
- Available for supported desktop operating systems.
- Includes tools for building and running containers.
- Commonly used by developers on laptops.

**2. Docker Engine**

- The core container platform.
- Used to build and run containers.
- Commonly installed on Linux servers.

**3. Docker Hub**

- A cloud-based image registry.
- Used to store and share Docker images.
- Supports public and private repositories.

Note: Docker Engine and Docker Desktop are different products, while Docker Hub is an image registry.

## 8. Docker System Requirements

Docker system requirements depend on the operating system and installation method.

General requirements include:

- Supported 64-bit operating system.
- Compatible Linux kernel for Docker Engine on Linux.
- Sufficient CPU and RAM.
- Internet connection for downloading images.
- Required virtualization support for Docker Desktop on supported platforms.
- Administrative privileges for installation and configuration.
- Available disk space for images and containers.

**Example:**

Check Ubuntu operating system information:

```bash
cat /etc/os-release
```

Check CPU information:

```bash
lscpu
```

Check available memory:

```bash
free -h
```

Check disk space:

```bash
df -h
```

## 9. Docker Installation and Setup

```bash
  sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

```
## 10. How to Verify Docker Installation?

After installing Docker, verify whether it is working correctly.

**Check Docker service:**

```bash
sudo systemctl status docker
```

**Check Docker version:**

```bash
docker --version
```

**Run a test container:**

```bash
sudo docker run hello-world
```

Expected result:

```text
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

**Check running containers:**

```bash
sudo docker ps
```

If the test container runs successfully, Docker is working.

## 11. About Docker Version

The Docker version command displays information about the installed Docker client and server.

**Command:**

```bash
docker version
```

It displays:

- Client Version
- Server Version
- API Version
- Go Version
- Operating System
- Architecture

**Check only the Docker client version:**

```bash
docker --version
```

**Display detailed Docker system information:**

```bash
docker info
```

**Difference:**

- `docker --version` displays a short version string.
- `docker version` displays client and server version details.
- `docker info` displays detailed Docker Engine information.

## 12. What Is OS-Level Virtualization?

OS-level virtualization is a technology that allows multiple isolated environments to run using the same operating system kernel.

- Containers share the host operating system kernel.
- Each container runs isolated processes.
- Containers use fewer resources than traditional virtual machines.
- Containers can run different applications independently.
- Linux namespaces provide isolation.
- Linux cgroups help manage and limit resources.

**Example:**

One Ubuntu server can run multiple containers:

- Nginx container
- MySQL container
- Node.js container
- Redis container

All these containers share the host Linux kernel.

<img width="678" height="294" alt="image" src="https://github.com/user-attachments/assets/bdf0c349-590f-4387-a1f6-4a63a68d6ce7" />


## 13. What Is a Layered File System?

Docker uses a layered filesystem to build and manage images efficiently.

- Docker images consist of multiple read-only layers.
- Each Dockerfile instruction that changes the filesystem can create a new layer.
- Layers can be shared between images.
- Docker uses storage drivers to manage image layers.
- Containers add a writable layer on top of the image layers.
- Changes in the writable layer are normally lost when the container is removed.

**Example Dockerfile:**

```dockerfile
FROM ubuntu:24.04

RUN apt update

RUN apt install -y nginx

CMD ["nginx", "-g", "daemon off;"]
```

Here, Docker builds the image using a base image and additional filesystem changes.

## 14. VMware vs Docker

VMware virtual machines and Docker containers provide different approaches to running isolated workloads.

| VMware Virtual Machine | Docker Container |
|---|---|
| Uses virtual machines | Uses containers |
| Runs a guest operating system | Shares the host kernel |
| Requires more resources generally | Usually requires fewer resources |
| Has a virtual hardware layer | Uses OS-level isolation |
| Generally takes longer to start | Generally starts faster |
| Provides a separate OS environment | Provides an isolated application environment |

<img width="678" height="294" alt="image" src="https://github.com/user-attachments/assets/d2d43ebd-208c-4589-90b5-eba7bc7caf28" />


**VMware use case:**

Running a separate Windows operating system on a Linux host.

**Docker use case:**

Running Nginx, MySQL, and Node.js applications inside separate containers on one Linux server.

## 15. What Are Docker Components?

Docker consists of several important components.

**1. Docker Client**

- Provides the command-line interface.
- Accepts commands from users.
- Communicates with Docker Daemon through the Docker API.

**2. Docker Daemon**

- Runs in the background.
- Manages images, containers, networks, and volumes.
- Receives requests from Docker Client.

**3. Docker Images**

- Read-only templates.
- Used to create containers.
- Contain application code and dependencies.

**4. Docker Containers**

- Instances of Docker images.
- Run applications in isolated environments.

**5. Docker Registry**

- Stores Docker images.
- Allows users to upload and download images.
- Example: Docker Hub.

**6. containerd**

- Manages container lifecycle operations.
- Works with Docker Engine.

**7. runc**

- A low-level container runtime.
- Creates and runs containers according to OCI specifications.

  <img width="1009" height="527" alt="image" src="https://github.com/user-attachments/assets/a9bfc34d-03ce-47c8-ad40-b82de8523f75" />


## 16. What Is Docker Workflow?

Docker workflow explains how an application moves from development to execution.

**Step 1: Write application code**

A developer creates an application.

**Step 2: Create a Dockerfile**

The Dockerfile contains instructions for building the image.

**Step 3: Build a Docker image**

```bash
docker build -t myapp:v1 .
```

**Step 4: Check available images**

```bash
docker images
```

**Step 5: Run a container**

```bash
docker run -d --name myapp-container myapp:v1
```

**Step 6: Check running containers**

```bash
docker ps
```

**Step 7: Push the image to a registry**

```bash
docker push username/myapp:v1
```

**Step 8: Download the image on another server**

```bash
docker pull username/myapp:v1
```

The application can now run on another machine using the same image.

## 17. What Are the Benefits of Docker?

Docker provides several benefits in software development and deployment.

- **Portability:** Applications can run across different supported environments.
- **Consistency:** Reduces differences between development and production.
- **Efficiency:** Containers generally use fewer resources than full virtual machines.
- **Scalability:** Multiple application containers can run simultaneously.
- **Isolation:** Applications run in separate environments.
- **Faster deployment:** Containers can start quickly.
- **CI/CD integration:** Docker works with modern automation tools.
- **Version management:** Different application image versions can be maintained.

## 18. What Is a Docker Image?

A Docker image is a read-only template used to create containers.

- It contains application code.
- It includes required dependencies.
- It contains filesystem layers.
- It defines default execution configuration.
- Multiple containers can be created from the same image.
- Images can be stored in Docker Hub or private registries.

**Example commands:**

Download Nginx image:

```bash
docker pull nginx
```

List images:

```bash
docker images
```

Run a container:

```bash
docker run -d --name web-server nginx
```

## 19. What Is a Docker Container?

A Docker container is a running or stopped instance of a Docker image.

- Containers execute applications.
- Containers provide application isolation.
- Containers have a writable layer.
- Containers can be started and stopped.
- Containers can communicate through Docker networks.
- Persistent data can be stored using volumes.

**Example:**

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Check the container:

```bash
docker ps
```

Access the application:

```text
http://SERVER-IP:8080
```

## 20. What Is a Dockerfile?

A Dockerfile is a text file containing instructions used to build a Docker image.

It defines:

- Base image.
- Working directory.
- Application files.
- Dependencies.
- Environment variables.
- Exposed ports.
- Default startup command.

**Example Dockerfile:**

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

Build the image:

```bash
docker build -t my-node-app .
```

Run the container:

```bash
docker run -d -p 3000:3000 my-node-app
```

## 21. What Is Docker Hub / Registry?

A Docker Registry is a service used to store and distribute Docker images.

Docker Hub is one of the most popular public Docker registries.

- Developers can upload Docker images.
- Other developers can download images.
- Public repositories allow image sharing.
- Private repositories restrict image access.
- Images can be organized using repositories and tags.
- Organizations can use private registries for internal applications.

**Examples of Docker registries:**

- Docker Hub
- Amazon Elastic Container Registry (ECR)
- GitLab Container Registry
- Google Artifact Registry
- Azure Container Registry

**Example:**

Download an Nginx image:

```bash
docker pull nginx
```

Upload your own image:

```bash
docker tag myapp:v1 username/myapp:v1

docker push username/myapp:v1
```

## 22. What Is Docker Daemon?

Docker Daemon is a background service responsible for managing Docker objects.

It is commonly called `dockerd`.

Its responsibilities include:

- Building Docker images.
- Creating and running containers.
- Managing Docker networks.
- Managing Docker volumes.
- Communicating with registries.
- Managing container lifecycle operations.

**Check Docker daemon status:**

```bash
sudo systemctl status docker
```

**Start Docker daemon:**

```bash
sudo systemctl start docker
```

**Stop Docker daemon:**

```bash
sudo systemctl stop docker
```

**Enable Docker at system startup:**

```bash
sudo systemctl enable docker
```

Docker Client communicates with Docker Daemon through the Docker API.


# Docker Documentation (Continued)

## 22. What Are Docker Volumes?

Docker volumes are used to store data permanently outside the container's writable layer.

- Volumes help preserve data even after a container is removed.
- Volumes are managed by Docker.
- Multiple containers can share the same volume.
- Volumes are useful for databases and application data.
- They provide persistent storage for containers.

**Create a volume:**

```bash
docker volume create mydata
```

**List volumes:**

```bash
docker volume ls
```

**Inspect a volume:**

```bash
docker volume inspect mydata
```

**Use a volume inside a container:**

```bash
docker run -d \
--name my-container \
-v mydata:/data \
nginx
```

## 23. Volume (Container-to-Container)

Docker allows multiple containers to access the same volume.

- Both containers can access shared data.
- Changes made by one container can be visible to the other.
- It is useful when multiple applications need access to the same files.
- Both containers must mount the volume at an appropriate path.

**Step 1: Create a shared volume**

```bash
docker volume create shared-data
```

**Step 2: Run the first container**

```bash
docker run -dit \
--name container1 \
-v shared-data:/data \
alpine sh
```

**Step 3: Run the second container**

```bash
docker run -dit \
--name container2 \
-v shared-data:/data \
alpine sh
```

**Step 4: Create a file in the first container**

```bash
docker exec container1 sh -c \
"echo Hello from Container 1 > /data/demo.txt"
```

**Step 5: Read the file from the second container**

```bash
docker exec container2 cat /data/demo.txt
```

Expected output:

```text
Hello from Container 1
```

Both containers are accessing the same Docker volume.

## 24. Volume (Host-to-Container)

Host-to-container storage allows you to connect a directory from your host machine to a directory inside a container.

This is commonly implemented using a Docker bind mount.

- Host directory is connected to a container directory.
- Changes made on the host can be reflected inside the container.
- It is useful for development environments.
- Developers can edit application files on the host without rebuilding the image.

**Example:**

```bash
docker run -d \
--name nginx-server \
-p 8080:80 \
-v /home/ubuntu/html:/usr/share/nginx/html \
nginx
```

Explanation:

- `/home/ubuntu/html` is the host directory.
- `/usr/share/nginx/html` is the container directory.
- Nginx reads website files from the mounted directory.

**Create a test HTML file on the host:**

```bash
mkdir -p /home/ubuntu/html

echo "<h1>Hello Docker</h1>" > /home/ubuntu/html/index.html
```

Open in your browser:

```text
http://SERVER-IP:8080
```

## 25. What Is Port Mapping?

Port mapping connects a port on the host machine to a port inside a Docker container.

- It allows external users to access applications running inside containers.
- It connects host ports with container ports.
- It is commonly used for web applications and APIs.
- Docker uses the `-p` option for port mapping.

**Syntax:**

```bash
docker run -d -p HOST_PORT:CONTAINER_PORT IMAGE
```

**Example:**

```bash
docker run -d \
--name my-nginx \
-p 8090:80 \
nginx
```

Explanation:

- `8090` is the host port.
- `80` is the container port.
- `nginx` is the Docker image.

Access the application:

```text
http://SERVER-IP:8090
```

**Check mapped ports:**

```bash
docker port my-nginx
```

## 26. What Is a Registry Server?

A Docker Registry is a service used to store, manage, and distribute Docker images.

- Developers can upload Docker images.
- Other developers can download Docker images.
- Registries support public and private repositories.
- Organizations use private registries to store internal application images.
- Docker Hub is a popular public registry.

**Examples of Docker registries:**

1. Docker Hub
2. Amazon Elastic Container Registry (ECR)
3. GitLab Container Registry
4. Azure Container Registry
5. Google Artifact Registry

**Example:**

```bash
docker pull nginx
```

This downloads the Nginx image from the default Docker Hub registry.

## 27. How to Pull and Push Images From/To a Registry?

Docker provides `pull` and `push` commands to download and upload images.

**Docker Pull:**

Downloads an image from a registry to your local machine.

```bash
docker pull nginx
```

Download a specific version:

```bash
docker pull nginx:alpine
```

**Docker Push:**

Uploads a local image to a registry.

**Step 1: Login to Docker Hub**

```bash
docker login
```

**Step 2: Tag your image**

```bash
docker tag myapp:v1 username/myapp:v1
```

**Step 3: Push the image**

```bash
docker push username/myapp:v1
```

Replace `username` with your actual Docker Hub username.

**Step 4: Verify the image**

Check your Docker Hub repository to confirm the image was uploaded.

## 28. What Is CMD in Dockerfile?

`CMD` is a Dockerfile instruction used to specify the default command or arguments that execute when a container starts.

- It provides the default execution behavior.
- It can be overridden when running a container.
- A Dockerfile should generally have one effective CMD instruction.
- It supports shell form and exec form.

**Example:**

```dockerfile
FROM ubuntu:24.04

CMD ["echo", "Hello from Docker CMD"]
```

Build the image:

```bash
docker build -t cmd-demo .
```

Run the container:

```bash
docker run cmd-demo
```

Output:

```text
Hello from Docker CMD
```

**Override CMD:**

```bash
docker run cmd-demo echo "New command"
```

Output:

```text
New command
```

## 29. What Is RUN in Dockerfile?

`RUN` is a Dockerfile instruction used to execute commands while building a Docker image.

- It executes commands during image building.
- It is commonly used to install packages.
- It can create directories and files.
- Filesystem changes are included in image layers.
- It does not execute every time the container starts.

**Example:**

```dockerfile
FROM ubuntu:24.04

RUN apt update

RUN apt install -y nginx

RUN mkdir /myapp

CMD ["nginx", "-g", "daemon off;"]
```

Build the image:

```bash
docker build -t run-demo .
```

The `RUN` instructions execute during the image build process.

## 30. What Is ENTRYPOINT in Dockerfile?

`ENTRYPOINT` is a Dockerfile instruction used to configure the main executable that runs when a container starts.

- It defines the main application or executable.
- It is commonly used for containers that run a specific application.
- Runtime arguments are passed to the entrypoint.
- It can be written in exec form or shell form.

**Example:**

```dockerfile
FROM ubuntu:24.04

ENTRYPOINT ["echo"]

CMD ["Hello from Docker"]
```

Build the image:

```bash
docker build -t entrypoint-demo .
```

Run the container:

```bash
docker run entrypoint-demo
```

Output:

```text
Hello from Docker
```

Override the default argument:

```bash
docker run entrypoint-demo "Hello Danish"
```

Output:

```text
Hello Danish
```

## 31. Relationship Between Docker and Containers

Docker is a platform used to build, manage, and run containers.

A container is one of the main objects managed by Docker.

- Docker provides tools to create containers.
- Docker images are used as templates for containers.
- Docker manages container lifecycle operations.
- Containers run applications in isolated environments.
- Docker manages container networking and storage.

**Simple example:**

Docker is like a vehicle management system, while a container is like an individual vehicle managed by that system.

**Command:**

```bash
docker run -d --name web nginx
```

This command uses Docker to create and start a container.

## 32. Why Is Docker So Popular?

Docker became popular because it simplified application packaging, deployment, and portability.

- **Portability:** Applications can run across supported environments.
- **Lightweight:** Containers generally use fewer resources than virtual machines.
- **Consistency:** Applications behave more consistently across environments.
- **Faster deployment:** Containers can start quickly.
- **Scalability:** Multiple containers can run together.
- **CI/CD integration:** Docker works with Jenkins, GitLab CI, and GitHub Actions.
- **Microservices support:** Each application service can run in its own container.
- **Cloud integration:** Docker works with AWS, Azure, and Google Cloud.

## 33. Difference Between Docker Image and Container

A Docker image is a template used to create containers.

A Docker container is an instance of an image.

| Docker Image | Docker Container |
|---|---|
| Read-only template | Running or stopped instance |
| Used to create containers | Used to run applications |
| Contains application and dependencies | Executes the application |
| Can create multiple containers | Created from an image |
| Stored in image layers | Has a writable layer |

**Example:**

```bash
docker pull nginx
```

This downloads an image.

```bash
docker run -d --name web nginx
```

This creates and starts a container using that image.

## 34. Docker Images

Docker images are templates used to create Docker containers.

- Images contain application code and dependencies.
- Images are built using Dockerfiles.
- Images consist of filesystem layers.
- Images can be downloaded from registries.
- Images can have different versions using tags.
- Multiple containers can use the same image.

**List images:**

```bash
docker images
```

**Pull an image:**

```bash
docker pull nginx
```

**Inspect an image:**

```bash
docker inspect nginx
```

**Remove an image:**

```bash
docker rmi nginx
```

## 35. What Is Docker PS?

`docker ps` is used to display running Docker containers.

- It displays running containers by default.
- It shows container IDs.
- It shows image names.
- It displays container status.
- It displays port mappings and container names.

**Display running containers:**

```bash
docker ps
```

**Display all containers, including stopped containers:**

```bash
docker ps -a
```

**Display only container IDs:**

```bash
docker ps -q
```

**Display the latest created container:**

```bash
docker ps -l
```

## 36. What Is Docker TOP?

`docker top` displays the running processes inside a container.

- It shows processes associated with a container.
- It helps administrators inspect running applications.
- It is useful for troubleshooting.
- It displays process information from the host's process view.

**Syntax:**

```bash
docker top CONTAINER_NAME
```

**Example:**

```bash
docker run -d --name my-nginx nginx
```

Check running processes:

```bash
docker top my-nginx
```

## 37. What Is Docker LOGS?

`docker logs` is used to display logs generated by a container's main process.

- It helps troubleshoot application problems.
- It displays standard output and standard error.
- It helps identify application errors.
- It supports real-time log monitoring.

**Display container logs:**

```bash
docker logs my-nginx
```

**Display the latest 50 lines:**

```bash
docker logs --tail 50 my-nginx
```

**Follow logs in real time:**

```bash
docker logs -f my-nginx
```

**Display timestamps:**

```bash
docker logs -t my-nginx
```

## 38. What Is Docker RMI?

`docker rmi` is used to remove one or more Docker images from the local machine.

- It removes local Docker images.
- It helps free disk space.
- It does not directly remove a running container.
- An image cannot normally be removed while a container depends on it unless the relevant container is removed first.

**Syntax:**

```bash
docker rmi IMAGE_NAME
```

**Example:**

```bash
docker images
docker rmi nginx
```

Remove an image using its ID:

```bash
docker rmi IMAGE_ID
```

## 39. What Is Docker RM?

`docker rm` is used to remove one or more stopped containers.

- It removes containers from the Docker host.
- It removes the container's writable layer.
- It does not remove the Docker image.
- It does not automatically remove named volumes.

**Syntax:**

```bash
docker rm CONTAINER_NAME
```

**Example:**

```bash
docker stop my-nginx

docker rm my-nginx
```

Remove a stopped container forcefully:

```bash
docker rm -f my-nginx
```

**Difference:**

- `docker rm` removes containers.
- `docker rmi` removes images.

## 40. What Is Docker Pull?

`docker pull` downloads an image from a Docker registry to the local machine.

- It downloads images from Docker Hub by default.
- It supports specific image tags.
- It allows developers to obtain application images.
- It downloads image layers that are not already present locally.

**Download Nginx:**

```bash
docker pull nginx
```

**Download a specific version:**

```bash
docker pull nginx:alpine
```

**Verify downloaded images:**

```bash
docker images
```

## 41. What Is Docker Search?

`docker search` is used to search for Docker images on Docker Hub.

- It searches for public images.
- It displays repository names.
- It displays descriptions.
- It can show image stars and official-image information.
- It helps developers find images.

**Search for Nginx:**

```bash
docker search nginx
```

**Search for Ubuntu:**

```bash
docker search ubuntu
```

**Limit search results:**

```bash
docker search --limit 5 nginx
```

After finding an image, download it using:

```bash
docker pull nginx
```

