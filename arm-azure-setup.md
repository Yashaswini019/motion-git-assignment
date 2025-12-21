
---

# Steps to Create an ARM Template to Deploy an Azure Virtual Machine

## Step 1: Prerequisites

Ensure you have:

* An **Azure subscription**
* Permission to create resources (Contributor or higher)
* Access to the **Azure Portal**
* Basic knowledge of **JSON**

---

## Step 2: Understand ARM Template Components

An ARM template is a **JSON file** that declaratively defines Azure resources. The main sections include:

* `$schema` – Template schema reference
* `contentVersion` – Version of the template
* `parameters` – User-defined inputs
* `variables` – Reusable values
* `resources` – Azure resources to deploy
* `outputs` – Values returned after deployment

---

## Step 3: Plan the Virtual Machine Resources

To deploy a basic VM, you need:

* Resource group
* Virtual network and subnet
* Network interface (NIC)
* Public IP address
* Virtual machine
* OS image (e.g., Ubuntu or Windows)

---

## Step 4: Create the ARM Template File

Create a file named **`azure-vm-template.json`**.

---

## Step 5: Define Parameters

Parameters allow customization without modifying the template.

```json
"parameters": {
  "vmName": {
    "type": "string",
    "defaultValue": "myAzureVM"
  },
  "adminUsername": {
    "type": "string"
  },
  "adminPassword": {
    "type": "secureString"
  }
}
```

---

## Step 6: Define Networking Resources

Add definitions for:

* Virtual network
* Subnet
* Public IP
* Network interface

These resources must be created before the VM.

---

## Step 7: Define the Virtual Machine Resource

Use `Microsoft.Compute/virtualMachines` to deploy the VM and attach networking resources.

---

## Step 8: Validate the Template

* Go to **Azure Portal → Deploy a custom template**
* Select **Build your own template**
* Paste or upload the ARM template
* Click **Validate**

---

## Step 9: Deploy the Template

1. Choose or create a **resource group**
2. Provide parameter values
3. Click **Review + Create**
4. Click **Create**

---

## Step 10: Verify Deployment

* Navigate to **Virtual Machines** in the Azure Portal
* Confirm the VM is running
* Check networking and public IP

---

