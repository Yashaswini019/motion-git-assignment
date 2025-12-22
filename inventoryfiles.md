````markdown
# Ansible Inventory Files for AWS, Azure, and GCP

## Overview
An Ansible inventory file defines the hosts and groups of hosts that Ansible
manages. Inventory files can be static (INI or YAML format) or dynamic.
This document demonstrates how to create **static inventory files** for
AWS, Azure, and Google Cloud Platform (GCP), including how to define
groups and hosts.

---

## General Steps to Create an Inventory File

1. Create a text file (commonly named `inventory` or `.ini`).
2. Define host groups using square brackets `[group_name]`.
3. Add hosts under each group with connection details such as:
   - `ansible_host` (public or private IP)
   - `ansible_user` (SSH user)
   - `ansible_ssh_private_key_file` (optional)
4. Save the file and use it with Ansible commands using the `-i` option.

Example:
```bash
ansible all -i inventory.ini -m ping
````

---

## AWS Inventory File Example

AWS EC2 instances are commonly accessed using the `ec2-user`.

```ini
[aws]
aws-ec2-1 ansible_host=54.123.45.67 ansible_user=ec2-user
aws-ec2-2 ansible_host=18.210.98.76 ansible_user=ec2-user
```

Run a command on AWS hosts:

```bash
ansible aws -i aws_inventory.ini -m ping
```

---

## Azure Inventory File Example

Azure virtual machines usually use `azureuser` or a custom admin username.

```ini
[azure]
azure-vm-1 ansible_host=20.55.66.77 ansible_user=azureuser
azure-vm-2 ansible_host=40.88.99.11 ansible_user=azureuser
```

Run a command on Azure hosts:

```bash
ansible azure -i azure_inventory.ini -m setup
```

---

## GCP Inventory File Example

GCP compute instances often use a custom SSH user created during VM setup.

```ini
[gcp]
gcp-vm-1 ansible_host=34.120.88.45 ansible_user=gcpuser
gcp-vm-2 ansible_host=35.199.22.90 ansible_user=gcpuser
```

Run a command on GCP hosts:

```bash
ansible gcp -i gcp_inventory.ini -m ping
```

---

## Combined Inventory File Example

All cloud providers can also be managed from a single inventory file.

```ini
[aws]
aws-ec2 ansible_host=54.x.x.x ansible_user=ec2-user

[azure]
azure-vm ansible_host=20.x.x.x ansible_user=azureuser

[gcp]
gcp-vm ansible_host=34.x.x.x ansible_user=gcpuser
```

---

## Conclusion

Static Ansible inventory files provide a simple way to manage cloud
infrastructure across AWS, Azure, and GCP. By organizing hosts into
groups and defining connection details, administrators can efficiently
run Ansible commands across multiple cloud environments.

```

---

