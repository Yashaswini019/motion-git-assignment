# Basic Docker Commands

## Introduction

Docker commands are used to manage container images and containers efficiently. These commands are consistent across cloud platforms like **AWS**, **Azure**, and **GCP**, allowing you to deploy and manage applications in a predictable way.

---

## 1. `docker pull`

### Description

Downloads a Docker image from a registry (e.g., Docker Hub) to the local system.

### Command Example

```bash
docker pull nginx
```

### Usage in Cloud Context

* **AWS EC2:** Pulls the `nginx` image onto an EC2 instance to deploy a web server.
* **Azure VM:** Downloads the image for container deployment on an Azure Virtual Machine.
* **GCP Compute Engine:** Retrieves the image to run containers on a Compute Engine instance.

---

## 2. `docker run`

### Description

Creates and starts a container from a specified Docker image.

### Command Example

```bash
docker run -d -p 80:80 nginx
```

* `-d`: Runs container in detached mode
* `-p 80:80`: Maps container port 80 to host port 80

### Usage in Cloud Context

* **AWS:** Runs Nginx in an EC2 instance, accessible via public IP.
* **Azure:** Hosts a web application on an Azure VM with port mapping.
* **GCP:** Deploys a web server container on a Compute Engine instance.

---

## 3. `docker ps`

### Description

Lists running containers on the host.

### Command Example

```bash
docker ps
```

* Add `-a` to see all containers (including stopped):

```bash
docker ps -a
```

### Usage in Cloud Context

* **AWS:** Monitors active containers on EC2 instances.
* **Azure:** Checks running containers on Azure VMs.
* **GCP:** Lists containers on Compute Engine VMs.

---

## 4. `docker stop`

### Description

Stops a running container gracefully.

### Command Example

```bash
docker stop <container_id>
```

### Usage in Cloud Context

* **AWS:** Stops a container on EC2 when no longer needed or for maintenance.
* **Azure:** Stops applications running inside containers on VMs.
* **GCP:** Halts a container running on Compute Engine to save resources.

---

## 5. `docker rm`

### Description

Removes one or more stopped containers from the system.

### Command Example

```bash
docker rm <container_id>
```

### Usage in Cloud Context

* **AWS:** Cleans up unused containers on EC2 instances.
* **Azure:** Removes stopped containers from Azure VMs to free space.
* **GCP:** Deletes old containers from Compute Engine hosts.

---

## Summary

These basic Docker commands — `docker pull`, `docker run`, `docker ps`, `docker stop`, and `docker rm` — are essential for managing containerized applications. They work consistently across **AWS**, **Azure**, and **GCP**, making Docker a powerful tool for multi-cloud deployments.
