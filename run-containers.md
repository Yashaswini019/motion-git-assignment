# **Creating and Running Containers Using Docker CLI on AWS, Azure, and GCP**

This document explains how to create and run Docker containers on the three major cloud platforms: **AWS, Azure, and GCP**. It includes commands to pull images from a registry, run containers, and check the status of running containers.

---

## **1. Prerequisites**

Before starting, ensure you have:

1. An account on AWS, Azure, or GCP.
2. A virtual machine (VM) or cloud instance running Linux (Ubuntu recommended).
3. Docker installed on the VM.
   **Install Docker on Linux:**

```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER  # Optional: allows running docker without sudo
```

Verify Docker installation:

```bash
docker --version
```

---

## **2. Pulling Images from a Docker Registry**

To use a Docker image, first pull it from Docker Hub or any other registry.

**Command:**

```bash
docker pull <image-name>:<tag>
```

**Example:**

```bash
docker pull nginx:latest
docker pull ubuntu:20.04
```

---

## **3. Running a Docker Container**

**Command:**

```bash
docker run [options] <image-name>:<tag>
```

**Common Options:**

* `-d` → Run container in detached mode (background)
* `-p <host-port>:<container-port>` → Map ports
* `--name <container-name>` → Assign a name to the container
* `-it` → Interactive mode (useful for Ubuntu, bash, etc.)

**Examples:**

1. Run Nginx in detached mode on port 8080:

```bash
docker run -d -p 8080:80 --name mynginx nginx:latest
```

2. Run Ubuntu interactively:

```bash
docker run -it ubuntu:20.04 bash
```

---

## **4. Checking the Status of Running Containers**

1. **List all running containers:**

```bash
docker ps
```

2. **List all containers (including stopped):**

```bash
docker ps -a
```

3. **View logs of a container:**

```bash
docker logs <container-name-or-id>
```

4. **Stop a running container:**

```bash
docker stop <container-name-or-id>
```

5. **Remove a container:**

```bash
docker rm <container-name-or-id>
```

6. **Remove an image:**

```bash
docker rmi <image-name>:<tag>
```

---

## **5. Running Containers on AWS**

1. Launch an **EC2 instance** and connect via SSH.
2. Install Docker on the EC2 instance.
3. Use Docker commands as described above.

**Example: Run Nginx on AWS EC2**

```bash
docker pull nginx:latest
docker run -d -p 80:80 --name webserver nginx:latest
docker ps
```

---

## **6. Running Containers on Azure**

1. Launch an **Azure Virtual Machine** (Linux).
2. SSH into the VM.
3. Install Docker.
4. Use the same Docker commands.

**Example: Run Ubuntu Container on Azure**

```bash
docker pull ubuntu:20.04
docker run -it ubuntu:20.04 bash
docker ps
```

---

## **7. Running Containers on GCP**

1. Launch a **Compute Engine VM** (Linux).
2. Connect via SSH.
3. Install Docker.
4. Run containers using Docker CLI.

**Example: Run Nginx on GCP Compute Engine**

```bash
docker pull nginx:latest
docker run -d -p 80:80 --name mynginx nginx:latest
docker ps
```

---

## **8. Summary of Common Commands**

| Task                    | Command                                                               |
| ----------------------- | --------------------------------------------------------------------- |
| Pull Docker image       | `docker pull <image>:<tag>`                                           |
| Run container           | `docker run -d -p <host-port>:<container-port> --name <name> <image>` |
| List running containers | `docker ps`                                                           |
| List all containers     | `docker ps -a`                                                        |
| Stop container          | `docker stop <container>`                                             |
| Remove container        | `docker rm <container>`                                               |
| Remove image            | `docker rmi <image>`                                                  |
| Check container logs    | `docker logs <container>`                                             |

---

This process works consistently across **AWS, Azure, and GCP** once Docker is installed on the VM.

---