
---

# Steps to Create a Basic CloudFormation Template for an EC2 Instance

## Step 1: Prerequisites

Ensure you have:

* An **AWS account**
* IAM permissions for **CloudFormation** and **EC2**
* Access to the **AWS Management Console**
* Basic understanding of **YAML or JSON**

---

## Step 2: Decide the EC2 Configuration

Before writing the template, identify:

* AWS Region (e.g., `us-east-1`)
* AMI ID (Amazon Linux 2 recommended)
* Instance type (e.g., `t2.micro`)
* Key pair (optional, for SSH access)
* Security group (optional, for network access)

---

## Step 3: Create the CloudFormation Template File

Create a file named **`ec2-template.yaml`** and define the template structure.

### Basic Template Structure

A CloudFormation template typically contains:

* `AWSTemplateFormatVersion`
* `Description`
* `Resources`

---

## Step 4: Define the EC2 Instance Resource

Use the `AWS::EC2::Instance` resource to define the EC2 instance.

### Example CloudFormation Template (YAML)

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: Basic CloudFormation template to create an EC2 instance

Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-0c02fb55956c7d316  # Amazon Linux 2 (us-east-1)
      Tags:
        - Key: Name
          Value: CloudFormation-EC2
```

---

## Step 5: Validate the Template

* Go to **AWS Console → CloudFormation**
* Choose **Create stack**
* Select **Upload a template file**
* Upload `ec2-template.yaml`
* CloudFormation automatically validates the template

---

## Step 6: Create the Stack

1. Click **Create stack**
2. Enter a **stack name** (e.g., `ec2-demo-stack`)
3. Review stack settings
4. Click **Submit**

---

## Step 7: Monitor Stack Creation

* Watch the **Events** tab for progress
* Status changes to **CREATE_COMPLETE** when successful

---

## Step 8: Verify the EC2 Instance

* Navigate to **EC2 → Instances**
* Confirm the instance is running
* Check the instance name and type

---


