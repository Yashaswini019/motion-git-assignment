# Ansible Architecture and Concepts

## Ansible Architecture

Ansible is an open-source automation tool that uses an agentless architecture to manage IT infrastructure efficiently.

### Control Node
The control node is the system where Ansible is installed. It executes playbooks and communicates with managed nodes using SSH or WinRM.

### Managed Nodes
Managed nodes are servers or virtual machines that Ansible controls. No agent installation is required on these nodes.

### Inventory
An inventory file lists managed nodes and groups them logically. It can be static or dynamically generated from cloud providers.

### Modules
Modules are reusable scripts that perform tasks such as installing packages, managing services, and configuring files.

## Role of Ansible in Cloud Automation

Ansible automates cloud infrastructure by provisioning resources, configuring servers, deploying applications, and maintaining consistency across AWS, Azure, and GCP environments.
