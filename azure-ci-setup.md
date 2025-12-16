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
