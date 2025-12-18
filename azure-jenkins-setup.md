# Jenkins Server Setup on Azure and Basic Job Execution

## Objective

This document describes how to:

* Set up a Jenkins server on **Microsoft Azure**
* Create and run a basic Jenkins job
* Configure build steps to execute a sample file and display output

---

## A. Set Up Jenkins Server on Azure

### Step 1: Create a Virtual Machine

1. Log in to **Azure Portal**
2. Go to **Virtual Machines → Create**
3. Choose:

   * Image: **Ubuntu 22.04 LTS** (recommended)
   * Size: **Standard B1s / B2s**
4. Authentication: SSH key or password
5. Networking:

   * Allow inbound ports: **22 (SSH)** and **8080 (Jenkins)**
6. Click **Create**

---

### Step 2: Connect to the VM

```bash
ssh azureuser@<Azure-VM-Public-IP>
```

---

### Step 3: Install Java

```bash
sudo apt update -y
sudo apt install openjdk-17-jdk -y
java -version
```

---

### Step 4: Install Jenkins

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update -y
sudo apt install jenkins -y
```

---

### Step 5: Start Jenkins

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins
```

---

### Step 6: Access Jenkins UI

Open in browser:

```
http://<Azure-VM-Public-IP>:8080
```

Retrieve initial admin password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Complete setup:

* Install suggested plugins
* Create admin user

---

## B. Create Sample File

```bash
mkdir jenkins-demo
cd jenkins-demo
nano hello.py
```

```python
print("Hello from Jenkins on Azure")
print("Result:", 20 + 30)
```

---

## C. Create and Run a Basic Jenkins Job

1. Go to **Jenkins Dashboard**
2. Click **New Item**
3. Job name: `azure-python-job`
4. Select **Freestyle project** → OK
5. Click **Build Now** to verify job creation

---

## D. Configure Build Steps to Execute Sample File

1. Open job → **Configure**
2. Scroll to **Build Steps**
3. Click **Add build step → Execute shell**
4. Add command:

```bash
python3 /home/azureuser/jenkins-demo/hello.py
```

5. Save → **Build Now**

---

