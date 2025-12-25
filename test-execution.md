# Test Execution in CI/CD Pipelines

Automated test execution is a core component of Continuous Integration and Continuous
Delivery (CI/CD) pipelines. Tests are automatically triggered whenever code changes
are pushed to the repository, ensuring fast feedback and high software quality.

This document explains:
- How tests are integrated at different pipeline stages
- How tools like Jenkins and GitHub Actions trigger tests automatically
- Examples of test execution in AWS, Azure, and GCP environments

---

## 1. Integration of Tests at Different Pipeline Stages

CI/CD pipelines are typically divided into multiple stages. Automated tests are
executed at different points to catch issues as early as possible.

### Build Stage
- Compiles or packages the application
- Executes **unit tests**
- Ensures individual components work correctly

**Example:**
```bash
mvn test
````

If unit tests fail, the pipeline stops immediately.

---

### Test Stage

* Runs **integration tests**
* Validates communication between components, APIs, and databases
* Ensures services work together correctly

**Example:**

```bash
mvn verify
```

This stage prevents broken integrations from reaching deployment.

---

### Deploy Stage

* Deploys the application to a staging or test environment
* Executes **acceptance or end-to-end tests**
* Confirms business workflows function correctly

**Example:**

```bash
npm run e2e
```

Only if all tests pass does the pipeline continue to production deployment.

---

## 2. Automated Test Execution Using CI/CD Tools

### Jenkins

Jenkins is a widely used CI/CD automation server that triggers tests automatically
when code changes are detected.

**How Jenkins Triggers Tests**

* A Git commit triggers the pipeline
* Jenkins executes defined stages in a Jenkinsfile
* Tests run automatically as part of the pipeline

**Example Jenkinsfile**

```groovy
pipeline {
    stages {
        stage('Build & Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
```

---

### GitHub Actions

GitHub Actions allows teams to define CI/CD workflows directly in the repository.

**How GitHub Actions Triggers Tests**

* Triggered by events such as push or pull request
* Executes test commands automatically in a workflow

**Example Workflow**

```yaml
name: CI Pipeline

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run Tests
        run: mvn test
```

---

## 3. Cloud-Specific CI/CD Test Execution Examples

### AWS – CodePipeline and CodeBuild

AWS CodePipeline orchestrates the pipeline, while CodeBuild runs automated tests.

**Example `buildspec.yml`**

```yaml
version: 0.2
phases:
  build:
    commands:
      - mvn test
```

* Unit and integration tests run during the build phase
* Pipeline fails if tests do not pass

---

### Azure – Azure Pipelines

Azure Pipelines supports automated test execution using YAML pipelines.

**Example Azure Pipeline**

```yaml
- task: Maven@3
  inputs:
    goals: 'test'
```

* Tests run automatically during pipeline execution
* Results are published in Azure DevOps

---

### GCP – Google Cloud Build

Google Cloud Build executes tests as part of the build steps.

**Example `cloudbuild.yaml`**

```yaml
steps:
- name: 'maven'
  args: ['test']
```

* Tests run automatically on every commit
* Supports unit, integration, and acceptance tests

---

## 4. Benefits of Automated Test Execution in CI/CD

* Early detection of defects
* Faster feedback for developers
* Consistent and repeatable testing
* Safe and reliable deployments

---

## Conclusion

Integrating automated tests at different stages of the CI/CD pipeline ensures high
software quality and reduces deployment risks. Tools like Jenkins and GitHub Actions
enable automatic test execution, while cloud platforms such as AWS, Azure, and GCP
provide scalable environments to run these tests efficiently.