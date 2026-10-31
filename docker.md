# Docker Documentation

## 1. What Is Docker?

Docker is an open-source platform used to build, package, and run applications inside containers.

- It makes applications portable.
- It packages applications with their dependencies.
- It helps developers run applications consistently across different environments.
- It simplifies application deployment.
- It supports microservices architecture.

## 2. What Is a Container?

A container is a lightweight, isolated environment used to run an application.

- Containers share the host operating system kernel.
- Each container has its own isolated processes and filesystem view.
- Containers start quickly.
- Containers use fewer resources than traditional virtual machines.

<img width="802" height="534" alt="image" src="https://github.com/user-attachments/assets/23ec2f66-6dfc-43f9-a4bc-f49f5586e5c7" />



## 3. What Are Docker Features?

- Lightweight application deployment.
- Portability across environments.
- Application isolation.
- Image versioning.
- Container networking.
- Persistent storage using volumes.
- Scalability and orchestration support.

## 4. What Is Docker Architecture?

Docker follows a client-server architecture.

Its main components are:

1. Docker Client
2. Docker Daemon
3. Docker Images
4. Docker Containers
5. Docker Registry

## 5. What Is a Docker Image?

A Docker image is a read-only template used to create containers.

- It contains application code.
- It includes required dependencies.
- It contains configuration instructions.
- Multiple containers can be created from the same image.

Example:

```bash
docker pull nginx
docker images
docker run -d -p 8080:80 nginx
```

## 6. What Is a Docker Container?

A Docker container is a running or stopped instance of a Docker image.

- Containers run applications.
- Containers provide isolation.
- Containers can be started, stopped, and removed.

Example:

```bash
docker ps
docker ps -a
docker stop container_name
docker start container_name
```

## 7. What Is a Dockerfile?

A Dockerfile is a text file containing instructions to build a Docker image.

Example:

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

Build the image:

```bash
docker build -t my-nginx .
```

Run the container:

```bash
docker run -d -p 8080:80 my-nginx
```
