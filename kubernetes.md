
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



# Kubernetes Documentation (Continued)

## 7. What Is Kubelet?

Kubelet is a Kubernetes node agent that runs on every worker node. It communicates with the Kubernetes API Server and ensures that the assigned Pods and their containers are running properly.

- It runs on every worker node.
- It communicates with the Kubernetes API Server.
- It receives Pod specifications assigned to its node.
- It ensures that containers are running according to the Pod specification.
- It monitors the health of Pods and containers.
- It reports node and Pod status to the API Server.
- It works with the container runtime to manage containers.

**Example:**

Suppose Kubernetes schedules a Pod on Worker Node 1.

1. The API Server stores the Pod information.
2. Kubelet on Worker Node 1 receives the Pod specification.
3. Kubelet instructs the container runtime to start the container.
4. Kubelet monitors the Pod and reports its status.

## 8. What Is a Pod?

A Pod is the smallest deployable unit in Kubernetes. It represents one or more containers that share network resources and can share storage volumes.

- It is the smallest deployable unit in Kubernetes.
- It can contain one or multiple containers.
- Containers inside the same Pod share the same network namespace.
- Containers inside a Pod can communicate using localhost.
- Containers can share storage volumes.
- Every Pod receives its own IP address.
- Pods are generally ephemeral and can be replaced when they fail.

**Example:**

Create a Pod using the Nginx image.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```

Create the Pod:

```bash
kubectl apply -f pod.yaml
```

Check the Pod:

```bash
kubectl get pods
```

Describe the Pod:

```bash
kubectl describe pod nginx-pod
```

Delete the Pod:

```bash
kubectl delete pod nginx-pod
```

## 9. What Is a ReplicaSet?

A ReplicaSet is a Kubernetes resource used to maintain a specified number of identical Pod replicas running in a cluster.

- It maintains the desired number of Pod replicas.
- It automatically creates new Pods when existing Pods fail or are deleted.
- It deletes extra Pods when the number of replicas exceeds the desired count.
- It uses label selectors to identify and manage Pods.
- It helps maintain application availability.
- It is generally managed through Deployments rather than created directly.

**Example:**

Suppose you want to run three replicas of an Nginx application.

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-replicaset
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
```

Create the ReplicaSet:

```bash
kubectl apply -f replicaset.yaml
```

Check the ReplicaSet:

```bash
kubectl get replicasets
```

Check the Pods:

```bash
kubectl get pods
```

Scale the ReplicaSet:

```bash
kubectl scale replicaset nginx-replicaset --replicas=5
```

## 10. What Is a ReplicationController?

ReplicationController is a Kubernetes resource that ensures a specified number of Pod replicas are running at all times.

- It maintains the desired number of Pod replicas.
- It creates new Pods when existing Pods fail.
- It deletes extra Pods when more than the desired number are running.
- It uses label selectors to manage Pods.
- It helps maintain application availability.
- It is an older Kubernetes resource.
- ReplicaSet is its more advanced successor and supports set-based label selectors.

**Example:**

Create a ReplicationController with three Nginx Pods.

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: nginx-rc
spec:
  replicas: 3
  selector:
    app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
```

Create the ReplicationController:

```bash
kubectl apply -f replicationcontroller.yaml
```

Check the ReplicationController:

```bash
kubectl get replicationcontrollers
```

Scale the ReplicationController:

```bash
kubectl scale replicationcontroller nginx-rc --replicas=5
```

**Note:** ReplicationController is an older resource. In modern Kubernetes applications, Deployments and ReplicaSets are preferred.

## 11. What Is a Deployment?

A Deployment is a Kubernetes resource used to manage stateless application workloads and control the lifecycle of Pods through ReplicaSets.

- It manages ReplicaSets automatically.
- It maintains the desired number of Pod replicas.
- It supports rolling updates.
- It supports application rollbacks.
- It allows scaling of applications.
- It automatically replaces failed Pods through its ReplicaSets.
- It helps deploy new application versions with minimal downtime.
- It is commonly used for stateless applications such as Node.js, Java, and Nginx services.

**Example:**

Create a Deployment with three Nginx replicas.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.27
          ports:
            - containerPort: 80
```

Create the Deployment:

```bash
kubectl apply -f deployment.yaml
```

Check the Deployment:

```bash
kubectl get deployments
```

Check the ReplicaSets:

```bash
kubectl get replicasets
```

Check the Pods:

```bash
kubectl get pods
```

Scale the Deployment:

```bash
kubectl scale deployment nginx-deployment --replicas=5
```

Update the application image:

```bash
kubectl set image deployment/nginx-deployment nginx=nginx:1.28
```

Check rollout status:

```bash
kubectl rollout status deployment/nginx-deployment
```

Rollback to the previous version:

```bash
kubectl rollout undo deployment/nginx-deployment
```

## 12. What Is a DaemonSet?

A DaemonSet is a Kubernetes resource that ensures a copy of a specific Pod runs on every eligible node in the cluster.

- It automatically creates Pods on eligible worker nodes.
- It ensures that each eligible node runs the required Pod.
- It automatically creates Pods when new eligible nodes join the cluster.
- It removes the corresponding Pods when nodes are no longer eligible.
- It is commonly used for monitoring, logging, and networking agents.
- It is useful for node-level services.
- It can use node selectors, affinity, and tolerations to control where Pods run.

**Example:**

Suppose you have three worker nodes and want to run a monitoring agent on every worker node.

A DaemonSet ensures that one monitoring agent Pod runs on each eligible worker node.

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: monitoring-agent
spec:
  selector:
    matchLabels:
      app: monitoring-agent
  template:
    metadata:
      labels:
        app: monitoring-agent
    spec:
      containers:
        - name: monitoring-agent
          image: busybox:1.36
          command: ["sh", "-c", "while true; do sleep 3600; done"]
```

Create the DaemonSet:

```bash
kubectl apply -f daemonset.yaml
```

Check the DaemonSet:

```bash
kubectl get daemonsets
```

Check the Pods:

```bash
kubectl get pods -o wide
```

Delete the DaemonSet:

```bash
kubectl delete daemonset monitoring-agent
```

**Real-world use cases:**

- Prometheus Node Exporter for node monitoring.
- Fluent Bit for collecting container logs.
- CNI networking agents for node-level networking.
- Security agents for monitoring node activity.

**Note:** A DaemonSet normally runs one Pod per eligible node, not necessarily every node. Node selectors, affinity, and taints can restrict placement.
