# Build and Run Instructions for Python Web Application

This document describes the steps to build and run the custom Docker image
for the Python web application using the provided Dockerfile.

---

## Build the Docker Image

Navigate to the directory containing the Dockerfile:

```bash
cd pythonweb-app
````

Build the Docker image using the following command:

```bash
docker build -t python-web-app .
```

---

## Run the Docker Container

Run a container from the built Docker image:

```bash
docker run -d -p 5000:5000 --name python-web-container python-web-app
```

This command runs the container in detached mode and maps port 5000 of the
container to port 5000 on the host machine.

---

## Access the Application

Once the container is running, open a web browser and access the application
using the following URL:

```
http://localhost:5000
```
