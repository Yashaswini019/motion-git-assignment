# Kubernetes Control Plane Components

The Kubernetes **control plane** is responsible for managing the overall state of the cluster. It makes global decisions, detects changes, and ensures that the cluster operates according to the desired configuration.

---

## API Server

The **API Server** is the central component of the Kubernetes control plane.

### Responsibilities:

* Acts as the **entry point** for all Kubernetes operations
* Exposes the Kubernetes REST API
* Handles authentication and authorization
* Validates and processes requests from:

  * `kubectl`
  * Controllers
  * Other cluster components

All communication within the cluster goes through the API Server.

---

## etcd (Key-Value Store)

**etcd** is a distributed, reliable key-value store used by Kubernetes to store all cluster data.

### Responsibilities:

* Stores:

  * Cluster configuration
  * State of nodes and Pods
  * Secrets and metadata
* Provides strong consistency and high availability
* Serves as the **source of truth** for the cluster

---

## Controller Manager

The **Controller Manager** runs background control loops that continuously monitor the cluster state.

### Responsibilities:

* Ensures the actual cluster state matches the desired state
* Automatically takes corrective actions when differences are detected

### Common Controllers:

* Node Controller
* Replica Controller
* Endpoint Controller
* Namespace Controller

---

## Scheduler

The **Scheduler** is responsible for assigning Pods to worker nodes.

### Responsibilities:

* Evaluates resource requirements (CPU, memory)
* Considers constraints such as:

  * Node affinity
  * Taints and tolerations
* Selects the most suitable worker node for each Pod

---

## Summary

| Component          | Function                  |
| ------------------ | ------------------------- |
| API Server         | Cluster communication hub |
| etcd               | Stores cluster state      |
| Controller Manager | Maintains desired state   |
| Scheduler          | Assigns Pods to nodes     |

---

## Conclusion

The Kubernetes control plane coordinates all cluster operations. It ensures application reliability, scalability, and consistency by continuously monitoring and managing cluster resources.