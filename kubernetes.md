
# Kubernetes Documentation

## 1. What Is Kubernetes?

Kubernetes (K8s) is an open-source container orchestration platform used to automate the deployment, scaling, and management of containerized applications.

- It helps manage multiple containers across multiple servers.
- It automates application deployment and scaling.
- It provides automatic container recovery (self-healing).
- It distributes application workloads across multiple nodes.
- It manages container networking and service discovery.
- It supports rolling updates and rollbacks.
- It helps maintain application availability.
- It is widely used in DevOps and cloud-native environments.

**Example:**

Suppose you have a microservices application with multiple services such as User Service, Payment Service, and Order Service.

Kubernetes helps deploy, manage, scale, and monitor these services across multiple servers.

## 2. What Are the Features of Kubernetes?

Kubernetes provides several important features:

- **Container Orchestration:** Manages containers across multiple nodes.
- **Auto Scaling:** Automatically increases or decreases application replicas based on resource usage or other metrics.
- **Self-Healing:** Automatically restarts failed containers and replaces unhealthy Pods.
- **Load Balancing:** Distributes network traffic across application replicas.
- **Service Discovery:** Allows applications to communicate with each other using Service names.
- **Rolling Updates:** Updates applications gradually without requiring downtime in many cases.
- **Rollback:** Allows you to return to a previous application version.
- **Storage Orchestration:** Automatically mounts supported storage systems to containers.
- **Resource Management:** Controls CPU and memory allocation for containers.
- **Configuration Management:** Manages application configurations and sensitive information using ConfigMaps and Secrets.

**Example:**

If an application has three replicas and one Pod crashes, Kubernetes can create a replacement Pod to maintain the desired replica count.

## 3. What Is Kubernetes Architecture?

Kubernetes follows a control-plane and worker-node architecture.

Its architecture consists of two major parts:

1. Control Plane (Master Node)
2. Worker Nodes

- The Control Plane manages the overall Kubernetes cluster.
- Worker Nodes run containerized applications.
- The API Server provides the communication interface for Kubernetes.
- The Scheduler assigns Pods to suitable worker nodes.
- The Controller Manager maintains the desired cluster state.
- Kubelet manages Pods on worker nodes.
- Container Runtime runs containers.
- Kube-proxy manages Service networking rules on worker nodes.

**Example:**

When you deploy an application using a Kubernetes Deployment, the Control Plane processes the request and schedules the Pods onto available worker nodes.

## 4. What Is Kubernetes Master (Control Plane)?

The Kubernetes Master, officially called the Control Plane, manages and controls the Kubernetes cluster.

It is responsible for maintaining the desired state of the cluster.

Its main components are:

- **API Server:** Exposes the Kubernetes API and handles communication between cluster components.
- **etcd:** Stores Kubernetes cluster data and configuration.
- **Scheduler:** Selects suitable worker nodes for newly created Pods.
- **Controller Manager:** Runs controllers that monitor and maintain the desired state of the cluster.
- **Cloud Controller Manager:** Integrates Kubernetes with cloud provider services when required.

**Example:**

When you create a Deployment with three replicas, the Control Plane ensures that Kubernetes schedules and maintains three application Pods.

## 5. What Are Kubernetes Nodes?

A Kubernetes Node is a physical or virtual machine that runs containerized applications inside a Kubernetes cluster.

There are two types of nodes:

1. Control Plane Node
2. Worker Node

**Worker Node:**

Worker Nodes are responsible for running application workloads.

Their main components are:

- **Kubelet:** Communicates with the API Server and ensures that assigned Pods are running.
- **Kube-proxy:** Implements Kubernetes Service networking rules.
- **Container Runtime:** Runs containers, such as containerd or CRI-O.

**Example:**

Suppose your application has five Pods running across three worker nodes.

Kubernetes distributes these Pods across the available nodes according to scheduling requirements and resource availability.

## 6. What Are Kubernetes Components?

Kubernetes components are the individual services and processes responsible for managing the cluster and running containerized applications.

They are divided into two major categories:

### A. Control Plane Components

**1. API Server (kube-apiserver)**

- It is the main entry point for Kubernetes API requests.
- It processes requests from kubectl and other components.
- It validates and processes cluster resource configurations.
- It communicates with etcd to store and retrieve cluster data.

**2. etcd**

- It is a distributed key-value database.
- It stores Kubernetes cluster information.
- It maintains cluster configuration and state.
- It is important for Kubernetes cluster recovery and consistency.

**3. Scheduler (kube-scheduler)**

- It assigns newly created Pods to suitable worker nodes.
- It checks available CPU and memory resources.
- It considers scheduling constraints and policies.
- It selects the most suitable node for a Pod.

**4. Controller Manager (kube-controller-manager)**

- It runs different Kubernetes controllers.
- It continuously monitors the cluster state.
- It ensures the actual state matches the desired state.
- It manages controllers such as Node Controller and Deployment-related ReplicaSet controllers.

**5. Cloud Controller Manager (cloud-controller-manager)**

- It integrates Kubernetes with cloud platforms.
- It manages cloud resources such as load balancers.
- It can manage cloud networking and node information.
- It is mainly used in cloud-based Kubernetes environments.

### B. Worker Node Components

**1. Kubelet**

- It runs on every worker node.
- It communicates with the Kubernetes API Server.
- It ensures assigned Pods and containers are running.
- It monitors Pod health and reports node status.

**2. Kube-proxy**

- It runs on worker nodes.
- It maintains network rules for Kubernetes Services.
- It enables communication with Services.
- It can use iptables or IPVS, depending on the configuration.

**3. Container Runtime**

- It is responsible for running containers.
- It downloads container images.
- It starts and stops containers.
- Examples include containerd and CRI-O.

**Note:** Kubernetes uses the Container Runtime Interface (CRI) to communicate with supported container runtimes.

**Example:**

When you deploy a Pod:

1. API Server receives the deployment request.
2. Scheduler selects a suitable worker node.
3. Kubelet receives the Pod assignment.
4. Container Runtime downloads the image if necessary and starts the container.
5. Kube-proxy handles Service networking rules when required.

This is how Kubernetes components work together to run your applications.
