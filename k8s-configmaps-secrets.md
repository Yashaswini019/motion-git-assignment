# Kubernetes ConfigMaps and Secrets

## Overview

Kubernetes provides **ConfigMaps** and **Secrets** to manage application configuration and sensitive data separately from container images. This separation improves flexibility, security, and maintainability across environments.

---

## What Are ConfigMaps?

### Definition

A **ConfigMap** is a Kubernetes resource used to store **non-sensitive configuration data** such as environment variables, application settings, and configuration files. ConfigMaps allow configuration values to be changed without rebuilding container images.

### Purpose of ConfigMaps

ConfigMaps help:

* Decouple configuration from application code
* Support different configurations for different environments (dev, test, prod)
* Improve portability and maintainability of applications

---

## How ConfigMaps Are Used in Pods

ConfigMaps can be consumed by Pods in two primary ways:

### 1. As Environment Variables

Configuration values can be injected directly into containers as environment variables.

```bash
kubectl create configmap app-config --from-literal=APP_MODE=production
```

Example Pod usage:

```yaml
env:
  - name: APP_MODE
    valueFrom:
      configMapKeyRef:
        name: app-config
        key: APP_MODE
```

---

### 2. As Configuration Files (Mounted Volumes)

ConfigMaps can also be mounted as files inside a container.

```bash
kubectl create configmap app-config --from-file=config.properties
```

This allows applications to read configuration values from files at runtime.

---

## What Are Secrets?

### Definition

A **Secret** is a Kubernetes resource designed to store **sensitive information** such as:

* Passwords
* API keys
* Tokens
* Certificates

Secrets are similar to ConfigMaps but provide additional security controls and are intended specifically for confidential data.

---

## Why Secrets Are Important

* Prevent hardcoding sensitive data in images or repositories
* Reduce exposure of credentials
* Enable secure injection of sensitive data into Pods
* Support encryption at rest (when configured)

---

## Managing Secrets in Kubernetes

### Creating a Secret Using kubectl

Secrets can be created using the `kubectl` command-line tool:

```bash
kubectl create secret generic db-secret --from-literal=password=securepassword
```

---

## Using Secrets in Pods

### 1. Injecting Secrets as Environment Variables

```yaml
env:
  - name: DB_PASSWORD
    valueFrom:
      secretKeyRef:
        name: db-secret
        key: password
```

---

### 2. Mounting Secrets as Files

Secrets can also be mounted as files within a container, making them accessible through the filesystem.

---

## ConfigMaps vs Secrets

| Feature       | ConfigMaps            | Secrets                     |
| ------------- | --------------------- | --------------------------- |
| Intended data | Non-sensitive         | Sensitive                   |
| Encryption    | No (by default)       | Yes (at rest, when enabled) |
| Use cases     | App settings, configs | Passwords, API keys         |
| Storage       | Plain text            | Base64 encoded              |

---

## Summary

* **ConfigMaps** store non-sensitive configuration data and allow dynamic configuration changes.
* **Secrets** securely store sensitive information required by applications.
* Both resources help keep container images clean and reusable.
* ConfigMaps and Secrets can be consumed by Pods as environment variables or mounted files.