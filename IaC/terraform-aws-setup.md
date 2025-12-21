Below is a **clear, step-by-step document** followed by a **basic Terraform configuration file (`main.tf`)** to create a simple EC2 instance on AWS.

---

# Setting Up a Basic EC2 Instance Using Terraform

### Step 1: Prerequisites

Ensure you have the following:

* An **AWS account**
* An **IAM user** with programmatic access
* Permissions: `AmazonEC2FullAccess` (for learning/demo)
* **AWS Access Key & Secret Key**
* **Terraform installed** on your machine

Verify Terraform installation:

```bash
terraform --version
```

---

### Step 2: Configure AWS Credentials

Configure credentials using AWS CLI:

```bash
aws configure
```

Enter:

* AWS Access Key
* AWS Secret Key
* Default region (e.g., `us-east-1`)
* Output format (optional)

Terraform will automatically use these credentials.

---

### Step 3: Create a Project Directory

```bash
mkdir terraform-ec2-demo
cd terraform-ec2-demo
```

---

### Step 4: Write Terraform Configuration

Create a file named **`main.tf`** and define:

* AWS provider
* EC2 instance resource
* AMI, instance type, and tags

---

### Step 5: Initialize Terraform

Downloads required provider plugins:

```bash
terraform init
```

---

### Step 6: Review the Execution Plan

Shows what Terraform will create:

```bash
terraform plan
```

---

### Step 7: Apply the Configuration

Creates the EC2 instance:

```bash
terraform apply
```

Type `yes` when prompted.

---

### Step 8: Verify EC2 Instance

* Go to **AWS Console → EC2**
* Confirm the instance is running

---

