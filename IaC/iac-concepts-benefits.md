
---

# Infrastructure as Code (IaC)

## a. Concept of Infrastructure as Code (IaC)

Infrastructure as Code (IaC) is the practice of **defining and managing IT infrastructure using machine-readable configuration files**, rather than manually setting up servers, networks, and other resources through graphical interfaces or ad-hoc scripts.

With IaC, infrastructure such as **virtual machines, networks, storage, load balancers, and databases** is described using code and deployed automatically using tools like **Terraform, AWS CloudFormation, Azure ARM/Bicep, and Pulumi**.

IaC treats infrastructure the same way application code is treated—**written, tested, versioned, reviewed, and deployed automatically**.

### Key Characteristics

* Declarative or imperative configuration files
* Automated provisioning and teardown
* Repeatable and predictable deployments
* Integration with CI/CD pipelines

---

## b. Benefits and Examples of IaC

### 1. Improved Deployment Consistency

**Concept**
IaC ensures that infrastructure is created **the same way every time**, regardless of environment (development, testing, or production).

**Example**
Using Terraform, the same configuration file can be used to create:

* A development environment
* A staging environment
* A production environment

```hcl
resource "aws_instance" "app_server" {
  ami           = "ami-0abc123"
  instance_type = "t2.micro"
}
```

This guarantees that all environments have **identical infrastructure**, eliminating “it works on my machine” issues.

**Benefit**

* No configuration drift
* Predictable and repeatable deployments

---

### 2. Reduction of Manual Errors

**Concept**
Manual infrastructure setup is prone to human mistakes such as:

* Incorrect security group rules
* Wrong instance sizes
* Missed configuration steps

IaC automates these steps, minimizing human intervention.

**Example**
Instead of manually opening ports in a firewall, rules are defined once in code:

```hcl
resource "aws_security_group" "web_sg" {
  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```

**Benefit**

* Fewer misconfigurations
* Faster provisioning
* More secure and reliable infrastructure

---

### 3. Version Control for Infrastructure

**Concept**
IaC files can be stored in **version control systems like Git**, enabling tracking of changes over time.

**Example**

* A change to increase server size is committed as:

```diff
- instance_type = "t2.micro"
+ instance_type = "t3.small"
```

* Changes can be:

  * Reviewed via pull requests
  * Rolled back if issues occur
  * Audited for compliance

**Benefit**

* Full history of infrastructure changes
* Easy rollback to previous stable versions
* Improved collaboration among teams

---

