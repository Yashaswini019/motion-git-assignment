# Jenkins Server Setup on AWS and Basic Job Execution

## Objective

This document explains how to:

1. Set up a Jenkins server on AWS (EC2)
2. Create and run a basic Jenkins job
3. Configure build steps to execute a sample Python file and display output

---

## A. Setting Up Jenkins Server on AWS

### Step 1: Create an EC2 Instance

1. Log in to **AWS Management Console**
2. Go to **EC2 → Launch Instance**
3. Choose **Amazon Linux 2 AMI**
4. Instance type: **t2.micro** (Free Tier eligible)
5. Create or select a key pair
6. Configure Security Group:

   * Allow **SSH (22)** from your IP
   * Allow **HTTP (80)** from anywhere
   * Allow **Custom TCP (8080)** from anywhere (Jenkins)
7. Launch the instance

---

### Step 2: Connect to EC2 Instance

```bash
ssh -i your-key.pem ec2-user@<EC2-Public-IP>
```

---

### Step 3: Install Java (Required for Jenkins)

```bash
sudo yum update -y
sudo yum install java-17-amazon-corretto -y
```

Verify:

```bash
java -version
```

---

### Step 4: Install Jenkins

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum install jenkins -y
```

---

### Step 5: Start and Enable Jenkins

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

---

### Step 6: Access Jenkins Web UI

Open browser:

```
http://<EC2-Public-IP>:8080
```

Get initial admin password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Complete setup wizard:

* Install suggested plugins
* Create admin user

---

## B. Sample Python File

Create a simple Python script on the Jenkins server:

```bash
mkdir jenkins-demo
cd jenkins-demo
nano add.py
```

```python
print("Hello from Jenkins")
print("Sum of 5 and 10 is:", 5 + 10)
```

---

## C. Create and Run a Basic Jenkins Job

1. Open Jenkins Dashboard
2. Click **New Item**
3. Enter job name: `python-demo-job`
4. Select **Freestyle project** → OK

---

## D. Configure Build Steps to Execute Python File

1. Scroll to **Build Steps**
2. Click **Add build step → Execute shell**
3. Enter:

```bash
python3 /home/ec2-user/jenkins-demo/add.py
```

4. Click **Save**
5. Click **Build Now**

---


