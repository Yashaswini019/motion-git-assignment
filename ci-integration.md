# AWS CI
# AWS CI Pipeline Setup Using Jenkins

## Jenkins Overview
Jenkins is an open-source automation server used to implement Continuous Integration (CI) and Continuous Delivery (CD). It helps automate tasks such as building, testing, and deploying applications. Jenkins works by monitoring a source code repository (such as GitHub) and automatically running pipelines whenever changes are pushed to the repository.

Jenkins pipelines are defined as code using a Jenkinsfile, which makes the CI process repeatable, version-controlled, and easy to maintain.

## Jenkins on AWS (EC2)
On AWS, Jenkins is commonly hosted on an Amazon EC2 instance. An EC2 virtual machine provides the computing resources needed to run Jenkins and execute CI jobs.

Typical setup steps include:
- Launching an EC2 instance using Amazon Linux
- Installing Java (required by Jenkins)
- Installing and starting the Jenkins service
- Opening port 8080 in the EC2 security group to access Jenkins
- Accessing Jenkins through a web browser using the EC2 public IP address

This setup allows Jenkins to act as a centralized CI server for the application.

## CI Pipeline Stages

### Build Stage
The build stage is responsible for preparing the application for testing and deployment. In this stage, Jenkins:
- Checks out the latest code from the GitHub repository
- Installs required dependencies
- Compiles the application or validates source files (for example, a Python script)

If the build process fails, the pipeline stops and reports an error to the developer.

### Test Stage
The test stage runs automated tests to ensure the code works as expected. Jenkins executes unit tests or basic validation scripts during this stage.

Examples of test activities include:
- Running unit tests
- Checking code syntax and formatting
- Validating application logic

If any test fails, the pipeline is marked as failed, helping developers detect issues early.

### Deploy Stage
The deploy stage delivers the application to a target environment. In an AWS-based setup, this usually means deploying the application to an EC2 instance.

Typical deployment steps include:
- Copying application files to the EC2 server
- Restarting application services if required

## Build Triggers (GitHub Webhook)
Build triggers define when Jenkins should start the CI pipeline. A common trigger is a GitHub webhook.

With a GitHub webhook:
- Every code push to the repository automatically notifies Jenkins
- Jenkins immediately starts the pipeline
- Developers receive fast feedback on build and test results

This automation ensures that every code change is continuously integrated and validated

## Conclusion
Using Jenkins on AWS provides a scalable and reliable way to implement Continuous Integration. By automating build, test, and deployment stages, teams can improve code quality, reduce integration risks, and deliver software faster.

# Azure CI
# Azure CI Pipeline Setup Using Azure DevOps

## Overview
This document describes how to set up a basic Continuous Integration (CI) pipeline using Azure DevOps. Azure DevOps provides tools such as Azure Repos and Azure Pipelines to automate the build, test, and deployment process whenever code changes are pushed to the repository.

## Tools Used
- Azure Repos (Git repository)
- Azure Pipelines
- Azure Virtual Machine (VM)

## CI Pipeline Stages

### Build Stage
The build stage prepares the application for testing and deployment. In Azure DevOps, this stage is configured using a YAML pipeline or the visual pipeline editor.

Typical build steps include:
- Checking out the source code from Azure Repos or GitHub
- Restoring dependencies
- Compiling the application or validating source files

The build stage ensures that the application can be successfully built before moving to the next stage.

### Test Stage
The test stage runs automated tests to verify the correctness of the application. Azure Pipelines executes test scripts as part of this stage.

Common test activities include:
- Running unit tests
- Performing basic code validation
- Verifying application logic

If any test fails, the pipeline stops and reports the failure to the development team.

### Deploy Stage
The deploy stage releases the application to an Azure Virtual Machine (VM). In a typical setup, Azure Pipelines connects securely to the VM using SSH or service connections.

Deployment steps may include:
- Copying application files to the Azure VM
- Running startup or deployment scripts
- Restarting services if required

## Build Triggers
Build triggers define when the CI pipeline should run. In Azure DevOps, pipelines can be configured to automatically trigger on code changes.

Common triggers include:
- Automatic pipeline execution on every commit to the main branch
- Pull request validation builds

These triggers ensure continuous integration by validating every code change.

## Conclusion
Using Azure DevOps for Continuous Integration enables teams to automate builds, testing, and deployments. This improves code quality, enhances collaboration, and ensures faster feedback during development.


# GCP CI
# GCP CI Pipeline Setup Using CircleCI

## Overview
This document explains how to set up a basic Continuous Integration (CI) pipeline using CircleCI on Google Cloud Platform (GCP). CircleCI integrates with GitHub repositories to automatically build, test, and deploy applications whenever code changes are pushed.

## Tools Used
- CircleCI
- GitHub
- Google Compute Engine (GCE)

## CI Pipeline Stages

### Build Stage
The build stage in CircleCI prepares the application for testing and deployment. This stage is defined using a CircleCI configuration file (`.circleci/config.yml`).

Typical build steps include:
- Checking out the source code from GitHub
- Installing required dependencies
- Compiling the application or validating source files

The build stage ensures the application is in a runnable state before proceeding.

### Test Stage
The test stage runs automated tests to verify application correctness. CircleCI executes test commands as part of the pipeline workflow.

Common test activities include:
- Running unit tests
- Performing basic validation checks
- Verifying application logic

If tests fail, the pipeline stops and reports the failure immediately.

### Deploy Stage
The deploy stage releases the application to a Google Compute Engine (GCE) virtual machine.

Typical deployment steps include:
- Establishing a secure connection to the GCE instance
- Transferring application files
- Running deployment or startup scripts

## Build Triggers
CircleCI pipelines are automatically triggered by changes in the source code repository.

Common triggers include:
- Code commits pushed to the main branch
- Updates to pull requests

These triggers ensure that every change is automatically built and tested, enabling continuous integration.

## Conclusion
Using CircleCI with GCP provides an efficient and automated CI solution. By defining build, test, and deploy stages, teams can ensure code quality, reduce integration risks, and deliver applications faster.

