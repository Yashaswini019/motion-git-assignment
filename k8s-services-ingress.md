# Kubernetes Services and Ingress

## Overview

In Kubernetes, **Services** and **Ingress** are networking resources that enable communication between application components and manage access to applications running inside a cluster. Services provide stable networking for Pods, while Ingress manages external HTTP/HTTPS access.

---

## What Are Services in Kubernetes?

### Definition

A **Service** is a Kubernetes resource that exposes a logical set of Pods and provides a stable way to access them. Since Pods are ephemeral and their IP addresses can change, Services act as a consistent endpoint for communication.

### How Services Work

* Services use **labels and selectors** to identify target Pods.
* They provide a stable **IP address and DNS name**.
* Traffic sent to the Service is automatically load-balanced across matching Pods.

---

## Types of Kubernetes Services

### 1. ClusterIP

* **Default Service type**
* Exposes the Service only within the Kubernetes cluster
* Used for internal communication between applications

**Use case:** Backend services accessed only by other services.

**Example:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-clusterip-service
spec:
  type: ClusterIP
  selector:
    app: my-app
  ports:
    - port: 80
      targetPort: 8080
```

---

### 2. NodePort

* Exposes the Service on each node’s IP at a static port
* Accessible externally using `<NodeIP>:<NodePort>`

**Use case:** Simple external access for development or testing.

**Example:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-nodeport-service
spec:
  type: NodePort
  selector:
    app: my-app
  ports:
    - port: 80
      targetPort: 8080
      nodePort: 30007
```

---

### 3. LoadBalancer

* Exposes the Service externally using a cloud provider’s load balancer
* Automatically provisions a cloud load balancer (AWS, Azure, GCP)

**Use case:** Production-grade external access.

**Example:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-loadbalancer-service
spec:
  type: LoadBalancer
  selector:
    app: my-app
  ports:
    - port: 80
      targetPort: 8080
```

---

## What Is Ingress?

### Definition

**Ingress** is a Kubernetes resource that manages **external HTTP and HTTPS access** to Services within a cluster. It provides routing rules based on hostnames and URL paths.

Ingress requires an **Ingress Controller** (such as NGINX, AWS Load Balancer Controller, or Azure Application Gateway) to function.

---

## How Ingress Helps Manage External Access

Ingress allows you to:

* Route traffic to different Services based on **URL paths**
* Use **host-based routing** (e.g., app.example.com)
* Centralize access rules instead of exposing multiple Services
* Enable TLS/SSL termination for HTTPS

Instead of exposing each Service individually, Ingress acts as a **single entry point**.

---

## Example Ingress Configuration

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
    - host: my-app.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: my-loadbalancer-service
                port:
                  number: 80
```

### How This Works

* Incoming traffic to `my-app.example.com`
* Routed to `my-loadbalancer-service`
* Service forwards traffic to matching Pods

---

## Services vs Ingress (Summary)

| Feature        | Service     | Ingress                |
| -------------- | ----------- | ---------------------- |
| Purpose        | Expose Pods | Manage external access |
| Protocols      | TCP/UDP     | HTTP/HTTPS             |
| Load balancing | Yes         | Yes                    |
| Routing rules  | No          | Yes                    |
| TLS support    | Limited     | Yes                    |

---

## Summary

* **Services** provide stable networking and load balancing for Pods.
* **ClusterIP**, **NodePort**, and **LoadBalancer** support different access needs.
* **Ingress** manages external HTTP/HTTPS access using routing rules.
* Ingress simplifies application exposure and improves scalability and security.
