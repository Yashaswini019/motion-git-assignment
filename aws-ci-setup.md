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

For this assignment, the deployment stage is documented conceptually and does not require an actual deployment.

## Build Triggers (GitHub Webhook)
Build triggers define when Jenkins should start the CI pipeline. A common trigger is a GitHub webhook.

With a GitHub webhook:
- Every code push to the repository automatically notifies Jenkins
- Jenkins immediately starts the pipeline
- Developers receive fast feedback on build and test results

This automation ensures that every code change is continuously integrated and validated.


## Conclusion
Using Jenkins on AWS provides a scalable and reliable way to implement Continuous Integration. By automating build, test, and deployment stages, teams can improve code quality, reduce integration risks, and deliver software faster.
