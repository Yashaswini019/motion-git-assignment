# Kubernetes Master and Worker Nodes

A Kubernetes cluster is composed of **master (control plane) nodes** and **worker nodes**. Each plays a critical role in managing and running containerized applications.

---

## Master Node (Control Plane)

The **master node** is responsible for managing the Kubernetes cluster and maintaining the desired state of applications.

### Key Components and Functions

#### API Server

* Acts as the **central management interface** for Kubernetes
* Receives requests from users, CLI tools (kubectl), and other components
* Validates and processes REST API requests

#### Scheduler

* Assigns Pods to worker nodes
* Makes scheduling decisions based on:

  * Resource availability
  * Node constraints
  * Policies and affinities

#### Controller Manager

* Runs background controllers that monitor cluster state
* Ensures the actual state matches the desired state

Common controllers include:

* Node Controller
* Replica Controller
* Endpoint Controller

#### etcd

* A distributed key-value store
* Stores cluster configuration and state data
* Ensures data consistency and reliability

---

## Worker Node

Worker nodes are responsible for **running application workloads** and communicating with the master node.

### Key Components and Functions

#### Kubelet

* An agent running on each worker node
* Communicates with the API Server
* Ensures containers are running as specified in Pod definitions

#### Kube Proxy

* Handles network routing and load balancing
* Maintains network rules for Pod-to-Pod and external communication

#### Container Runtime

* Software that runs containers
* Responsible for pulling images and starting containers

Common container runtimes:

* Docker
* containerd
* CRI-O

---

## Summary

| Node Type   | Responsibility                       |
| ----------- | ------------------------------------ |
| Master Node | Manages cluster state and scheduling |
| Worker Node | Runs application workloads           |

---

## Conclusion

* The **master node** controls and coordinates the cluster
* **Worker nodes** execute application containers
* Together, they ensure high availability, scalability, and reliability in Kubernetes


## Kubernetes Cluster Architecture

                +----------------------+
                |      Master Node     |
                |----------------------|
                |  API Server          |
                |  Scheduler           |
                |  Controller Manager |
                |  etcd                |
                +----------+-----------+
                           |
          -----------------------------------------
          |                    |                 |
+----------------+   +----------------+   +----------------+
|  Worker Node 1 |   |  Worker Node 2 |   |  Worker Node 3 |
|----------------|   |----------------|   |----------------|
| Kubelet        |   | Kubelet        |   | Kubelet        |
| Kube Proxy     |   | Kube Proxy     |   | Kube Proxy     |
| Containers     |   | Containers     |   | Containers     |
+----------------+   +----------------+   +----------------+
