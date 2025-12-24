# Kubernetes Cluster Setup on Cloud Platforms

This document outlines the steps required to set up a Kubernetes cluster on major cloud platforms using their managed Kubernetes services: **AWS EKS**, **Azure AKS**, and **GCP GKE**.

---

## AWS – Elastic Kubernetes Service (EKS)

Amazon EKS is a managed Kubernetes service that simplifies running Kubernetes on AWS.

### Steps to Set Up EKS:

1. Create an AWS account and configure IAM permissions.
2. Install AWS CLI, `eksctl`, and `kubectl`.
3. Create an EKS cluster using `eksctl` or the AWS Management Console.
4. Configure `kubectl` to connect to the EKS cluster.
5. Create and attach worker node groups.
6. Verify cluster access using `kubectl get nodes`.
7. Deploy applications using Kubernetes manifests.

### Benefits:

* Fully managed control plane
* High availability and scalability
* Native AWS IAM integration

---

## Azure – Azure Kubernetes Service (AKS)

AKS provides a managed Kubernetes environment integrated with Azure services.

### Steps to Set Up AKS:

1. Create an Azure account and resource group.
2. Install Azure CLI and `kubectl`.
3. Create an AKS cluster using the Azure Portal or Azure CLI.
4. Configure cluster credentials using `az aks get-credentials`.
5. Verify cluster connectivity with `kubectl get nodes`.
6. Deploy containerized applications.

### Benefits:

* Integrated with Azure Active Directory
* Automatic upgrades and scaling
* Simplified cluster management

---

## GCP – Google Kubernetes Engine (GKE)

GKE is Google’s managed Kubernetes service offering advanced automation and monitoring.

### Steps to Set Up GKE:

1. Create a GCP project and enable billing.
2. Enable the Kubernetes Engine API.
3. Install Google Cloud SDK and `kubectl`.
4. Create a GKE cluster via Google Cloud Console or CLI.
5. Authenticate using `gcloud` and configure `kubectl`.
6. Verify node status using `kubectl get nodes`.
7. Deploy applications to the cluster.

### Benefits:

* Automatic node repair and scaling
* Strong monitoring and logging
* Secure and reliable cluster management

---

## Summary

| Cloud Provider | Kubernetes Service | Key Advantage                   |
| -------------- | ------------------ | ------------------------------- |
| AWS            | EKS                | IAM integration and scalability |
| Azure          | AKS                | Azure AD integration            |
| GCP            | GKE                | Auto-scaling and monitoring     |

---

## Conclusion

Managed Kubernetes services on AWS, Azure, and GCP simplify cluster setup by handling the control plane and infrastructure management, allowing teams to focus on deploying and managing applications efficiently.