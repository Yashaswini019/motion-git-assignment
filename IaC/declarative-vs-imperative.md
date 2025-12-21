
---

# Declarative vs Imperative Approaches in Infrastructure as Code (IaC)

Infrastructure as Code (IaC) can be implemented using two main approaches: **declarative** and **imperative**. These approaches differ in how infrastructure is defined and how automation tools execute changes.

---

## a. Difference Between Declarative and Imperative IaC

### Declarative Approach

The **declarative approach** focuses on **what the desired end state of the infrastructure should be**, without specifying the exact steps required to achieve that state. The IaC tool determines how to create, update, or remove resources to match the declared configuration.

**Key Idea:**

> “This is how the infrastructure should look.”

Common declarative IaC tools include **Terraform, AWS CloudFormation, and Azure Resource Manager (ARM)**.

---

### Imperative Approach

The **imperative approach** defines **how to perform each step** to reach the desired infrastructure state. The user explicitly specifies the sequence of commands or actions that must be executed.

**Key Idea:**

> “These are the steps to build the infrastructure.”

Imperative approaches are commonly used in **scripts, CLI commands, and configuration management tools**.

---

## b. Examples, Pros, and Cons

### Declarative IaC

#### Example

Terraform configuration defining an EC2 instance:

```hcl
resource "aws_instance" "web" {
  ami           = "ami-0abc123"
  instance_type = "t2.micro"
}
```

The tool:

* Compares current infrastructure with the desired state
* Automatically determines what actions are required
* Applies changes to reach the defined state

#### Pros

* Easier to understand and maintain
* Idempotent (running multiple times gives the same result)
* Reduces configuration drift
* Supports automatic dependency management
* Ideal for large-scale and complex environments

#### Cons

* Less control over execution order
* Debugging can be harder
* Requires understanding of the tool’s internal logic
* State management may add complexity

---

### Imperative IaC

#### Example

Shell script to create infrastructure resources:

```bash
aws ec2 run-instances --image-id ami-0abc123 --instance-type t2.micro
aws ec2 create-tags --resources i-123456 --tags Key=Name,Value=WebServer
```

Each step must be explicitly defined and executed in order.

#### Pros

* Full control over execution flow
* Easier for simple or one-time tasks
* Straightforward and flexible
* No state files required

#### Cons

* Error-prone and harder to maintain
* Not idempotent by default
* Difficult to scale for large infrastructures
* No built-in rollback or dependency tracking

---

---


