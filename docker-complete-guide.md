# Complete Docker Guide

This document consolidates all Docker-related documentation, including Dockerfile usage, build/run instructions, Docker Compose setup, and multi-container management.

---

## 1. Dockerfile Usage

- The Dockerfile is used to build a container image for the application.
- Key steps:
  1. Choose a base image (e.g., `python:3.11-slim`)
  2. Copy application files into the container
  3. Install dependencies
  4. Set environment variables
  5. Expose required ports
  6. Define the entrypoint or command

**Build the image:**

```bash
docker build -t my-app:latest .
````

**Run the container:**

```bash
docker run -d -p 5000:5000 my-app:latest
```

---

## 2. Build and Run Instructions

* **Building the image**: `docker build -t my-app:latest .`
* **Running the container**: `docker run -d -p 5000:5000 my-app:latest`
* **Stopping the container**: `docker stop <container_id>`
* **Removing the container**: `docker rm <container_id>`
* **Listing containers**: `docker ps -a`

---

## 3. Docker Compose Setup

* `docker-compose.yml` defines multi-container applications.
* Example services:

  * `web` – Python application
  * `db` – PostgreSQL database
* Key features:

  * Environment variables
  * Volume mapping for persistence
  * Network configuration

**Start all services:**

```bash
docker-compose up -d
```

**Stop all services:**

```bash
docker-compose down
```

---

## 4. Multi-Container Management

### Viewing Logs

```bash
docker-compose logs -f
docker-compose logs -f web
```

### Scaling Services

```bash
docker-compose up -d --scale web=3
```

### Additional Commands

* Check running containers: `docker-compose ps`
* Stop a specific service: `docker-compose stop <service_name>`
* Remove stopped containers: `docker-compose rm`

---

## Notes

* Ensure `.env` files and sensitive information are not committed.
* All commands assume the current working directory contains `docker-compose.yml`.
* Scaling may require extra configuration depending on the application.
