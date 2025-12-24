# Kubernetes Components

Kubernetes is a container orchestration platform that manages the deployment, scaling, and operation of containerized applications. The following are the core components used to run and manage workloads in a Kubernetes cluster.

---

## Pods

A **Pod** is the smallest and most basic deployable unit in Kubernetes. It represents a single instance of a running process in a cluster.

* A Pod can contain **one or more containers**
* Containers in a Pod share:

  * The same network namespace (IP address and ports)
  * Storage volumes
* Pods are **ephemeral**, meaning they can be created and destroyed easily

**Use case:**

* Running a single application container
* Running tightly coupled containers (e.g., an app and a logging sidecar)

---

## Services

A **Service** provides a stable network endpoint to access a set of Pods. Since Pods can be created or destroyed dynamically, Services ensure reliable communication.

### Key Features:

* Abstracts Pod IP addresses
* Enables load balancing across Pods
* Provides service discovery

### Common Types:

* **ClusterIP** – Internal access within the cluster
* **NodePort** – Exposes service on each node’s IP
* **LoadBalancer** – Exposes service externally using a cloud provider’s load balancer

---

## Deployments

A **Deployment** is a higher-level Kubernetes object used to manage applications declaratively.

### Responsibilities:

* Manages Pod creation and updates
* Enables **rolling updates** and **rollbacks**
* Ensures the desired number of replicas are running

Deployments use **ReplicaSets** internally to maintain the desired state of Pods.

---

## ReplicaSets

A **ReplicaSet** ensures that a specified number of identical Pods are running at all times.

### Key Points:

* Automatically creates or deletes Pods to match the desired count
* Rarely managed directly by users
* Typically controlled by a Deployment

**Purpose:**

* Maintain application availability and fault tolerance

---

## ConfigMaps

A **ConfigMap** is used to store non-sensitive configuration data in key-value pairs.

### Common Uses:

* Environment variables
* Application configuration files
* Command-line arguments

**Benefits:**

* Separates configuration from application code
* Makes applications more portable and easier to manage

---

## Secrets

A **Secret** is used to store sensitive information securely.

### Examples:

* Database passwords
* API keys
* TLS certificates

### Features:

* Base64-encoded storage
* Access controlled via Kubernetes RBAC
* Can be mounted as environment variables or volumes

**Best Practice:**

* Use Secrets instead of hardcoding sensitive data into application code or configuration files

---

## Summary

| Component  | Purpose                       |
| ---------- | ----------------------------- |
| Pod        | Smallest deployable unit      |
| Service    | Stable network access         |
| Deployment | Manages application lifecycle |
| ReplicaSet | Ensures desired Pod count     |
| ConfigMap  | Stores non-sensitive config   |
| Secret     | Stores sensitive data         |
