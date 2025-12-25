# Cloud Command-Line Tools Overview

This document describes the command-line tools provided by AWS, Microsoft Azure, and Google Cloud Platform (GCP). These tools allow DevOps engineers and cloud administrators to manage cloud resources efficiently through automation and scripting.

---

## 1. AWS CLI (Command Line Interface)

### Overview
The AWS CLI is a unified command-line tool used to manage AWS services and resources directly from the terminal.

### Features
- Unified access to AWS services
- Support for automation and scripting
- Integration with IAM for secure authentication
- Works across Windows, macOS, and Linux

### Installation
- Install via package manager or installer
- Configure credentials using:
  ```bash
  aws configure

## Common Commands
- aws ec2 describe-instances
- aws s3 ls
- aws s3 cp file.txt s3://bucket-name/

## 2. Azure CLI
Overview

Azure CLI is a cross-platform command-line tool used to manage Azure resources and services.

# Capabilities

Create, update, and delete Azure resources

Manage virtual machines, storage, and networking

Support for scripting and automation

Integration with Azure Active Directory

Using Azure CLI

# Login to Azure:

az login


# List virtual machines:

az vm list

Common Management Tasks
az group list
az storage account list
az vm start --name <vm-name> --resource-group <resource-group>

## 3. Google Cloud SDK (gcloud)
# Overview

Google Cloud SDK is a set of tools that includes the gcloud CLI for managing resources in Google Cloud Platform.

# Functionality

- Manage GCP services and resources

- Configure authentication and projects

- Support for automation and scripting

- Integration with GCP IAM

# Key Commands
gcloud init
gcloud compute instances list
gcloud storage buckets list

## Advantages

Simple and consistent command structure

Strong integration with GCP services

Efficient resource management through automation

## Conclusion

AWS CLI, Azure CLI, and Google Cloud SDK are essential tools for managing cloud infrastructure in DevOps environments. They enable automation, scripting, and efficient control of cloud resources across AWS, Azure, and GCP platforms.