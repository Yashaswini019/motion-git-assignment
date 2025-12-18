# Jenkins Server Setup on Google Cloud Platform (GCP)

This document provides step-by-step instructions to set up a Jenkins server on Google Cloud Platform using a Compute Engine VM.

---

## 1. Prerequisites

* A Google Cloud Platform (GCP) account
* A GCP project created
* Billing enabled for the project
* Basic knowledge of Linux and SSH

---

## 2. Create a Compute Engine VM

1. Go to **Google Cloud Console** → **Compute Engine** → **VM instances**.
2. Click **Create Instance**.
3. Configure the VM:

   * **Name**: jenkins-server
   * **Region/Zone**: Choose nearest region
   * **Machine type**: e2-medium (2 vCPU, 4 GB RAM) or higher
   * **Boot disk**: Ubuntu 20.04 LTS or 22.04 LTS
   * **Firewall**: Check **Allow HTTP traffic** and **Allow HTTPS traffic**
4. Click **Create**.

---

## 3. Configure Firewall Rule for Jenkins

Jenkins runs on port **8080** by default.

1. Go to **VPC Network** → **Firewall**.
2. Click **Create Firewall Rule**.
3. Set:

   * **Name**: allow-jenkins-8080
   * **Targets**: All instances in the network
   * **Source IP ranges**: 0.0.0.0/0 (or restrict to your IP)
   * **Protocols and ports**: TCP: 8080
4. Click **Create**.

---

## 4. Connect to the VM via SSH

From the VM instances page:

* Click **SSH** next to the `jenkins-server` VM

Or using terminal:

```bash
gcloud compute ssh jenkins-server --zone <your-zone>
```

---

## 5. Install Java (Required for Jenkins)

```bash
sudo apt update
sudo apt install -y openjdk-17-jdk
java -version
```

---

## 6. Install Jenkins

1. Add Jenkins repository and key:

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```

2. Install Jenkins:

```bash
sudo apt update
sudo apt install -y jenkins
```

3. Start and enable Jenkins:

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins
```

---

## 7. Access Jenkins Web Interface

Open a browser and navigate to:

```
http://<EXTERNAL_IP>:8080
```

You can find the external IP from the VM instance details page.

---

## 8. Unlock Jenkins

Retrieve the initial admin password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

* Paste the password into the Jenkins UI
* Click **Continue**

---

## 9. Install Recommended Plugins

* Choose **Install suggested plugins**
* Wait for plugin installation to complete

---

## 10. Create Admin User

* Enter admin username, password, and email
* Save and continue

---

## 12. Verify Jenkins Service

* Jenkins dashboard should load successfully
* Create a sample job to confirm functionality


---


