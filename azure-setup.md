Steps to 

1. **Create an Azure Account**
2. **Set up a basic Amazon vm**
3. **Deploy a sample Python script (e.g., adds two numbers)**

# **1. Create an Azure Account**

### **Step 1: Go to Azure Sign-Up Page**

* Visit: [https://azure.microsoft.com](https://azure.microsoft.com)
* Click **Start free**.

### **Step 2: Sign in or Create a Microsoft Account**

* Use an existing Microsoft account or create a new one.

### **Step 3: Identity Verification**

* Enter contact info and verify phone number.

### **Step 4: Payment Method**

* Add a credit/debit card (required for free trial).

### **Step 5: Activate Free Trial**

* Click **Start** to activate your Azure subscription.

---

# **2. Create a Basic Azure VM**

### **Step 1: Open Azure Portal**

* Go to [https://portal.azure.com](https://portal.azure.com)

### **Step 2: Create a new Virtual Machine**

* In the search bar → type **Virtual Machines** → click **Create** → **Azure Virtual Machine**.

### **Step 3: Configuration (one-sentence version)**

Choose a name, select **Ubuntu 22.04 LTS**, choose a free-tier eligible size such as **Standard_B1s**, create/choose an SSH key pair, and allow SSH (port 22) in inbound rules.

---

# **3. Connect to the VM + Install Python + Run Sample Script (combined)**

### **Step 1: SSH into VM**

Use the VM's public IP:

```bash
ssh -i myazurekey.pem azureuser@<PUBLIC_IP>
```

### **Step 2: Install Python (if not installed)**

```bash
sudo apt update
sudo apt install python3 -y
```

### **Step 3: Create and run the sample Python script**

```bash
echo -e "a=10\nb=20\nprint('Sum =', a+b)" > add_numbers.py
python3 add_numbers.py
```

Output:

```
Sum = 30
```


