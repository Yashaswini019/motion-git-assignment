# Docker Hub: Managing Container Images

This document explains how to use **Docker Hub** to manage container images. It includes step-by-step instructions for:

* Creating a Docker Hub account
* Building and pushing images to Docker Hub
* Pulling images from Docker Hub
* Using Docker Hub images in **AWS**, **Azure**, and **GCP** environments

---

## 1. What is Docker Hub?

Docker Hub is a cloud-based container registry used to store, manage, and share Docker container images. It supports:

* Public and private repositories
* Image versioning with tags
* Integration with CI/CD pipelines

---

## 2. Creating a Docker Hub Account

1. Go to [https://hub.docker.com](https://hub.docker.com)
2. Click **Sign Up**
3. Register using an email address or GitHub/Google account
4. Verify your email
5. Create a **Docker Hub username** (this will be used in image names)

After account creation, create a repository:

1. Log in to Docker Hub
2. Click **Repositories → Create Repository**
3. Choose **Public** or **Private**
4. Name the repository (e.g., `sample-app`)

---

## 3. Installing Docker (Cloud VMs)

Before pushing or pulling images, Docker must be installed on your VM or local machine.

### Install Docker on Linux (AWS EC2 / Azure VM / GCP VM)

```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

Verify installation:

```bash
docker --version
```

(Optional) Run Docker without sudo:

```bash
sudo usermod -aG docker $USER
logout
```

---

## 4. Login to Docker Hub

Authenticate Docker CLI with Docker Hub:

```bash
docker login
```

Enter:

* Docker Hub username
* Docker Hub password or access token

---

## 5. Build and Push an Image to Docker Hub

### Step 1: Create a Dockerfile

```Dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```

### Step 2: Build the Docker Image

```bash
docker build -t <dockerhub-username>/sample-app:latest .
```

Example:

```bash
docker build -t yashaswini/sample-app:latest .
```

### Step 3: Push Image to Docker Hub

```bash
docker push <dockerhub-username>/sample-app:latest
```

After pushing, the image will be visible in your Docker Hub repository.

---

## 6. Pulling an Image from Docker Hub

Pull an image on any machine (local or cloud VM):

```bash
docker pull <dockerhub-username>/sample-app:latest
```

Run the container:

```bash
docker run -d -p 80:80 <dockerhub-username>/sample-app:latest
```

---

## 7. Using Docker Hub with AWS

### AWS EC2 Example

1. Launch an EC2 instance (Ubuntu)
2. Install Docker on EC2
3. Login to Docker Hub
4. Pull the image

```bash
docker pull yashaswini/sample-app:latest
docker run -d -p 80:80 yashaswini/sample-app:latest
```

Access the app using:

```
http://<EC2-Public-IP>
```

### AWS ECS (Conceptual)

* Use Docker Hub image URI in ECS task definition
* Example image:

```
yashaswini/sample-app:latest
```

---

## 8. Using Docker Hub with Azure

### Azure Virtual Machine Example

1. Create an Azure VM (Ubuntu)
2. Install Docker
3. Login to Docker Hub
4. Pull and run image

```bash
docker pull yashaswini/sample-app:latest
docker run -d -p 80:80 yashaswini/sample-app:latest
```

Access using:

```
http://<Azure-VM-Public-IP>
```

### Azure Kubernetes Service (AKS)

Use Docker Hub image in Kubernetes deployment:

```yaml
containers:
- name: sample-app
  image: yashaswini/sample-app:latest
  ports:
  - containerPort: 80
```

---

## 9. Using Docker Hub with GCP

### GCP Compute Engine Example

1. Create a Compute Engine VM
2. Install Docker
3. Login to Docker Hub
4. Pull and run image

```bash
docker pull yashaswini/sample-app:latest
docker run -d -p 80:80 yashaswini/sample-app:latest
```

Access using:

```
http://<GCP-VM-External-IP>
```

### Google Kubernetes Engine (GKE)

Use Docker Hub image directly in deployment:

```yaml
containers:
- name: sample-app
  image: yashaswini/sample-app:latest
```

---

## 10. Best Practices

* Use meaningful image tags (e.g., `v1.0`, `prod`, `dev`)
* Avoid using `latest` in production
* Use private repositories for sensitive images
* Scan images for vulnerabilities
* Automate builds using CI/CD pipelines

---

## 11. Summary

Docker Hub provides a centralized way to manage container images and easily deploy them across AWS, Azure, and GCP. By pushing images once and pulling them across environments, teams can ensure consistency, portability, and scalability in cloud-native deployments.
