# Compute Services Across Cloud Providers

This document describes the core compute services offered by AWS, Microsoft Azure, and Google Cloud Platform (GCP). These services enable organizations to run applications, process workloads, and scale infrastructure efficiently in the cloud.

---

## 1. AWS EC2 (Elastic Compute Cloud)

### Overview

Amazon EC2 is a web service that provides resizable compute capacity in the AWS cloud. It allows users to launch and manage virtual servers known as *instances*.

### Features

* Wide range of instance types optimized for compute, memory, storage, and GPU workloads
* Support for multiple operating systems (Linux, Windows)
* Auto Scaling and Elastic Load Balancing integration
* Security using key pairs, security groups, and IAM roles
* Pay-as-you-go pricing with On-Demand, Reserved, and Spot instances

### Use Cases

* Hosting web and application servers
* Running CI/CD pipelines and DevOps tools
* Big data processing and batch workloads
* Application migration from on-premises to cloud

### Benefits

* High scalability and flexibility
* Cost-efficient pricing models
* Deep integration with other AWS services
* Reliable and highly available infrastructure

---

## 2. Azure Virtual Machines

### Overview

Azure Virtual Machines provide on-demand, scalable computing resources in Microsoft Azure, supporting both Windows and Linux operating systems.

### Capabilities

* Support for Windows and Linux-based VMs
* VM Scale Sets for automatic scaling
* Integration with Azure networking, storage, and security services
* Built-in monitoring and management via Azure Monitor
* Hybrid cloud support through Azure Arc

### Beneficial Scenarios

* Running enterprise and business-critical applications
* Migrating legacy workloads to the cloud
* Hosting development and testing environments
* Supporting hybrid cloud and on-premises integrations

### Benefits

* Strong integration with Microsoft ecosystem and tools
* Enterprise-grade security and compliance
* Flexible scaling options
* Simplified management through Azure Portal and CLI

---

## 3. Google Compute Engine (GCE)

### Overview

Google Compute Engine is GCP’s Infrastructure-as-a-Service (IaaS) offering that provides high-performance virtual machines running on Google’s global infrastructure.

### Functionality

* Custom machine types tailored to workload needs
* Preemptible VMs for cost-effective batch processing
* Live migration of VMs during maintenance
* Fast networking and global load balancing
* Integration with GCP monitoring and logging tools

### Advantages

* High performance and low latency networking
* Cost savings through sustained-use and committed-use discounts
* Flexible VM configurations
* Reliable infrastructure backed by Google’s global network

---

## Conclusion

AWS EC2, Azure Virtual Machines, and Google Compute Engine each provide robust and scalable compute solutions. While all three offer similar core capabilities, their strengths vary based on ecosystem integration, pricing models, and performance optimizations, allowing organizations to choose the best fit for their workloads and DevOps practices.