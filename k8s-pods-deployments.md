# Kubernetes Pods and Deployments

## Overview

Kubernetes provides core resources that help run and manage containerized applications efficiently. Two of the most fundamental resources are **Pods** and **Deployments**. This document explains what Pods are, how they function within Kubernetes, and how Deployments are used to manage Pods.

---

## What Are Pods in Kubernetes?

### Definition

A **Pod** is the smallest and simplest deployable unit in Kubernetes. It represents a single instance of a running process in a cluster and can contain **one or more containers** that run together.

### How Pods Function

Pods provide:

* **Shared networking**: All containers in a Pod share the same IP address and ports.
* **Shared storage**: Containers can share volumes mounted inside the Pod.
* **Co-located execution**: Containers in a Pod are scheduled on the same node and run together.

Typically, a Pod runs:

* A **single container** (most common use case), or
* Multiple tightly coupled containers (for example, a main application container and a logging sidecar).

### Key Characteristics

* Pods are **ephemeral** — they can be created, destroyed, and recreated.
* If a Pod fails, Kubernetes does not automatically recreate it unless it is managed by a higher-level resource such as a Deployment.
* Pods enable applications to scale and communicate efficiently within the cluster.

---

## What Is a Deployment?

### Definition

A **Deployment** is a higher-level Kubernetes resource that manages a set of identical Pods. It ensures that the desired number of Pods are running at all times and provides mechanisms for updates and rollbacks.

### Why Use Deployments?

Deployments provide:

* **Replica management**: Ensures the specified number of Pods are running.
* **Rolling updates**: Updates Pods gradually without downtime.
* **Self-healing**: Automatically replaces failed Pods.
* **Version control**: Allows rollback to previous versions of an application.

Instead of managing Pods directly, Deployments are the recommended way to run applications in Kubernetes.

---

## Creating a Deployment to Manage Pods

### Using kubectl Commands

A simple way to create a Deployment using `kubectl` is:

```bash
kubectl create deployment my-deployment --image=nginx
```

This command:

* Creates a Deployment named `my-deployment`
* Runs Pods using the `nginx` container image
* Automatically manages the Pods created by the Deployment

### Scaling a Deployment

To scale the number of Pods managed by the Deployment:

```bash
kubectl scale deployment my-deployment --replicas=3
```

This ensures that three identical Pods are running.

---

### Creating a Deployment Using a YAML Manifest

Deployments are commonly defined using YAML for better control and repeatability.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: nginx
        ports:
        - containerPort: 80
```

Apply the Deployment using:

```bash
kubectl apply -f deployment.yaml
```

---

## Summary

* **Pods** are the smallest deployable units in Kubernetes and run one or more containers.
* Pods share networking and storage and are designed to be short-lived.
* **Deployments** manage Pods by providing scalability, reliability, and controlled updates.
* Using Deployments is the recommended approach for running applications in Kubernetes.

