Here is a **step-by-step guide** to create a **simple Ansible playbook** that provisions a **Google Compute Engine (GCE) instance**.

---

# Steps to Create an Ansible Playbook for GCE

## Step 1: Prerequisites

Ensure you have the following:

* **Ansible installed** (version 2.9 or later recommended)
* A **Google Cloud Platform (GCP) account**
* **Service account key** with **Compute Admin** role (JSON format)
* **Python Google Cloud SDK libraries** (`google-auth`, `google-api-python-client`) installed
* `gce` module available via `ansible-galaxy` if needed

---

## Step 2: Install Required Python Packages

```bash
pip install google-auth google-auth-oauthlib google-api-python-client
```

---

## Step 3: Set Up GCP Credentials

1. Create a **service account** in GCP Console
2. Assign **Compute Admin** role
3. Download the **JSON key file**
4. Export the environment variable to let Ansible use it:

```bash
export GCP_SERVICE_ACCOUNT_FILE="/path/to/your-service-account.json"
export GCP_PROJECT="your-gcp-project-id"
export GCP_ZONE="us-central1-a"
```

---

## Step 4: Create the Ansible Playbook

1. Create a directory for your playbook:

```bash
mkdir gce-ansible
cd gce-ansible
```

2. Create a file named **`create_gce_instance.yml`**

---

### Example Ansible Playbook (`create_gce_instance.yml`)

```yaml
---
- name: Provision a Google Compute Engine instance
  hosts: localhost
  connection: local
  gather_facts: no
  vars:
    instance_name: ansible-gce-demo
    machine_type: n1-standard-1
    image_family: debian-11
    image_project: debian-cloud
    network: default
    zone: "{{ lookup('env', 'GCP_ZONE') }}"
    project: "{{ lookup('env', 'GCP_PROJECT') }}"
    service_account_file: "{{ lookup('env', 'GCP_SERVICE_ACCOUNT_FILE') }}"

  tasks:
    - name: Create GCE instance
      google.cloud.gcp_compute_instance:
        name: "{{ instance_name }}"
        machine_type: "{{ machine_type }}"
        disks:
          - auto_delete: true
            boot: true
            initialize_params:
              source_image: "projects/{{ image_project }}/global/images/family/{{ image_family }}"
        network_interfaces:
          - network: "{{ network }}"
            access_configs:
              - name: External NAT
                type: ONE_TO_ONE_NAT
        project: "{{ project }}"
        zone: "{{ zone }}"
        service_account_file: "{{ service_account_file }}"
      register: gce_instance

    - name: Display the instance info
      debug:
        var: gce_instance
```

---

## Step 5: Run the Playbook

```bash
ansible-playbook create_gce_instance.yml
```

---

## Step 6: Verify the Instance

* Go to **GCP Console → Compute Engine → VM Instances**
* You should see a running VM with the name `ansible-gce-demo`

---

