# Jenkins Documentation

## 1. What Is Jenkins?

Jenkins is an open-source automation server used to automate software development processes, especially Continuous Integration (CI) and Continuous Delivery/Continuous Deployment (CD).

- It helps automate software build processes.
- It automates application testing.
- It supports Continuous Integration and Continuous Deployment.
- It integrates with version control systems such as Git and GitHub.
- It supports automated application deployment.
- It provides pipelines to define automation workflows.
- It supports plugins to extend its functionality.
- It helps reduce manual work in software development and deployment.
- It supports integration with Docker, Kubernetes, Ansible, Terraform, and cloud platforms.


## 2. Why Jenkins?

Jenkins is used to automate software development, testing, and deployment processes. It helps development and DevOps teams reduce manual work and deliver applications faster and more reliably.

- **Automation:** Automates repetitive tasks such as building, testing, and deploying applications.
- **Continuous Integration (CI):** Automatically integrates code changes from multiple developers into a shared repository.
- **Continuous Delivery (CD):** Automates the process of preparing applications for release.
- **Continuous Deployment:** Automatically deploys successfully tested application changes to production.
- **Time Saving:** Reduces manual effort and speeds up software delivery.
- **Error Reduction:** Reduces human errors by automating repetitive processes.
- **Integration:** Integrates with tools such as Git, GitHub, GitLab, Docker, Kubernetes, and Ansible.
- **Plugin Support:** Provides thousands of plugins to extend automation capabilities.
- **Monitoring:** Provides build history, pipeline status, and execution logs.
- **Scalability:** Supports distributed builds using multiple agents.



## 3. Relationship Between Jenkins and Hudson

Jenkins and Hudson are related because Jenkins was originally developed as a fork of the Hudson project.

- **Hudson:** Hudson was an open-source automation server originally created by Kohsuke Kawaguchi at Sun Microsystems.
- **Jenkins Origin:** Jenkins started in 2011 as a fork of the Hudson project.
- **Reason for Fork:** A disagreement arose between the Hudson community and Oracle after Oracle acquired Sun Microsystems.
- **Community Support:** The majority of the Hudson community moved to the Jenkins project.
- **Development:** Jenkins continued development as an independent open-source automation server.
- **Naming:** The Hudson project continued separately, while Jenkins became the widely adopted project.
- **Purpose:** Both tools were designed to automate software builds, testing, and continuous integration.

**History:**

1. Hudson was introduced in 2004.
2. Hudson became popular as a continuous integration server.
3. Oracle acquired Sun Microsystems in 2010.
4. Disagreements developed between Oracle and the Hudson community.
5. In 2011, the community forked Hudson and created Jenkins.
6. Jenkins continued to grow with strong community support and plugin development.

**Relationship:**

```text
          Hudson
             |
             |
       Forked in 2011
             |
             v
          Jenkins
             |
             |
     Independent Project
```



## 4. Why Is Jenkins So Popular?

Jenkins is popular because it is an open-source automation server that helps developers and DevOps engineers automate software development, testing, and deployment processes.

- **Open Source:** Jenkins is free to use and has a large community of contributors.
- **Easy Automation:** It automates repetitive tasks such as building, testing, and deploying applications.
- **Plugin Ecosystem:** It provides thousands of plugins to integrate with different development and DevOps tools.
- **Platform Independent:** Jenkins can run on Linux, Windows, and macOS.
- **CI/CD Support:** It supports Continuous Integration, Continuous Delivery, and Continuous Deployment.
- **Tool Integration:** It integrates with Git, GitHub, GitLab, Docker, Kubernetes, Maven, Ansible, and Terraform.
- **Pipeline as Code:** Jenkins allows users to define CI/CD pipelines using a Jenkinsfile.
- **Distributed Builds:** It supports multiple agents to execute jobs across different machines.
- **Scalability:** Jenkins can handle multiple projects and build workloads using distributed agents.
- **Community Support:** It has a large community that provides plugins, documentation, and troubleshooting support.

**Real-world example:**

Suppose a company has multiple microservices developed using Node.js, Java, and Python.

Without Jenkins:
- Developers manually build applications.
- Developers manually execute test cases.
- DevOps engineers manually create Docker images.
- DevOps engineers manually deploy applications.

With Jenkins:
1. Developers push code to GitLab.
2. Jenkins automatically detects code changes.
3. Jenkins pulls the latest source code.
4. Jenkins builds the applications.
5. Jenkins runs automated tests.
6. Jenkins creates Docker images.
7. Jenkins pushes images to Amazon ECR.
8. Jenkins deploys applications to Kubernetes.

**Example Jenkins integrations:**

| Tool | Purpose |
|---|---|
| Git / GitHub / GitLab | Source code management |
| Maven | Java application build |
| SonarQube | Code quality analysis |
| Docker | Container image creation |
| Trivy | Security and vulnerability scanning |
| Ansible | Configuration management |
| Terraform | Infrastructure provisioning |
| Kubernetes | Container orchestration |
| AWS ECR | Docker image storage |




## 6. What Is Jenkins Architecture?

Jenkins follows a Controller-Agent architecture (previously known as Master-Slave architecture). It is used to manage and execute CI/CD jobs across one or multiple machines.

Jenkins architecture consists of two major components:

1. Jenkins Controller
2. Jenkins Agents

- **Jenkins Controller:** The central component responsible for managing Jenkins jobs, pipelines, configurations, and agents.
- **Jenkins Agents:** Machines that execute build, test, and deployment tasks assigned by the controller.
- **Communication:** The controller communicates with agents to distribute workloads and manage execution.
- **Distributed Builds:** Multiple agents can execute different jobs simultaneously.
- **Scalability:** Additional agents can be connected to handle increased workloads.

### A. Jenkins Controller

The Jenkins Controller is the central management component of Jenkins.

Its main responsibilities are:

- **Job Management:** Creates and manages Jenkins jobs and pipelines.
- **Scheduling:** Decides when and where jobs should execute.
- **Agent Management:** Connects to and manages Jenkins agents.
- **User Interface:** Provides the Jenkins web interface for managing jobs and configurations.
- **Plugin Management:** Manages installed Jenkins plugins.
- **Build Monitoring:** Tracks job execution and build status.
- **Configuration Management:** Stores Jenkins configuration and job information.
- **Build Coordination:** Assigns build tasks to available agents.

### B. Jenkins Agents

Jenkins Agents are machines that execute build and deployment tasks assigned by the controller.

Their main responsibilities are:

- **Build Execution:** Executes application build commands.
- **Testing:** Runs automated test cases.
- **Deployment:** Executes application deployment tasks.
- **Distributed Execution:** Allows multiple jobs to run on different machines.
- **Resource Management:** Uses the CPU, memory, and storage resources of the agent machine.
- **Tool Availability:** Provides required tools such as Java, Maven, Docker, and Node.js.

### C. Jenkins Architecture Workflow

1. Developer pushes code to GitHub or GitLab.
2. Jenkins Controller detects the code changes through a webhook or polling.
3. Controller schedules the Jenkins job.
4. Controller assigns the job to an available agent.
5. Agent pulls the source code from the repository.
6. Agent builds the application.
7. Agent executes automated tests.
8. Agent performs deployment tasks if configured.
9. Agent sends the build result to the controller.
10. Controller displays the build status in the Jenkins dashboard.

### D. Jenkins Architecture Diagram

```text
              Developer
                  |
                  |
            Push Source Code
                  |
                  v
           GitHub / GitLab
                  |
               Webhook
                  |
                  v
        +----------------------+
        |  Jenkins Controller  |
        |----------------------|
        | Job Management       |
        | Build Scheduling     |
        | Agent Management     |
        | Pipeline Management  |
        | Web Interface        |
        +----------------------+
                  |
          Assign Build Jobs
                  |
        +---------+---------+
        |         |         |
        v         v         v
     Agent 1   Agent 2   Agent 3
     Linux     Windows   Linux
        |         |         |
        v         v         v
      Build     Testing   Deployment
        |         |         |
        +---------+---------+
                  |
                  v
         Build Results
                  |
                  v
        Jenkins Controller
                  |
                  v
           Jenkins Dashboard
```



## 7. What Are the Prerequisites for Jenkins?



### A. Hardware Requirements

The hardware requirements depend on the number of users, plugins, pipelines, and build workloads.

For a basic learning environment, the following resources are a reasonable starting point:

| Resource | Suggested configuration |
|---|---|
| CPU | 2 vCPUs |
| RAM | 4 GB |
| Disk Space | 20 GB |
| Network | Internet connectivity |




## 8. What Is Continuous Integration (CI)?

Continuous Integration (CI) is a software development practice in which developers frequently integrate their code changes into a shared repository. Every code change triggers an automated process to build and test the application.

- **Frequent Code Integration:** Developers regularly push their code changes to a shared repository.
- **Automated Build:** Automatically builds the application whenever new code changes are detected.
- **Automated Testing:** Runs test cases to identify bugs and errors in the application.
- **Early Bug Detection:** Helps identify problems early in the development process.
- **Code Quality:** Integrates tools such as SonarQube to analyze code quality.
- **Version Control:** Uses Git, GitHub, or GitLab to manage source code changes.
- **Build Notifications:** Notifies developers about successful or failed builds.
- **Team Collaboration:** Allows multiple developers to work on the same project and integrate their changes regularly.
- **Faster Development:** Reduces manual build and testing efforts.

### A. How Does Continuous Integration Work?

1. Developer writes application code.
2. Developer commits and pushes code to GitHub or GitLab.
3. Jenkins detects the code changes using a webhook or polling.
4. Jenkins pulls the latest source code.
5. Jenkins installs the required dependencies.
6. Jenkins builds the application.
7. Jenkins runs automated test cases.
8. Jenkins performs code quality analysis if configured.
9. Jenkins reports the build result to the development team.

### B. Continuous Integration Workflow

```text
       Developer
           |
           |
      Write Code
           |
           v
      Git Commit
           |
           v
    GitHub / GitLab
           |
           |
       Webhook
           |
           v
    Jenkins Server
           |
           v
      Build Code
           |
           v
     Run Test Cases
           |
           v
    Code Quality Check
           |
           v
     Build Result
           |
       +---+---+
       |       |
       v       v
    Success   Failure
       |       |
       v       v
   Continue  Notify
   Pipeline  Developer
```

