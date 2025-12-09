Steps to 

1. **Create an AWS Account**
2. **Set up a basic EC2 instance**
3. **Deploy a sample Python script (e.g., adds two numbers)**

---

# **1. Create an AWS Account**

### **Step 1: Go to AWS Sign-Up Page**

* Visit: [https://aws.amazon.com](https://aws.amazon.com)
* Click **Create an AWS Account**.

### **Step 2: Enter Email & Password**

* Provide:

  * Email address
  * Password
  * AWS account name
* Continue to next step.

### **Step 3: Contact Information**

* Choose **Personal** or **Business** account.
* Enter full name, address, and phone number.

### **Step 4: Payment Method**

* Add a valid **credit/debit card** (required even for free tier).
* AWS will place a small temporary authorization hold.

### **Step 5: Identity Verification**

* Verify via **SMS** or **Voice call**.

### **Step 6: Select Support Plan**

* Choose **Basic (Free)**.

### **Step 7: Account Activation**

* AWS activates your account in a few minutes.
* You will receive a confirmation email.

---

# **2. Set Up a Basic EC2 Instance (Amazon Linux 2023)**

### **Step 1: Log in to AWS Console**

* Go to: [https://console.aws.amazon.com](https://console.aws.amazon.com)
* Sign in using your email and password.

### **Step 2: Open the EC2 Dashboard**

* In the search bar, type **EC2**.
* Click **EC2** → **Instances**.

### **Step 3: Launch a New Instance**

Click **Launch Instances**.

#### Configure:

Configure the Name of the instance, Select OS, Instance type, Key Pair for authentication, Network configuration, Storage. Once all the configuration is done, Click **Launch Instance**.

---

# **3. Connect to the EC2 Instance and Deploy python Script**


### **Step 1: SSH into EC2**

Use the **Public IPv4 address** from the EC2 dashboard:

```bash
ssh -i mykey.pem ec2-user@<EC2_PUBLIC_IP>
```

You are now logged into the EC2 VM.

---

### **Step 2: Install Python (Usually Preinstalled)**

Check Python:

```bash
python3 --version
```

If not installed:

```bash
sudo dnf install python3 -y
```

---

### **Step 3: Create and Run a Sample Python Script**

#### ** 1: Create the script**

```bash
vi add_numbers.py
```

Paste:

```python
a = 10
b = 20
print("Sum =", a + b)
```

### ** 2: Run the script**

```bash
python3 add_numbers.py
```

You should see:

```
Sum = 30
```
