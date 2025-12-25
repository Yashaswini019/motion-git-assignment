Below is **ready-to-use content** you can directly save as **`cloud-service-models.md`**.
It’s written at the right depth for an assignment and aligns exactly with the requirement.

---

# Cloud Service Models

Cloud computing provides different service models that define how resources are delivered and managed. The three primary cloud service models are **Infrastructure as a Service (IaaS)**, **Platform as a Service (PaaS)**, and **Software as a Service (SaaS)**. Each model offers a different level of control, flexibility, and responsibility.

---

## Infrastructure as a Service (IaaS)

**Infrastructure as a Service (IaaS)** provides virtualized computing resources over the internet. In this model, cloud providers supply fundamental infrastructure components such as virtual machines, storage, and networking, while users manage the operating system, middleware, and applications.

### Characteristics

* On-demand virtual machines and storage
* High scalability and flexibility
* Users have full control over OS and applications
* Pay-as-you-go pricing model
* Ideal for custom environments and migrations

### Examples

* **AWS EC2** – Provides resizable compute capacity in the cloud
* **Azure Virtual Machines** – Offers scalable virtual machines for various workloads
* **Google Compute Engine** – Delivers high-performance virtual machines on GCP

### Common Use Cases

* Hosting custom applications
* Running legacy systems
* Disaster recovery and backup solutions

---

## Platform as a Service (PaaS)

**Platform as a Service (PaaS)** provides a complete development and deployment environment in the cloud. It allows developers to focus on building and deploying applications without worrying about infrastructure management.

### Purpose

* Simplifies application development
* Eliminates the need to manage servers, OS, or runtime environments
* Accelerates development and deployment cycles

### Characteristics

* Managed runtime environment
* Built-in scalability and load balancing
* Integrated development tools
* Supports CI/CD workflows

### Examples

* **AWS Elastic Beanstalk** – Automatically deploys and manages applications
* **Azure App Service** – Hosts web apps, APIs, and mobile backends
* **Google App Engine** – Fully managed platform for scalable applications

### Common Use Cases

* Web and mobile application development
* Microservices-based architectures
* Rapid prototyping and testing

---

## Software as a Service (SaaS)

**Software as a Service (SaaS)** delivers fully functional software applications over the internet. Users access applications through a web browser without managing infrastructure, platforms, or software updates.

### Characteristics

* No installation or maintenance required
* Accessible from any device with internet connectivity
* Subscription-based pricing
* Automatic updates and security patches

### Examples

* **Google Workspace** – Productivity tools like Gmail, Docs, and Drive
* **Salesforce** – Cloud-based customer relationship management (CRM)
* **Microsoft 365** – Office productivity and collaboration tools

### Common Use Cases

* Email and collaboration tools
* Customer relationship management
* Enterprise business applications

---

## Summary

| Service Model | Managed By User              | Managed By Provider         |
| ------------- | ---------------------------- | --------------------------- |
| IaaS          | OS, middleware, applications | Hardware, networking        |
| PaaS          | Applications, data           | Infrastructure, OS, runtime |
| SaaS          | Data and usage               | Everything else             |

Each cloud service model plays a vital role in modern cloud computing and DevOps practices, enabling organizations to choose the right balance of control, scalability, and operational responsibility.

Nice touch — **simple diagrams** will earn you clarity points without extra complexity.
Below are **clean, text-based diagrams** you can paste directly into `cloud-service-models.md`.

---

## Infrastructure as a Service (IaaS)

```
+----------------------------------+
|        User Responsibilities     |
|----------------------------------|
| Applications                     |
| Middleware                       |
| Runtime                          |
| Operating System                 |
+----------------------------------+
|     Cloud Provider Manages       |
|----------------------------------|
| Virtual Machines                 |
| Storage                          |
| Networking                       |
| Physical Hardware                |
+----------------------------------+
```

**Key Idea:**
👉 Maximum control for the user, more management responsibility.

---

## Platform as a Service (PaaS)

```
+----------------------------------+
|        User Responsibilities     |
|----------------------------------|
| Applications                     |
| Application Data                 |
+----------------------------------+
|     Cloud Provider Manages       |
|----------------------------------|
| Runtime                          |
| Middleware                       |
| Operating System                 |
| Servers & Networking             |
+----------------------------------+
```

**Key Idea:**
👉 Developers focus on code, not infrastructure.

---

## Software as a Service (SaaS)

```
+----------------------------------+
|        User Responsibilities     |
|----------------------------------|
| Application Usage                |
| Configuration                    |
+----------------------------------+
|     Cloud Provider Manages       |
|----------------------------------|
| Application                      |
| Runtime & Middleware             |
| Operating System                 |
| Infrastructure & Security        |
+----------------------------------+
```
**Key Idea:**
👉 Zero infrastructure management — just use the software.