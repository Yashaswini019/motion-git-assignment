# Docker Installation and Usage on Cloud Platforms

## 1. Installing Docker on AWS EC2 Instance

### Prerequisites

* EC2 instance running **Amazon Linux 2** or **Ubuntu**
* SSH access to the instance

### Steps (Amazon Linux 2)

```bash
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
```

(Optional: run Docker without sudo)

```bash
sudo usermod -aG docker ec2-user
newgrp docker
```

### Verify Installation

```bash
docker --version
```

---

## 2. Installing Docker on Azure Virtual Machine

### Prerequisites

* Azure VM (Ubuntu recommended)
* SSH access enabled

### Steps (Ubuntu)

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

(Optional: add user to Docker group)

```bash
sudo usermod -aG docker azureuser
newgrp docker
```

### Verify Installation

```bash
docker --version
```

---

## 3. Installing Docker on GCP Compute Engine Instance

### Prerequisites

* GCP VM instance (Ubuntu/Debian)
* SSH access

### Steps

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

(Optional: add user to Docker group)

```bash
sudo usermod -aG docker $USER
newgrp docker
```

### Verify Installation

```bash
docker --version
```

---

## 4. Building the Docker Image from Dockerfile

Ensure the **Dockerfile** is present in the working directory.

### Build the Docker Image

```bash
docker build -t my-nginx-app .
```

### Verify Image Creation

```bash
docker images
```

---

## 5. Running the Docker Container

Run the container using the built image:

```bash
docker run -d -p 80:80 my-nginx-app
```

### Verify Running Container

```bash
docker ps
```

Access the application using the VM’s public IP:

```
http://<PUBLIC-IP>
```

---

## 6. Conclusion

Docker can be easily installed on AWS EC2, Azure VMs, and GCP Compute Engine instances using standard package managers. Once installed, Docker enables consistent application deployment using Dockerfiles, allowing developers to build and run containers reliably across multiple cloud platforms.