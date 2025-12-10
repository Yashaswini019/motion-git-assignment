Steps to 

1. **Create an GCP Account**
2. **Set up a basic Google Compute Engine VM**
3. **Deploy a sample Python script (e.g., adds two numbers)**

# **GCP: Create Account → Create VM → Deploy Python Script**

---

# **1. Create a Google Cloud Account**

### **Step 1: Go to Google Cloud**

* Visit [https://cloud.google.com](https://cloud.google.com)
* Click **Get started for free**.

### **Step 2: Sign In**

* Use your Google account.

### **Step 3: Provide Required Details**

* Enter basic information and accept terms.

### **Step 4: Payment Method**

* Add a valid credit/debit card (required for free trial credits).

### **Step 5: Activate Free Trial**

* Click **Start Free** to activate your GCP project with $300 free credits.

---

# **2. Create a Basic Google Compute Engine VM**

### **Step 1: Go to GCP Console**

* Visit [https://console.cloud.google.com](https://console.cloud.google.com)

### **Step 2: Enable Compute Engine**

* Search **Compute Engine** → Click **Enable API** if prompted.

### **Step 3: Create a VM Instance**

Choose a name, select **e2-micro (free-tier eligible)** with **Debian/Ubuntu Linux**, configure default network settings with **SSH allowed**, and create/choose an SSH key for login.

---

# **3. Connect to VM + Install Python + Run Script (combined)**

### **Step 1: Connect to the VM**

You have two options:

#### **Option A — Browser SSH (easiest)**

* Go to Compute Engine → VM instances
* Click **SSH** next to your VM
  (No key handling needed)

#### **Option B — Local SSH**

Download SSH key from GCP and run:

```bash
ssh -i <private-key> <username>@<EXTERNAL_IP>
```

---

### **Step 2: Install Python (if needed)**

```bash
sudo apt update
sudo apt install python3 -y
```

---

### **Step 3: Create and run the Python script**

```bash
echo -e "a=10\nb=20\nprint('Sum =', a+b)" > add_numbers.py
python3 add_numbers.py
```

Expected Output:

```bash
Sum =30
```