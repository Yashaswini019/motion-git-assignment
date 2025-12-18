# Jenkins Architecture

## Overview

Jenkins is an open-source automation server used to implement Continuous Integration and Continuous Delivery (CI/CD) pipelines. It automates building, testing, and deploying applications. Jenkins follows a **controller–agent (master–slave)** architecture that allows workloads to be distributed across multiple machines.

---

## Jenkins Controller (Master)

The **Jenkins Controller** (historically called *Master*) is the central component responsible for managing and coordinating all Jenkins activities.

### Responsibilities:

* Provides the **Web UI** and REST APIs
* Manages jobs, pipelines, and configurations
* Schedules builds and assigns them to agents
* Maintains build history, logs, and artifacts
* Manages plugins, credentials, and security

⚠️ Best Practice: Avoid running heavy build tasks on the controller; delegate work to agents.

---

## Jenkins Agents (Slaves)

**Jenkins Agents** are worker nodes that execute build jobs assigned by the controller.

### Characteristics:

* Can run on physical machines, virtual machines, containers, or cloud instances
* Can be configured with specific tools (Java, Docker, Node.js, etc.)
* Can be static (always available) or dynamic (created on demand)

### Responsibilities:

* Execute build, test, and deployment steps
* Report build results and logs back to the controller

---

## Communication Between Controller and Agents

* Communication is typically done over **SSH** or **JNLP (Java Web Start)**
* Controller sends job instructions
* Agents return execution status, logs, and artifacts

---

## Jenkins Architecture Diagram

```
                 +----------------------+
                 |   Jenkins Controller |
                 |  (Web UI, Scheduler) |
                 +----------+-----------+
                            |
            -----------------------------------------
            |                    |                  |
+-------------------+  +-------------------+  +-------------------+
|   Agent 1 (VM)    |  | Agent 2 (Docker)  |  | Agent 3 (Cloud)   |
|  Build / Test     |  |  Build / Test     |  |  Build / Deploy   |
+-------------------+  +-------------------+  +-------------------+
```

---

## Jenkins Interaction with Cloud Platforms

Jenkins integrates seamlessly with major cloud providers to support **scalable and dynamic CI/CD pipelines**.

### AWS

* Jenkins controller runs on **EC2** or **EKS**
* Agents can be dynamically provisioned using:

  * EC2 instances
  * Docker containers
  * Kubernetes pods
* Integrates with AWS services like S3, ECR, ECS, EKS, and IAM

### Azure

* Controller runs on **Azure VM** or **AKS**
* Agents created on demand using Azure VMs or containers
* Integrates with Azure DevOps, Azure Container Registry (ACR), and Azure Storage

### Google Cloud Platform (GCP)

* Controller hosted on **Compute Engine** or **GKE**
* Agents provisioned dynamically using GCE instances or Kubernetes pods
* Integrates with GCR, Artifact Registry, and Cloud Storage

---




