
---

````markdown
# Ansible Ad-Hoc Commands Documentation

## Overview
Ansible ad-hoc commands are single-line commands used to perform quick
administrative tasks on managed nodes without writing a full playbook.
They are commonly used for service checks, system monitoring, and
gathering system information across cloud platforms such as AWS, Azure,
and Google Cloud Platform (GCP).

---

## Basic Ad-Hoc Command Syntax

```bash
ansible <host-pattern> -m <module> -a "<arguments>"
````

Example:

```bash
ansible all -m ping
```

---

## Gathering Facts from Managed Nodes

Gather complete system facts:

```bash
ansible all -m setup
```

Gather specific system information:

```bash
ansible all -m setup -a "filter=ansible_os_family"
```

---

## Checking the Status of a Service

Check and start a service if it is not running:

```bash
ansible all -m service -a "name=nginx state=started"
```

Check service status using systemctl:

```bash
ansible all -m shell -a "systemctl status nginx"
```

---

## Managing AWS EC2 Instances Using Ad-Hoc Commands

Example inventory group:

```ini
[aws]
aws-instance ansible_host=54.x.x.x ansible_user=ec2-user
```

Run uptime command:

```bash
ansible aws -m command -a "uptime"
```

Check Docker service:

```bash
ansible aws -m service -a "name=docker state=started"
```

---

## Managing Azure Virtual Machines Using Ad-Hoc Commands

Example inventory group:

```ini
[azure]
azure-vm ansible_host=20.x.x.x ansible_user=azureuser
```

Gather facts from Azure VMs:

```bash
ansible azure -m setup
```

Check SSH service status:

```bash
ansible azure -m shell -a "systemctl status sshd"
```

---

## Managing Google Cloud Platform (GCP) Instances Using Ad-Hoc Commands

Example inventory group:

```ini
[gcp]
gcp-vm ansible_host=34.x.x.x ansible_user=gcpuser
```

Ping GCP instances:

```bash
ansible gcp -m ping
```

Check Apache service status:

```bash
ansible gcp -m service -a "name=httpd state=started"
```

---

