# Managing Multi-Container Application with Docker Compose

This document explains how to manage a multi-container application using Docker Compose, including starting, stopping, viewing logs, and scaling services.

## 1. Starting the Application

To start all services defined in `docker-compose.yml`:

```bash
docker-compose up -d
````

* `-d` runs containers in detached mode (in the background).
* This will create and start all containers for your application.

---

## 2. Stopping the Application

To stop all running containers:

```bash
docker-compose down
```

* This stops and removes containers, networks, and default volumes.
* Data volumes will persist unless explicitly removed.

---

## 3. Viewing Logs

To view real-time logs of all services:

```bash
docker-compose logs -f
```

* `-f` (follow) allows you to see continuous logs.
* To view logs of a specific service:

```bash
docker-compose logs -f <service_name>
```

Example:

```bash
docker-compose logs -f web
```

---

## 4. Scaling Services

If you need multiple instances of a service (e.g., web app):

```bash
docker-compose up -d --scale <service_name>=<number_of_instances>
```

Example:

```bash
docker-compose up -d --scale web=3
```

* This will run 3 instances of the `web` service.
* Useful for load balancing and testing multiple containers.

---

## 5. Additional Commands

* Check running containers:

```bash
docker-compose ps
```

* Stop a specific service:

```bash
docker-compose stop <service_name>
```

* Remove stopped containers:

```bash
docker-compose rm
```

---

## Notes

* Ensure all environment variables and volume mappings are correctly set in `docker-compose.yml`.
* Scaling may require additional configuration depending on network and dependencies.

